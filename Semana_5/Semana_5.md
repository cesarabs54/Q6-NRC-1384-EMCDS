# Semana 5 — Técnicas de gestión de la calidad

**Curso:** Estándares y Métricas de Calidad en el Desarrollo de Software
Los temas marcados como *propuesta* son sugerencias del docente y pueden ajustarse.

## Introducción

Esta semana lleva a la práctica lo visto en la Semana 4. Se aplica el **modelo procedimental de ocho pasos** para especificar requisitos funcionales a dos casos completos, y se revisa cómo **medir la calidad de esos requisitos** con criterios, métricas e instrumentos. Aquí las "técnicas de gestión de la calidad" son técnicas de calidad aplicadas a la especificación: entrevistas, actas validadas, matrices de cobertura, control de versiones del catálogo, revisiones técnicas y métricas por paso.

## 🎯 Resultados de aprendizaje

- Realiza la especificación del software.
- Identifica los requisitos de calidad del software.

## 🧭 Idea central de la semana

Especificar bien es un proceso con entregables verificables en cada paso, no un documento escrito de una vez. Cada artefacto (acta, ficha, catálogo) se valida, se versiona y se mide. Así un requisito deja de ser una opinión y pasa a ser algo **correcto, no ambiguo, completo, consistente, verificable, trazable, modificable, priorizado y factible**.

## 🗂️ Orientación para la clase

### Los ocho pasos del modelo procedimental

| Paso | Fase | Entregable |
|:-:|:--|:--|
| 1 | Contexto de uso y propósito | Tabla de escenarios, tabla de estereotipos de usuario y acta de definición de objetivos. |
| 2 | Stakeholders | Tabla de stakeholders y relación operativa de personal. |
| 3 | Educción: preparación | Matrices usuario × escenario y objetivo × escenario. |
| 4 | Educción: captura | Fichas de entrevista, lista de chequeo y acta de entrevista. |
| 5 | Educción: cierre | Registro consolidado de actas validadas y firmadas (*member checking*). |
| 6 | Elicitación | Fichas de caracterización: agrupación por funcionalidad, satisfacción mínima aceptable, solapamientos y vacíos. |
| 7 | Especificación: inventario | Catálogo de requisitos funcionales con versión, estado y trazabilidad (ejemplo: 21 RF en 6 módulos). |
| 8 | Especificación: formalización | Fichas SRS por requisito (IEEE-STD-830): acciones del sistema y del usuario, flujos alternos y restricciones. |

### Calidad de los requisitos

| Característica | Métrica | Meta de referencia |
|:--|:--|:--|
| Correcto | Tasa de defectos de corrección (RF incorrectos / RF totales) | < 5 % |
| No ambiguo | Índice de ambigüedad (RF con términos vagos / RF totales) | 0 % |
| Completo | Cobertura de completitud (campos especificados / requeridos) | ≥ 95 % |
| Consistente | Densidad de conflictos (conflictos / RF totales) | 0 |
| Verificable | RF con criterio de aceptación / RF totales | 100 % |
| Trazable | RF trazados / RF totales | 100 % |
| Modificable | Índice de duplicación y tasa de impacto de cambio | ID = 0; TIC < 1,5 |
| Priorizado | RF con prioridad asignada / RF totales | 100 % |
| Factible | RF validados técnicamente / RF totales | 100 % antes de la línea base |

*Las metas son referencia de industria y se calibran según dominio, criticidad y madurez. Fuente: anexo `Métricas_Instrumentos_Calidad_Requisitos_Funcionales.docx`. La presentación del Caso 2 liga además un criterio de calidad medible a cada paso del modelo (ISO/IEC 25010 e IEEE-830).*

### Métricas según el ciclo de vida

El anexo `Métricas_Instrumentos_Calidad_según_Clasificación_Desarrollo_Software.docx` relaciona métricas e instrumentos con el tipo de desarrollo:

