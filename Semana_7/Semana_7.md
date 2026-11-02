# Semana 7 — Técnicas de gestión y medición en la calidad de software

**Curso:** Estándares y Métricas de Calidad en el Desarrollo de Software
Los temas marcados como *propuesta* son sugerencias del docente y pueden ajustarse.

## Introducción

La Semana 6 presentó las herramientas. Esta semana pregunta qué técnica sirve a qué objetivo de calidad, y cómo medir si funcionó. Se separan tres conceptos que suelen confundirse (**técnica, herramienta y estándar**), se clasifican las técnicas con dos ejes independientes (ISO/IEC 25010 para el producto y CMMI nivel 3 para el proceso) y se miden los resultados con métricas, incluida la **deuda técnica**. El artículo de pruebas continuas muestra cómo una organización financiera real sostiene la calidad con la pirámide de pruebas, y los **seis talleres** de la semana llevan esa pirámide al código con pruebas unitarias, de integración y de aceptación en Java.

## 🎯 Resultados de aprendizaje

- Establece las herramientas de calidad de software.
- Clasifica las técnicas de gestión de la calidad del software.

## 🧭 Idea central de la semana

El estándar define el marco, la técnica define el método y la herramienta automatiza su ejecución. La herramienta se elige **después** del diagnóstico (Pareto, Ishikawa), no por moda. Una misma técnica se ubica en un área de proceso CMMI y, a la vez, mejora una o varias características de ISO/IEC 25010; los dos ejes no son intercambiables.

## 🗂️ Orientación para la clase

| # | Bloque | Qué orientar en clase |
|:-:|:--|:--|
| 1 | Técnica, herramienta y estándar | Definiciones y ejemplos: revisión por pares y TDD (técnicas), SonarQube y Karate (herramientas), ISO/IEC 25010 y CMMI (estándar o modelo). |
| 2 | Eje 1: ISO/IEC 25010 | Qué atributo del producto mejora la técnica. Las ocho características de la Semana 1. |
| 3 | Eje 2: CMMI nivel 3 | En qué área de proceso se institucionaliza la técnica: REQM, VER, VAL, PPQA y RSKM. |
| 4 | Cruce de ejes | Tabla técnica × característica × área de proceso (revisión por pares → mantenibilidad y VER; quality gate en CI → mantenibilidad, seguridad y PPQA; matriz de trazabilidad → adecuación funcional y REQM). |
| 5 | Herramientas de diagnóstico y de ejecución | Ishikawa (causa raíz), Pareto (priorización), SonarQube, Karate y JIRA + Xray. |
| 6 | Métricas que hacen tangible la calidad | Densidad de defectos, cobertura automatizada, DDE (eficiencia de detección), defectos escapados, MTTR, complejidad ciclomática y NPS. |
| 7 | Caso DataFlow Solutions, InventoryPro v3 | Migración a microservicios; detección temprana de 54 % a 89 %, retrabajo −58 %, ciclo de release de 6 a 4 semanas, tickets de soporte −61 %. |
| 8 | Pruebas continuas (artículo) | Pirámide de Cohn; pruebas unitarias solitarias y sociables; TDD; pruebas de contrato y de componente; Karate para aceptación; E2E con BDD; rendimiento; DevSecOps con OWASP ZAP. Norma ISO/IEC/IEEE 29119-4. |
| 9 | Caso de crédito digital | Gestión y medición de calidad en una plataforma de crédito, con técnicas clasificadas por ISO/IEC 25010 y CMMI. |
| 10 | Deuda técnica con SonarQube Cloud | Metodología SQALE; code smells, deuda, *debt ratio*, rating A-E y esfuerzo para llegar a A. Documentos `01` a `03` y `METRICAS_DE_CALIDAD.md`. |
| 11 | Talleres de pruebas en Java | Práctica de la pirámide de pruebas: unitarias con mocks, integración (MockMvc, Testcontainers) y aceptación BDD con Cucumber. Ver la sección de talleres. |

## 🛠️ Talleres de la semana

Se trabajan en [Semana_7_Talleres](Semana_7_Talleres/). Orden sugerido: del 1 al 3 como base y del 4 al 6 como refuerzo.

