# Semana 6 — Herramientas y requisitos de calidad de software

**Curso:** Estándares y Métricas de Calidad en el Desarrollo de Software
Los temas marcados como *propuesta* son sugerencias del docente y pueden ajustarse.

## Introducción

Las semanas anteriores definieron qué es calidad, cómo se comprueba, cómo se caracterizan los defectos y cómo se especifican los requisitos. Esta semana une esas piezas: a partir de los **defectos** de un sistema se formulan **requisitos de calidad medibles** y se eligen las **herramientas** que ayudan a prevenirlos, detectarlos y gestionarlos. Los requisitos de calidad se expresan con las características de ISO/IEC 25010 y se verifican con herramientas de análisis estático, pruebas funcionales, rendimiento y gestión de defectos.

## 🎯 Resultados de aprendizaje

- Identifica los requisitos de calidad del software.
- Establece las herramientas de calidad de software.

## 🧭 Idea central de la semana

Ninguna herramienta reemplaza a las demás ni a unos criterios de aceptación bien definidos. ISO/IEC 25010 dice **qué** es calidad en el producto; CMMI dice **cómo** madura el proceso; las herramientas actúan en capas distintas. Un requisito vago ("el sistema debe ser rápido") no se puede verificar; uno medible ("la consulta de estado responde en menos de 2 s con 200 usuarios concurrentes") sí.

## 🗂️ Orientación para la clase

| # | Bloque | Qué orientar en clase |
|:-:|:--|:--|
| 1 | Enlace con las semanas 3 y 4 | Los defectos clasificados en la Semana 3 y los requisitos de la Semana 4 son la materia prima de esta semana. |
| 2 | Análisis estático de código | **SonarQube**: analiza el código sin ejecutarlo; duplicación, deuda técnica, vulnerabilidades y reglas de codificación. Se usa en cada *pull request* y en el pipeline de CI. |
| 3 | Pruebas funcionales y de regresión | **Selenium**: automatiza el navegador; protege el comportamiento ya validado. No es una herramienta de pruebas unitarias. |
| 4 | Rendimiento y gestión de defectos | **Apache JMeter** simula carga concurrente. Herramientas de seguimiento de defectos (por ejemplo, JIRA) para el ciclo de vida del defecto. |
| 5 | Requisitos de calidad: ISO/IEC 25010 | Sucesora de ISO/IEC 9126. Ocho características que deben traducirse en métricas medibles. Aclarar que las características son las mismas de la Semana 1. |
| 6 | Cómo redactar requisitos de calidad medibles | De vago a medible: atributo + métrica + umbral + condición de medición. Cada requisito lleva criterio de aceptación o forma de verificación. |
| 7 | Caso BancoRegional SA | Plataforma de créditos con 3.200 usuarios mensuales. SonarQube mostró 340 h de deuda técnica, complejidad ciclomática promedio de 28 (umbral 10) y 23 bloques duplicados. Un índice en la tabla de movimientos bajó la respuesta con 200 usuarios de 8,9 s a 1,4 s (confirmado con JMeter). |
| 8 | Pruebas de aceptación | Verifican que el sistema cumple lo acordado con el cliente antes de liberarlo. Criterios en formato Dado-Cuando-Entonces (Gherkin). |
| 9 | Karate DSL | Pruebas de API REST en sintaxis Gherkin sobre Cucumber/JVM; se ejecutan con Maven e integran en CI. |

## ⚠️ Puntos a aclarar en clase

- **ISO/IEC 9126 y 25010.** El recurso básico de la actividad (Ávila, 2013) usa ISO/IEC 9126-1. La presentación usa su sucesora, ISO/IEC 25010; aclarar la correspondencia de nombres de las características.
- **Densidad de defectos y complejidad.** Los umbrales de los casos (por ejemplo, complejidad ciclomática ≤ 10) son referencias del docente; el equipo debe calibrarlos para su contexto.

## 💬 Preguntas para detonar la discusión

