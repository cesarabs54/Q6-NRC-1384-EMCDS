# Semana 4 — Especificación de requisitos del software

**Curso:** Estándares y Métricas de Calidad en el Desarrollo de Software
Los temas marcados como *propuesta* son sugerencias del docente y pueden ajustarse.

## Introducción

Las semanas 2 y 3 mostraron cómo se comprueba la calidad y cómo se caracterizan los defectos. Esta semana se mira al origen: **la especificación de requisitos**. Un requisito ambiguo, incompleto o inconsistente produce defectos que luego hay que detectar, clasificar y corregir. Por eso la especificación es el primer mecanismo preventivo de calidad. Se apoya en IEEE 830 (hoy ISO/IEC/IEEE 29148), en ISO/IEC/IEEE 12207, en los modelos de mejora de procesos (SPI) y en un modelo procedimental para obtener requisitos funcionales. El caso de CMMI, TSP y PSP muestra con datos cómo un proceso integrado reduce defectos y costo de calidad.

## 🎯 Resultados de aprendizaje

- Realiza la especificación del software.

## 🧭 Idea central de la semana

Requisitos claros → menos defectos → menor costo de calidad → mayor rentabilidad. Clasificar los requisitos en funcionales y no funcionales no basta: hace falta un **procedimiento** que diga cómo obtenerlos y documentarlos, y un conjunto de **métricas** que permita saber si la especificación es buena.

## 🗂️ Orientación para la clase

| # | Bloque | Qué orientar en clase | Material |
|:-:|:--|:--|:--|
| 1 | Enlace con la Semana 3 | Los defectos de origen "Requisitos" (ambigüedad, omisiones, contradicciones) se previenen aquí. | — |
| 2 | Introducción: requisitos y calidad | La especificación como base de la calidad. Relación requisitos claros → menos defectos y retrabajo. | `SEMANA_4_01_Especificacion_requisitos.pptx`, `SEMANA_4_02_Requisitos_calidad.pptx` |
| 3 | IEEE 830 (hoy ISO/IEC/IEEE 29148) | Estructura del documento de requisitos (SRS): introducción, descripción general y requisitos específicos. Un requisito debe ser verificable, no ambiguo, completo y consistente. | Ídem |
| 4 | ISO/IEC/IEEE 12207 | Procesos del ciclo de vida (adquisición, suministro, desarrollo, operación, mantenimiento) y sus procesos de verificación, validación y aseguramiento. Enlaza con la Semana 2. | Ídem |
| 5 | Modelos SPI y requisitos | CMMI, MoProSoft, Competisoft, MPS.Br e IT Mark. Elegir mal el modelo puede ser un problema y no una mejora (Merchán et al., 2017). | Ídem y artículo 02 |
| 6 | Modelo procedimental de requisitos | Contexto y stakeholders → educción → elicitación → especificación. Artefactos: tabla de escenarios, tabla de usuarios, acta de objetivos, cuestionarios, actas, catálogo de RF y fichas de especificación. | Cornejo-Aparicio et al. (2020) |
| 7 | Requisitos, métricas y mejora continua | PCC (porcentaje de costo de calidad), CDP (defectos por proyecto), PVC (variación de costo), PCS (clientes satisfechos) y densidad de defectos. | Presentación 01, diapositivas 13-14 |
| 8 | Complemento: RNF, criterios de aceptación, trazabilidad y puntos de control | RNF medibles y clasificados con ISO/IEC 25010; criterios Dado-Cuando-Entonces; matriz requisito → caso de uso → caso de prueba → métrica; puntos de control de V&V. | Presentación 01, diapositiva 26 |
| 9 | Caso de estudio CMMI, TSP y PSP | Modelo integrado proceso-equipo-persona. En 22 proyectos el PCC máximo bajó de 19,85 % a 7,41 % y los defectos por proyecto, de 249 a 95. | `SEMANA_4_02_CMMI_TSP_PSP_Caso_estudio.pptx`, artículo 01 |
| 10 | Ejercicios prácticos | Citas médicas (contexto, escenarios, stakeholders, RF01) y trazabilidad requisitos-métricas en una fintech. Tablero de métricas y plan de integración de PSP y TSP. Traen respuestas modelo. | `SEMANA_4_01_Ejercicios_practicos.pptx` y ejercicios de las otras presentaciones |

## ⚠️ Puntos a aclarar en clase

