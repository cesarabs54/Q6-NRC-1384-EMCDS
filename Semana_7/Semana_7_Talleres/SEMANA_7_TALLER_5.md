# Guía paso a paso: Escalar el proyecto a Cucumber y API REST (Spring Boot)

Proyecto base: `user-quality-demo` (gestión de usuarios + pruebas unitarias, integración y aceptación).

---

## Índice

1. Extender a API REST con Spring Boot  
   1.1. Actualizar `pom.xml`  
   1.2. Crear clase principal `UserQualityDemoApplication`  
   1.3. Ajustar `User`, crear configuración, controlador REST y manejo de errores  
   1.4. Probar la API (manual y con tests)  

2. Añadir Cucumber para pruebas de aceptación BDD  
   2.1. Actualizar `pom.xml` con dependencias de Cucumber  
   2.2. Crear archivo `.feature` con escenarios Given–When–Then  
   2.3. Crear clase runner de Cucumber  
   2.4. Crear step definitions conectadas al `UserService`  
   2.5. Ejecutar las pruebas de Cucumber  

---

## 1. Extender a API REST con Spring Boot

### 1.1. Actualizar `pom.xml`

Sustituye el contenido actual por una versión con Spring Boot (o ajusta lo necesario):

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>user-quality-demo</artifactId>
    <version>1.1.0</version>
    <packaging>jar</packaging>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.2.5</version>
    </parent>

    <properties>
        <java.version>17</java.version>
    </properties>

    <dependencies>
        <!-- Web / REST -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <!-- JUnit 5 ya viene integrado con Spring Boot -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>

        <!-- Mockito explícito (opcional, ya incluido en starter-test) -->
        <dependency>
            <groupId>org.mockito</groupId>
            <artifactId>mockito-core</artifactId>
            <version>5.11.0</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
</project>
```

---

### 1.2. Clase principal `UserQualityDemoApplication`

Crea:

```java
// src/main/java/com/example/usermanagement/UserQualityDemoApplication.java
package com.example.usermanagement;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

/**
 * Punto de entrada de la aplicación Spring Boot.
 */
@SpringBootApplication
public class UserQualityDemoApplication {

    public static void main(String[] args) {
        SpringApplication.run(UserQualityDemoApplication.class, args);
    }
}
```

---

### 1.3. Ajustes a `User`, configuración, controlador REST y manejo de errores

**a) Constructor vacío en `User`.** Jackson necesita un constructor sin argumentos para convertir el JSON del
`@RequestBody` en un objeto. Agrega a la clase `User` del Taller 4:

```java
public User() { }
```

**b) Configuración de beans.** `UserService` es una clase Java simple (sin `@Service`), así que la registramos como bean
para poder inyectarla en el controlador:

```java
// src/main/java/com/example/usermanagement/config/AppConfig.java
package com.example.usermanagement.config;

import com.example.usermanagement.repository.InMemoryUserRepository;
import com.example.usermanagement.repository.UserRepository;
import com.example.usermanagement.service.UserService;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class AppConfig {

    @Bean
    public UserRepository userRepository() {
        return new InMemoryUserRepository();
    }

    @Bean
    public UserService userService(UserRepository userRepository) {
        return new UserService(userRepository);
    }
}
```

**c) Controlador REST `UserController`.**

```java
// src/main/java/com/example/usermanagement/api/UserController.java
package com.example.usermanagement.api;

import com.example.usermanagement.model.User;
import com.example.usermanagement.service.UserService;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

import java.util.List;

/**
 * Controlador REST para gestionar usuarios.
 * Este es el "punto de contacto" con el mundo exterior.
 */
@RestController
@RequestMapping("/api/users")
public class UserController {

    private final UserService userService;

    // El servicio se inyecta (ver AppConfig): el controlador no crea sus dependencias.
    public UserController(UserService userService) {
        this.userService = userService;
    }

    @PostMapping
    public ResponseEntity<User> create(@RequestBody User user) {
        User created = userService.createUser(user.getName(), user.getEmail());
        return ResponseEntity.ok(created);
    }

    @GetMapping
    public ResponseEntity<List<User>> getAll() {
        return ResponseEntity.ok(userService.getAllUsers());
    }

    @PutMapping("/{id}")
    public ResponseEntity<User> update(@PathVariable Long id,
                                       @RequestBody User user) {
        User updated = userService.updateUser(id, user.getName(), user.getEmail());
        return ResponseEntity.ok(updated);
    }

