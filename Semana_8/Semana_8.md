# Semana 8 — Herramientas de calidad de software

**Curso:** Estándares y Métricas de Calidad en el Desarrollo de Software
Los temas marcados como *propuesta* son sugerencias del docente y pueden ajustarse.

## Introducción

Es la semana de cierre. Se integra lo visto: el aseguramiento de la calidad (QA) como función preventiva a lo largo del ciclo de vida, el marco de verificación y validación con el ciclo PDCA, el catálogo de técnicas y herramientas de QA, las métricas de interpretación y su integración en el pipeline de CI/CD. La práctica de pruebas en Java (los seis talleres) se trabaja en la [Semana 7](../Semana_7/Semana_7.md).

## 🎯 Resultados de aprendizaje

- Implementa el aseguramiento de la calidad en la construcción de software.
- Aplica las técnicas de gestión de la calidad del software.

## 🧭 Idea central de la semana

La técnica precede a la herramienta: primero se define qué característica de calidad (ISO/IEC 25010) se quiere asegurar, luego la técnica y al final la herramienta. La verificación y validación sin el ciclo PDCA produce datos sin mejora continua. La calidad se gestiona desde los requisitos, a lo largo de todo el ciclo de vida.

## 🗂️ Orientación para la clase

| # | Bloque | Qué orientar en clase |
|:-:|:--|:--|
| 1 | QA: concepto e importancia | Definición de calidad de ISO 9000 (grado en que las características inherentes cumplen los requisitos); QA como función estratégica y preventiva, no solo pruebas tardías. |
| 2 | Marco de V&V con PDCA | Verificación (¿construimos bien el producto?) y validación (¿construimos el producto correcto?), repasando la Semana 2, integradas en el ciclo PDCA. |
| 3 | Técnicas estáticas | Revisiones de adherencia, inspecciones, análisis estático, revisión de código y deuda técnica. |
| 4 | Técnicas dinámicas | Unitarias, integración, API, UI, regresión, aceptación, rendimiento, seguridad, mutación y humo. |
| 5 | Herramientas de QA | SonarQube (escala A-E), Selenium WebDriver, JUnit 5 / TestNG, JIRA + Xray, JMeter. |
| 6 | Gestión y trazabilidad | Ciclo de vida del defecto, trazabilidad requisito-prueba y análisis de causa raíz. |
| 7 | Métricas: medición e interpretación | Densidad de defectos, cobertura, DDE y otras, con su interpretación y la acción si se deterioran. |
| 8 | QA en CI/CD | *Deployment pipeline* (commit stage, acceptance stage, performance stage) y *quality gates*. |
| 9 | Actividad práctica: análisis integrador | Caso DataFlow Solutions con pipeline en Jenkins: interpretar sus métricas y proponer acciones. |

## 📂 Materiales de la semana

Apoyan la semana [Calidad_del_Backend.md](Calidad_del_Backend.md) (segunda medición de SonarQube del backend de ejemplo, que continúa los [reportes de la Semana 7](../Semana_7/Semana_7_Caso_de_estudio/)) y las presentaciones de la semana.

## ⚠️ Puntos a aclarar en clase

- **Talleres.** Los seis talleres de pruebas en Java se movieron a la Semana 7 porque en esta semana no alcanza el tiempo para realizarlos. Los resultados "implementa" y "aplica" de esta semana se apoyan en esa práctica; falta decidir si se ajusta su redacción en el plan del curso.
- **Nombres de las características.** Una presentación nombra las características como "funcionalidad, confiabilidad, eficiencia" (ISO/IEC 9126). Usar los nombres de ISO/IEC 25010 de la Semana 1: adecuación funcional, fiabilidad y eficiencia del desempeño.
- **Densidad por KLOC.** Presentarla como métrica clásica y complementarla con las de la Semana 2.
- **Proyecto real.** `Calidad_del_Backend.md` y los reportes de deuda técnica analizan un backend real (`backend-demo`); sirven de ejemplo, no son un entregable.
- **Deuda técnica.** Los reportes `01` a `03` están solo en la Semana 7; `Calidad_del_Backend.md` los continúa con una medición posterior.

## 💬 Preguntas para detonar la discusión

1. ¿Qué diferencia hay entre una prueba estática y una dinámica? Den un ejemplo de cada una.
2. ¿Qué métrica del pipeline de DataFlow les preocupa más y qué acción tomarían?
3. ¿Qué *quality gate* pondrían en el commit stage de su proyecto?
4. ¿Por qué la técnica va antes que la herramienta?
5. ¿Cómo cerraría el ciclo PDCA un defecto detectado en producción?

## 📝 Evaluación de la semana

**MA Evaluación 8** (aula virtual, tarea evaluativa). Es una presentación interactiva de 14 diapositivas con **tres preguntas** de autoevaluación en el recorrido: una de selección múltiple (finalidad de la gestión de la calidad del software), una de completar frases y una de verdadero o falso (si la calidad se aplica solo al final del proyecto). Al terminar, el estudiante envía sus respuestas. La calificación se suma a la evaluación final del curso. **No hay entrega de video ni de documento.**

Contenido de la presentación:

| Tema | Qué trata |
|:--|:--|
| Calidad del software | La gestión de la calidad como conjunto de procesos que asegura un producto confiable que cumple los requisitos. |
| Procesos de QA | Planificación de QA, gestión de defectos y pruebas funcionales; por qué las herramientas no garantizan la calidad por sí solas. |
| Actividad QA | Preguntas en tarjetas sobre planificación, defectos y pruebas funcionales. |
| Herramientas de QA | Pruebas automatizadas, análisis de código y control de versiones, seguimiento de errores. |
| Técnicas de calidad | Pruebas de sistema, revisión de código y evaluación de métricas; seguimiento continuo y registro de fallos. |
| Caso Netflix | Pruebas antes de liberar, revisión de código, métricas y registro de fallos. |
| Cierre y tiempos de la gestión | Corregir temprano cuesta menos; la gestión de calidad se aplica durante todo el desarrollo. |

> **Error en el aula virtual:** la tarea tiene asociada la rúbrica **"Rubrica Video"**, que no corresponde a esta evaluación (no hay video ni documento; las tres preguntas se califican en la propia presentación). No se usa como instrumento de la semana. Falta asociar la rúbrica correcta o retirar esta en la plataforma.

La evaluación es conceptual y sigue la presentación de la semana (QA, V&V y herramientas). **No evalúa los talleres de Java** (ahora en la Semana 7).

## ✍️ Actividad sugerida en clase (propuesta)

Con el caso **DataFlow Solutions**, ubicar en el pipeline de CI/CD (commit, acceptance y performance stage) la técnica, la herramienta y la métrica que corresponde a cada etapa.

## 🔑 Glosario rápido

- **QA:** actividades planificadas y sistemáticas que dan confianza de que se cumplirán los requisitos de calidad.
- **PDCA:** ciclo planear, hacer, verificar, actuar.
- **Prueba unitaria / de integración / de aceptación:** componente aislado, componentes reales juntos y cumplimiento de criterios acordados con el cliente.
- **Prueba de mutación:** introduce defectos artificiales para medir la efectividad de las pruebas.
- **Quality gate:** umbral que debe cumplir el código para avanzar en el pipeline.
- **CI/CD:** integración y entrega continuas.