1. Tomen un defecto de la Semana 3 y conviértanlo en un requisito de calidad medible.
2. ¿Qué herramienta habrían puesto primero en BancoRegional SA y por qué?
3. ¿Qué diferencia hay entre una prueba de regresión y una de aceptación?
4. ¿Por qué no basta con subir la cobertura de pruebas para cumplir un requisito de fiabilidad?

## 📝 Actividad evaluable de la semana

**Taller. Identificación de requisitos de calidad y herramientas de aseguramiento del software** (código EDSTV011_A6, [EDSTV011_A6_V2.pdf](Semana_6_Actividad/EDSTV011_A6_V2.pdf)). Actividad **individual**: 6 horas de desarrollo y 5 horas de consulta de materiales. Documento de 5 a 7 páginas.

**Qué debe contener**

1. **Identificación de defectos:** un sistema real o hipotético y al menos 5 defectos con su contexto.
2. **Clasificación según atributos de calidad:** funcionalidad, confiabilidad, usabilidad, eficiencia, seguridad, mantenibilidad; explicar por qué cada defecto afecta ese atributo.
3. **Requisitos de calidad:** al menos 5, con descripción, atributo asociado y criterio de aceptación o forma de verificación.
4. **Herramientas de aseguramiento:** al menos 3 (seguimiento de defectos, análisis estático, pruebas automatizadas o integración continua) y cómo contribuyen.
5. **Análisis y reflexión** sobre la relación defectos → requisitos → herramientas.
6. **Estructura:** portada, introducción, desarrollo, conclusiones y referencias APA.

**Recursos básicos:** Ávila (2013), Díaz, Casañola e Hidalgo (2019) y Paredes et al. (2017). **Complementario:** Vidal et al. (2020), habilidades blandas.

### Rúbrica del taller (total: 5.0 puntos, según el PDF de la actividad)

| Criterio | Puntaje máximo |
|:--|:-:|
| Identificación y análisis de defectos de software | 0.5 |
| Formulación de requisitos de calidad | 1.5 |
| Identificación de herramientas de aseguramiento de la calidad | 1.5 |
| Análisis y organización del documento | 1.5 |

> **Inconsistencias en el material de la actividad (por revisar con el docente):**
> - El enunciado es un taller, pero el apartado "Rol del profesor" habla de guiar una **entrevista** (perfil del entrevistado, preguntas técnicas) y el ejemplo de nombre de archivo es `romero_luis_entrevista`.
> - Se eliminó `S6_Rubrica` (`.md` y `.docx`), una rúbrica genérica de **ensayo** que no correspondía al taller. La rúbrica vigente es la del PDF.

## ✍️ Actividad sugerida en clase (propuesta)

Con un sistema conocido por el grupo: listar **tres defectos**, redactar **un requisito de calidad medible** para cada uno (atributo, métrica, umbral y forma de verificación) y asignar **una herramienta** a cada requisito explicando por qué.

## 🔑 Glosario rápido

- **Requisito de calidad:** requisito no funcional medible vinculado a una característica de ISO/IEC 25010.
- **Análisis estático:** revisión del código sin ejecutarlo (SonarQube).
- **Deuda técnica:** costo estimado de corregir los problemas de mantenibilidad del código.
- **Complejidad ciclomática:** número de caminos independientes en el código; indicador de dificultad de prueba y mantenimiento.
- **Prueba de regresión:** comprueba que un cambio no rompe lo que ya funcionaba.
- **Prueba de aceptación:** comprueba que el sistema cumple los criterios acordados con el cliente.
- **Gherkin / Dado-Cuando-Entonces:** lenguaje para escribir criterios de aceptación.
- **Karate DSL:** framework de pruebas de API en sintaxis Gherkin.

## ➡️ Puente hacia la Semana 7

La Semana 7 distingue **técnica, herramienta y estándar**, clasifica las técnicas de gestión de la calidad con ISO/IEC 25010 y CMMI nivel 3, y mide la calidad con métricas y deuda técnica.