    @DeleteMapping("/{id}")
    public ResponseEntity<Void> delete(@PathVariable Long id) {
        userService.deleteUser(id);
        return ResponseEntity.noContent().build();
    }
}
```

**d) Manejo de errores.** Sin esto, las `IllegalArgumentException` del servicio se convierten en `500 Internal Server Error`.
Las reglas de negocio incumplidas son un error del cliente, por lo que se responde `400 Bad Request`:

```java
// src/main/java/com/example/usermanagement/api/ApiExceptionHandler.java
package com.example.usermanagement.api;

import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.ExceptionHandler;
import org.springframework.web.bind.annotation.RestControllerAdvice;

import java.util.Map;

@RestControllerAdvice
public class ApiExceptionHandler {

    @ExceptionHandler(IllegalArgumentException.class)
    public ResponseEntity<Map<String, String>> handleBadRequest(IllegalArgumentException ex) {
        return ResponseEntity.status(HttpStatus.BAD_REQUEST)
                .body(Map.of("error", ex.getMessage()));
    }
}
```

> Para producción, lo ideal sería usar un repositorio real (JPA, etc.) y códigos más específicos (`404`, `409`). Aquí mantenemos la simplicidad didáctica.

---

### 1.4. Probar la API REST

1. Ejecutar la aplicación:

```bash
mvn spring-boot:run
```

2. Probar con `curl` o Postman:

- Crear usuario:

```bash
curl -X POST http://localhost:8080/api/users \
     -H "Content-Type: application/json" \
     -d '{"name":"Cesar","email":"cesar@example.com"}'
```

- Listar usuarios:

```bash
curl http://localhost:8080/api/users
```

- Actualizar usuario:

```bash
curl -X PUT http://localhost:8080/api/users/1 \
     -H "Content-Type: application/json" \
     -d '{"name":"Cesar Actualizado","email":"cesar@example.com"}'
```

- Eliminar usuario:

```bash
curl -X DELETE http://localhost:8080/api/users/1
```

Intenta crear dos veces el mismo email: la segunda llamada debe responder `400` con `{"error":"El email ya está registrado"}`.

En clase puedes conectar esto con las pruebas de integración: ahora el servicio se expone como API y se puede probar con `MockMvc` o con un cliente HTTP (actividad 4).

---

## 2. Añadir Cucumber para pruebas de aceptación BDD

Ahora vamos a reemplazar/acompañar las pruebas de aceptación JUnit por **escenarios Cucumber**.

### 2.1. Actualizar `pom.xml` con dependencias de Cucumber

Añade estas dependencias dentro de `<dependencies>`:

```xml
<!-- Cucumber JUnit Platform -->
<dependency>
    <groupId>io.cucumber</groupId>
    <artifactId>cucumber-java</artifactId>
    <version>7.15.0</version>
    <scope>test</scope>
</dependency>

<dependency>
    <groupId>io.cucumber</groupId>
    <artifactId>cucumber-junit-platform-engine</artifactId>
    <version>7.15.0</version>
    <scope>test</scope>
</dependency>

<!-- Permite declarar la suite con @Suite (versión gestionada por Spring Boot) -->
<dependency>
    <groupId>org.junit.platform</groupId>
    <artifactId>junit-platform-suite</artifactId>
    <scope>test</scope>
</dependency>
```

---

### 2.2. Crear archivo `.feature` con escenarios Given–When–Then

Crea el directorio de recursos de test:

```text
src/test/resources/features/user_management.feature
```

Contenido:

```gherkin
Feature: Gestión de usuarios

  Como administrador
  Quiero evitar emails duplicados
  Para garantizar la unicidad de los usuarios

  Scenario: Rechazar creación de usuario con email ya existente
    Given existe un usuario con email "existing@example.com"
    When intento crear un usuario con nombre "Nuevo" y email "existing@example.com"
    Then el sistema debe rechazar la creación con el mensaje "El email ya está registrado"

  Scenario: Rechazar creación de usuario sin nombre
    Given no existe usuario con email "noname@example.com"
    When intento crear un usuario con nombre "" y email "noname@example.com"
    Then el sistema debe rechazar la creación con el mensaje "El nombre es obligatorio"
```

---

### 2.3. Crear clase runner de Cucumber

```java
// src/test/java/com/example/usermanagement/cucumber/CucumberTest.java
package com.example.usermanagement.cucumber;

import org.junit.platform.suite.api.ConfigurationParameter;
import org.junit.platform.suite.api.IncludeEngines;
import org.junit.platform.suite.api.SelectClasspathResource;
import org.junit.platform.suite.api.Suite;