| Ciclo de vida | Ejemplos de métricas |
|:--|:--|
| Predictivo (cascada) | Densidad de defectos por fase, completitud de entregables, varianza de cronograma. |
| Iterativo e incremental | Velocidad, deuda técnica acumulada, defectos residuales por iteración. |
| Evolutivo (espiral, RUP) | Reducción de riesgo por ciclo, cobertura de prototipado, cambio de arquitectura. |
| Ágil | Lead time y cycle time, cobertura de pruebas automatizadas, tasa de escapados a producción. |
| Híbrido (SAFe) | Predictibilidad del PI, alineación estratégica, tiempo de resolución de dependencias. |

Sirve para justificar el modelo de ciclo de vida que pide la actividad de la Semana 4 y enlaza con las métricas de la Semana 2 (tasa de fuga, DORA).

## 📂 Materiales de la semana

| Archivo | Uso |
|:--|:--|
| `SEMANA_5_Caso_2_Sistema_gestión_académica_profesor.pptx` / `.docx` | Ejemplo resuelto completo (Universidad Regional del Conocimiento). Incluye rúbrica de evaluación (versión profesor). |
| `SEMANA_5_Caso_2_Sistema_gestión_académica.docx` / `.pdf` | Guía del estudiante del mismo caso. |
| `SEMANA_5_Caso_1_Sistema_gestión_citas_médicas.docx` | Ejercicio en equipos de 3 a 4 personas (Clínica San Rafael), siguiendo los 8 pasos. |
| `SEMANA_5_Caso_1_..._profesor.docx` | Solución del Caso 1. |
| `Semana_5_Anexo/` | Dos documentos de métricas e instrumentos y la imagen sobre la importancia de los requisitos. |
| `Modelo Procedimental para la Especificación de Requisitos Funcionales.txt` | Texto del artículo de Cornejo-Aparicio et al. (2020), el mismo recurso básico de la Semana 4. |

## ⚠️ Puntos a aclarar en clase

- **Título y contenido.** "Técnicas de gestión de la calidad" es el título del plan del curso, pero el material es especificación de requisitos con criterios de calidad. La clasificación de las técnicas de gestión de la calidad se desarrolla en la Semana 7.
- **Sin actividad evaluable.** La semana 5 no tiene actividad ni foro calificados. Los dos casos son ejercicios de clase, sin código de actividad (como EDSTV011_A2, F3 o A4) ni rúbrica para el estudiante. Es una semana de práctica y de preparación para la actividad de la Semana 4.
- **Mismo dominio.** Citas médicas ya apareció en la Semana 2 (MediCitas) y en la Semana 4. Para el Caso 1, pedir que no copien artefactos anteriores.

## 💬 Preguntas para detonar la discusión

1. ¿Qué se pierde si se salta la validación de las actas de entrevista (paso 5)?
2. ¿Qué indica un "vacío" en una ficha de caracterización y qué se hace con él?
3. Un catálogo con 21 RF, 12 aprobados, 4 en revisión y 5 propuestos: ¿está listo para una línea base? ¿Qué métricas del cuadro anterior consultarían?
4. ¿Cuál de las métricas de calidad de requisitos es más difícil de medir y por qué?

## ✍️ Actividad sugerida en clase (propuesta)

Con el **Caso 1 (Clínica San Rafael)**, en equipos: completar los pasos 1 a 3, redactar una ficha SRS de un requisito (por ejemplo, agendamiento de cita) y calcular dos métricas del cuadro de calidad sobre su catálogo (por ejemplo, índice de ambigüedad y cobertura de verificabilidad).

## 🔑 Glosario rápido

- **Escenario de despliegue:** entorno donde se usará el software.
- **Estereotipo de usuario:** perfil de usuario y para qué usa el software.
- **Matriz usuario × escenario:** cobertura que asegura que todos los usuarios sean entrevistados.
- **Acta de entrevista:** resumen de la entrevista validado y firmado por el entrevistado.
- **Member checking:** validación de lo anotado con el propio entrevistado.
- **Ficha de caracterización:** agrupación de lo capturado por funcionalidad, con prioridad MoSCoW.
- **Catálogo de RF:** índice versionado de todos los requisitos funcionales.
- **Ficha SRS:** especificación individual de un requisito (IEEE-STD-830).
- **RTM:** matriz de trazabilidad de requisitos.

## ➡️ Puente hacia la Semana 6

La Semana 6 pasa de los requisitos a las **herramientas** que sostienen la calidad y a los requisitos de calidad del software.