- **Densidad de defectos por KLOC.** La Semana 2 la reemplaza por métricas más actuales (tasa de fuga, cobertura, DORA), pero las presentaciones de esta semana y del caso CMMI la siguen usando. Presentarla como métrica clásica, útil para comparar, y no como la única.
- **UML en la actividad.** La actividad pide diagrama de casos de uso y diagrama de clases conceptual, pero las presentaciones desarrollan el modelo procedimental y no enseñan UML. Se asume UML como conocimiento previo, o el docente lo refuerza en clase *(propuesta)*.
- **Ciclo de vida.** La actividad pide justificar un modelo de ciclo de vida. La Semana 5 trae un anexo de métricas por tipo de ciclo (cascada, iterativo, evolutivo, ágil e híbrido) que puede servir de apoyo.

## 💬 Preguntas para detonar la discusión

1. ¿Qué defectos de la clasificación por origen de la Semana 3 se previenen con una buena especificación?
2. ¿Cómo comprobarían que un requisito es verificable? Escriban un criterio de aceptación en formato Dado-Cuando-Entonces.
3. ¿Por qué no basta con clasificar los requisitos en funcionales y no funcionales?
4. ¿Qué aporta PSP (persona) que no aporta CMMI (organización)?
5. ¿Qué requisito no funcional medible pondrían a un sistema de citas médicas y con qué característica de ISO/IEC 25010 se relaciona?

## 📝 Actividad evaluable de la semana

**Modelado digital UML. Sistema de software con integración del aseguramiento de la calidad** (código EDSTV011_A4, versión V3 en [EDSTV011_A4_V3.pdf](Semana_4_Actividad/EDSTV011_A4_V3.pdf)). Actividad **individual**: 5 horas de desarrollo y 6 horas de consulta de materiales. Escenario: lo asigna el docente; si no, puede usarse el sistema de préstamos y reservas de una biblioteca universitaria con dos sedes.

**El modelo debe contener:** especificación estructurada desde la perspectiva del aseguramiento de la calidad, diagrama de casos de uso, diagrama de clases conceptual, requisitos funcionales y no funcionales, criterios de aceptación, trazabilidad básica requisito-caso de prueba y puntos de control de calidad en el ciclo de vida (con el modelo de ciclo de vida justificado).

**El documento debe contener:** portada, introducción, desarrollo, planeación, modelado (imágenes PNG o PDF, o enlace) y conclusiones, con referencias APA 7.

**Recursos básicos:** Cornejo-Aparicio et al. (2020) y Merchán Paredes et al. (2017). **Complementarios:** Bermón Angarita (2021) y Espejo Chavarría et al. (2016).

### Rúbrica (total: 5.0 puntos)

| Criterio | Puntaje máximo |
|:--|:-:|
| Claridad y precisión técnica en la especificación | 0.5 |
| Definición y estructuración de requisitos | 1.3 |
| Modelado UML y coherencia estructural | 1.3 |
| Integración de criterios de aseguramiento de calidad | 1.4 |
| Documento, redacción y referencias APA | 0.5 |

*Si hay plagio total, se envía otra actividad o no se entrega, la calificación es 0.0 en todos los criterios. La V2 de la actividad hablaba de un "modelado digital 3D" y no pedía escenario base; la V3 corrige ambos puntos y es la vigente.*

## ✍️ Actividad sugerida en clase (propuesta)

Con el sistema de citas médicas: redactar **tres requisitos funcionales**, escribir **un criterio de aceptación** para cada uno y armar una **mini matriz de trazabilidad** requisito → caso de prueba.

## 🔑 Glosario rápido

- **Requisito funcional (RF):** comportamiento que el sistema debe ofrecer.
- **Requisito no funcional (RNF):** atributo de calidad medible y verificable (rendimiento, disponibilidad, seguridad).
- **SRS:** documento de especificación de requisitos de software (IEEE 830, hoy ISO/IEC/IEEE 29148).
- **Educción:** preparación de la captura (contraste de usuarios y escenarios, planificación de entrevistas).
- **Elicitación:** análisis y agrupación de lo capturado en las entrevistas.
- **Criterio de aceptación:** condición verificable que debe cumplir un requisito (Dado-Cuando-Entonces).
- **Trazabilidad:** vínculo requisito → caso de uso → caso de prueba → métrica.
- **SPI:** mejora de procesos de software (CMMI, MoProSoft, Competisoft, MPS.Br, IT Mark).
- **PCC, CDP, PVC, PCS:** costo de calidad, defectos por proyecto, variación de costo y clientes satisfechos.
- **PSP / TSP:** procesos personal y de equipo de software.

## ➡️ Puente hacia la Semana 5

La Semana 5 aplica el modelo procedimental completo (ocho pasos) a dos casos nuevos y revisa los **criterios y métricas de calidad** de los requisitos funcionales.