| Taller | Contenido |
|:--|:--|
| [Taller 1](Semana_7_Talleres/SEMANA_7_TALLER_1.md) | Pruebas unitarias con mocks, de integración y de aceptación BDD sobre una aplicación Java de gestión de usuarios. |
| [Taller 2](Semana_7_Talleres/SEMANA_7_TALLER_2.md) | CRUD con Spring Boot y Maven, con pruebas con Mockito, MockMvc y Cucumber. |
| [Taller 3](Semana_7_Talleres/SEMANA_7_TALLER_3.md) | Pruebas de integración de Spring Boot con Testcontainers. |
| [Taller 4](Semana_7_Talleres/SEMANA_7_TALLER_4.md) | Proyecto *User Quality Demo*: tres niveles de pruebas y tabla comparativa. |
| [Taller 5](Semana_7_Talleres/SEMANA_7_TALLER_5.md) | Escala el proyecto del Taller 4 a API REST y Cucumber. |
| [Taller 6](Semana_7_Talleres/SEMANA_7_TALLER_6.md) | Proyecto de gestión de ventas con base de datos `bd_ventas.sql` y las tres suites de pruebas. |

Los talleres 4, 5 y 6 repiten el proyecto de los talleres 1 y 2 en distinto nivel; indicar al grupo el orden de trabajo y cuáles son obligatorios.

## 📂 Materiales de la semana

| Archivo | Uso |
|:--|:--|
| `semana_7_002_ejercicios.md` y `Semana_7_002_ejercicios_profesor.pptx` | Técnica/herramienta/estándar, ejes y caso DataFlow. |
| `Semana_7_Pruebas_continuas_articulo_profesor.pptx` y artículo *Pruebas Continuas de Software* | Pirámide de pruebas y cultura DevSecOps. |
| `Semana_7_Caso_de_Estudio_Gestion_Calidad_Software.md` | Caso de crédito digital. |
| `Medicion_Deuda_Tecnica_SonarQube_Cloud.md` | Deuda técnica y SQALE. |
| `Semana_7_Caso_de_estudio/` | Tutorial y dos reportes de deuda técnica (manual y SonarQube) y métricas del backend `backend-demo`. |
| `Semana_7_Artículos/` | Apuntes para gestionar actividades de calidad, Pruebas Continuas y Dialnet (evaluación de características de un SI). |

## ⚠️ Puntos a aclarar en clase

- **Cifras del caso.** Los valores de DataFlow y del caso de crédito son hipotéticos y con fines didácticos; discutir qué evidencia haría falta para afirmar causalidad.
- **Backend real.** `Semana_7_Caso_de_estudio/` analiza un proyecto real (`backend-demo`) como ejemplo de deuda técnica. No es un entregable del curso.
- **Densidad por KLOC.** El caso la usa, mientras que la Semana 2 propone métricas más actuales (tasa de fuga, DORA). Presentarla como métrica clásica complementaria.
- **Duplicados.** Los *Apuntes para gestionar actividades* están repetidos en las semanas 6, 7 y 8. Los reportes de deuda técnica `01` a `03` quedan solo en esta semana; la Semana 8 conserva `Calidad_del_Backend.md` como segunda medición.

## 💬 Preguntas para detonar la discusión

1. ¿Por qué ISO/IEC 25010 y CMMI no son ejes intercambiables?
2. Para una técnica que ustedes usen (por ejemplo, revisión de código), ¿a qué característica y a qué área de proceso corresponde?
3. ¿Qué mostraría un diagrama de Pareto en un proyecto con muchos defectos de interfaz y pocos de lógica?
4. ¿Por qué expresar la deuda técnica en tiempo ayuda más a gestionar que contar *code smells*?
5. ¿Qué parte de la pirámide de Cohn falta en su proyecto?

## 📝 Actividad de la semana

**Esta semana no tiene actividad evaluable.** Los materiales son de estudio y de práctica; los talleres son práctica guiada, sin entrega calificada.

## ✍️ Actividad sugerida en clase (propuesta)

Elegir **tres técnicas** que use el grupo y completar la tabla técnica → características de ISO/IEC 25010 → área de proceso CMMI → herramienta → métrica que mostraría su efecto.

## 🔑 Glosario rápido

- **Técnica / herramienta / estándar:** método, instrumento que lo automatiza y marco de referencia.
- **REQM, VER, VAL, PPQA, RSKM:** áreas de proceso de CMMI nivel 3 (requisitos, verificación, validación, aseguramiento de calidad de proceso y producto, riesgos).
- **DDE:** eficiencia de detección de defectos (defectos hallados antes de liberar / defectos totales).
- **MTTR:** tiempo medio de resolución.
- **Pirámide de Cohn:** estrategia de pruebas con muchas unitarias en la base, menos de integración y aceptación, y pocas E2E en la cima.
- **TDD:** desarrollo guiado por pruebas (rojo, verde, refactorizar).
- **SQALE:** metodología para expresar la deuda técnica como tiempo de remediación.
- **Debt ratio:** relación entre el costo de remediación y el costo de desarrollo.

## ➡️ Puente hacia la Semana 8

La Semana 8 integra lo visto: marco de V&V con PDCA, técnicas y herramientas de QA, y QA en CI/CD. Cierra con la evaluación de la semana.
