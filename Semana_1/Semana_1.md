# Semana 1 — Fundamentos de la calidad de software

**Curso:** Estándares y Métricas de Calidad en el Desarrollo de Software

## Introducción

Le damos la más cordial bienvenida a la semana 1 del curso Estándares y Métricas de Calidad en el Desarrollo de Software. Durante esta semana se revisarán los fundamentos de la calidad de software, abarcando temas como el valor y los costos asociados a la realización de software de calidad. Además, se comenzará con el estudio de los modelos y las características que deben contemplarse en el desarrollo de software y de las posibilidades de mejora para asegurar la calidad, teniendo en cuenta la cultura y la ética durante la ejecución de las diferentes etapas de construcción del software e involucrando las diferentes metodologías existentes para el desarrollo de los diferentes procesos. Se busca siempre asegurar la construcción de software eficiente y confiable, lo que conlleva la producción de software de calidad.

## 🎯 Resultados de aprendizaje

- Conoce la cultura y ética de la ingeniería de software.
- Comprende conceptos básicos sobre estándares y métricas.
- Asegura la calidad a través de la definición de los modelos y características de calidad.

## 🧭 Idea central de la semana

La calidad del software no es solo "que no tenga errores". Es un concepto multidimensional que **tiene un valor y un costo**, se construye desde el inicio del proyecto, se define con **modelos y estándares**, se evalúa con **métricas** y se mejora con procesos sistemáticos, siempre dentro de una **cultura y ética profesional**. El propósito es construir software **eficiente y confiable**.

## 🗺️ Ruta de la semana

La introducción plantea cinco ejes. La clase puede seguir este orden:

| Eje | Tema de la introducción |
|:-:|:--|
| 1 | Valor y costos de la calidad |
| 2 | Modelos y características de calidad (software eficiente y confiable) |
| 3 | Estándares y métricas (resultado de aprendizaje de la semana) |
| 4 | Posibilidades de mejora y metodologías |
| 5 | Cultura y ética en las etapas de construcción |

## 🗂️ Orientación para la clase

### Apertura

| Tema | Qué orientar en clase |
|:--|:--|
| Bienvenida y enfoque del curso | Recorrido por la plataforma (recursos, actividades, foros) y calidad como eje transversal del ciclo de vida, no solo pruebas. |

### Eje 1 — Valor y costos de la calidad

| Tema | Qué orientar en clase |
|:--|:--|
| ¿Qué es calidad de software? | "Funciona" no equivale a "tiene calidad". Calidad como valor para el usuario, costo para la organización y disciplina profesional. La calidad se planifica desde el inicio. |
| Valor y costos | Los cuatro tipos de costos: prevención, evaluación, fallos internos y fallos externos. Por qué corregir tarde es más caro. La calidad exigida depende del contexto y la criticidad (videojuego casual vs. control aéreo). |

### Eje 2 — Modelos y características de calidad

| Tema | Qué orientar en clase |
|:--|:--|
| Modelos y características | ISO/IEC 25010 y sus ocho características: adecuación funcional, eficiencia del desempeño, compatibilidad, usabilidad, fiabilidad, seguridad, mantenibilidad y portabilidad. Enfatizar **eficiencia del desempeño** y **fiabilidad**, que responden al "software eficiente y confiable" de la introducción. |
| Priorizar según el proyecto | Tres casos: historia clínica, app de pedidos de comida e inventario interno. Relación con la gestión de riesgos. |

### Eje 3 — Estándares y métricas

| Tema | Qué orientar en clase |
|:--|:--|
| Métricas | Definición de métrica. Métricas de producto, de proceso y de proyecto. Interpretarlas en contexto (50 defectos no significa "malo"; cero defectos reportados puede significar que no se evaluó). |
| Estándares | Qué es un estándar y por qué da consistencia. Ejemplo de estándar de codificación y su efecto en la mantenibilidad. |

### Eje 4 — Posibilidades de mejora y metodologías

| Tema | Qué orientar en clase |
|:--|:--|
| Mejora continua | La calidad como proceso dinámico. CMMI y ciclo PHVA (planear, hacer, verificar, actuar) como estructuras de mejora. |
| Aseguramiento de la calidad (visión general) | Disciplina preventiva: estándares, planes de calidad, auditorías, revisiones, métricas, gestión de defectos y de configuración. |

> **Nota sobre metodologías:** la introducción habla de "las diferentes metodologías existentes", pero este eje desarrolla sobre todo CMMI y PHVA. Si se quiere cubrir más metodologías, el docente puede ampliar este eje en clase.

### Eje 5 — Cultura y ética

| Tema | Qué orientar en clase |
|:--|:--|
| Cultura y ética | Responsabilidad del ingeniero de software. Equipos maduros vs. inmaduros ante la calidad. Cada defecto como oportunidad de mejora. La calidad como compromiso ético (bancario, médico, educativo). |

### Cierre

| Tema | Qué orientar en clase |
|:--|:--|
| Recursos de la semana | Infografía interactiva y recursos básicos, complementarios y de actualidad. Foros y correo del aula virtual para dudas. |

## 💬 Preguntas para detonar la discusión

1. ¿Conocen un software que "funciona" pero que consideran de baja calidad? ¿Qué característica de ISO/IEC 25010 le falla?
2. Piensen en un fallo de software que haya afectado a usuarios. ¿Qué costo de calidad fue (prevención, evaluación, fallo interno o fallo externo) y qué se pudo haber hecho antes?
3. ¿Qué diferencia hay entre un software **eficiente** y uno **confiable**? ¿Puede ser uno sin el otro?
4. ¿Cómo medirían la mantenibilidad de un sistema existente para justificar una refactorización?
5. Para un sistema de historia clínica, ¿qué características priorizarían y qué métrica usarían para cada una?
6. ¿Qué responsabilidad ética tiene el ingeniero de software cuando el cliente presiona por entregar rápido sin evaluar la calidad?

## ✍️ Actividad sugerida en clase (propuesta del docente)

Dado un sistema real o ficticio, el grupo:

1. Identifica las **3 características de ISO/IEC 25010** más críticas y justifica por qué.
2. Propone **una métrica medible** para cada una (ejemplo: "tiempo de respuesta promedio menor a 2 s con 1000 usuarios concurrentes").
3. Clasifica una actividad de calidad del proyecto como costo de **prevención**, **evaluación**, **fallo interno** o **fallo externo**.
4. Propone **una acción de mejora continua** (siguiendo el ciclo PHVA) para una de las características elegidas.

## 🔑 Glosario rápido

- **Calidad (software):** concepto multidimensional que integra aspectos técnicos, funcionales y organizacionales.
- **Costos de la calidad:** prevención, evaluación, fallos internos y fallos externos.
- **Modelo de calidad:** estructura conceptual que descompone la calidad en atributos evaluables.
- **Métrica:** medida cuantitativa de un atributo del software o del proceso.
- **Estándar:** conjunto de reglas o criterios reconocidos que dan consistencia a procesos o productos.
- **Aseguramiento de la calidad:** actividades planificadas y sistemáticas que dan confianza de que se cumplirán los requisitos de calidad.
- **Mejora continua:** enfoque sistemático para mejorar procesos de forma permanente (CMMI, PHVA).

## ➡️ Puente hacia la Semana 2

La Semana 2 parte de la diferencia entre **verificación** y **validación**, y del papel de las **revisiones técnicas** y las **auditorías**.