import static io.cucumber.junit.platform.engine.Constants.GLUE_PROPERTY_NAME;

/**
 * Runner de Cucumber usando JUnit Platform Suite.
 * Al ejecutar mvn test, Cucumber buscará los .feature en src/test/resources/features
 * y los steps en el paquete indicado en el glue.
 */
@Suite
@IncludeEngines("cucumber")
@SelectClasspathResource("features")
@ConfigurationParameter(key = GLUE_PROPERTY_NAME, value = "com.example.usermanagement.cucumber")
public class CucumberTest {
    // No necesita código adicional.
}
```

---

### 2.4. Crear step definitions conectadas al `UserService`

```java
// src/test/java/com/example/usermanagement/cucumber/UserSteps.java
package com.example.usermanagement.cucumber;

import com.example.usermanagement.repository.InMemoryUserRepository;
import com.example.usermanagement.repository.UserRepository;
import com.example.usermanagement.service.UserService;
import io.cucumber.java.Before;
import io.cucumber.java.en.*;

import static org.junit.jupiter.api.Assertions.*;

public class UserSteps {

    private UserRepository repo;
    private UserService service;
    private Exception capturedException;

    @Before
    public void setup() {
        repo = new InMemoryUserRepository();
        service = new UserService(repo);
        capturedException = null;
    }

    @Given("existe un usuario con email {string}")
    public void existe_un_usuario_con_email(String email) {
        service.createUser("Existente", email);
    }

    @Given("no existe usuario con email {string}")
    public void no_existe_usuario_con_email(String email) {
        // No hacemos nada: el repositorio está vacío
    }

    @When("intento crear un usuario con nombre {string} y email {string}")
    public void intento_crear_un_usuario_con_nombre_y_email(String name, String email) {
        try {
            service.createUser(name, email);
        } catch (Exception e) {
            capturedException = e;
        }
    }

    @Then("el sistema debe rechazar la creación con el mensaje {string}")
    public void el_sistema_debe_rechazar_la_creacion_con_el_mensaje(String expectedMessage) {
        assertNotNull(capturedException, "Se esperaba una excepción");
        assertEquals(expectedMessage, capturedException.getMessage());
    }
}
```

> Aquí se ve claramente el puente entre **escenarios de negocio** y **lógica de servicio**. Es un excelente punto para discutir trazabilidad entre requisitos y pruebas.
>
> **Alcance:** estos steps llaman directamente a `UserService`; no pasan por HTTP. Validan la regla de negocio, no la API.
> Para una aceptación sobre la API real, los steps deberían usar `MockMvc` (ver Taller 2) o un cliente HTTP.

---

### 2.5. Ejecutar las pruebas de Cucumber

Simplemente:

```bash
mvn test
```

- JUnit ejecutará `CucumberTest`.
- Cucumber leerá `user_management.feature`.
- Los steps en `UserSteps` se ejecutarán contra el `UserService` real.

En clase puedes mostrar:

- El `.feature` como especificación legible por negocio.
- Los steps como “implementación técnica” de esa especificación.
- Cómo los mensajes de error del servicio se convierten en criterios de aceptación.

---

## Conclusiones

- **Spring Boot** lleva el mismo servicio a un contexto más cercano a producción: API REST, endpoints, HTTP.
- **Cucumber** convierte las pruebas de aceptación en artefactos BDD, alineados con historias de usuario.

Con este archivo `.md` puedes:

- Entregarlo como guía de laboratorio.
- Usarlo como base para una práctica donde los estudiantes:
    - Extienden nuevos endpoints.
    - Añaden nuevos escenarios Cucumber para otras reglas de negocio.

---

## Actividades y entregable

1. Aplicar la guía sobre el proyecto `user-quality-demo` del Taller 4 y verificar que `mvn test` pasa.
2. Probar la API con `curl` o Postman: crear un usuario, intentar crearlo de nuevo y comprobar que responde `400` con el mensaje de error.
3. Agregar un escenario Cucumber para «actualizar un usuario con el email de otro usuario».
4. Agregar una prueba con `MockMvc` (`@SpringBootTest` + `@AutoConfigureMockMvc`) que valide el código HTTP del `POST /api/users`.
5. Responder: ¿qué diferencia hay entre los steps actuales (que llaman a `UserService`) y una prueba de aceptación sobre la API?

**Entregable:** proyecto con el escenario y la prueba nuevos, captura de `mvn test` en verde y la respuesta a la pregunta 5.