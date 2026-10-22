# Semana 2 — Aseguramiento de la calidad del software: validación, verificación, revisiones y auditorías

**Curso:** Estándares y Métricas de Calidad en el Desarrollo de Software
Los temas marcados como *propuesta* son sugerencias del docente y pueden ajustarse.

## Introducción

Le damos la bienvenida a la semana 2. Durante esta semana revisaremos por qué es importante contar con un plan de verificación, validación y revisión, tanto del producto que se construye como del proceso con el que se construye. Aprenderá a combinar estos mecanismos con las auditorías para mejorar la calidad y la seguridad del software. Detectar y corregir las fallas en la etapa del proceso en que aparecen reduce los costos económicos y los tiempos de retrabajo más adelante.

## 🎯 Resultados de aprendizaje

- Conoce los principios fundamentales de calidad implementando la verificación, validación, revisiones y auditorías.
- Comprende conceptos básicos sobre estándares y métricas.
- Estructura el informe sobre los estándares y metodologías de diseño en la medición de la calidad del software.
- Realiza verificación y validación de software.
- Revisa y audita la construcción de software.

## 🧭 Idea central de la semana

Para comprobar de forma objetiva que lo que se construye cumple lo esperado y responde a una necesidad real, se necesitan mecanismos concretos. La calidad se asegura **desde el proceso** y no solo al final, cuando el producto ya está terminado. Cuanto antes se detecta un defecto (en requisitos, diseño o código, incluidas las fallas de seguridad), menos cuesta corregirlo. Por eso se planifica cómo y cuándo se va a verificar, validar, revisar y auditar.

## 🗂️ Orientación para la clase

| # | Bloque | Qué orientar en clase |
| :-: | :-- | :-- |
| 1 | Repaso y enlace con la Semana 1 | Calidad definida por modelos, medida con métricas y fortalecida con mejora continua. De ahí surge la necesidad de comprobarla con mecanismos objetivos. |
| 2 | Aseguramiento de la calidad (SQA) | Disciplina preventiva: planes de calidad, estándares, revisiones, auditorías, métricas, gestión de defectos y de configuración. Es una función que acompaña todo el ciclo de vida y se apoya en tres pilares: verificación y validación, revisiones técnicas y auditorías. El plan de V&V forma parte del plan de aseguramiento de la calidad, cuyo contenido y procesos define el estándar IEEE 730. |
| 3 | **Verificación** | Pregunta clave: *¿estamos construyendo el producto correctamente?* Comprueba conformidad con especificaciones, estándares, diseño y requisitos. Técnicas: revisiones de código, inspecciones, pruebas unitarias, análisis estático, revisión de documentación. |
| 4 | **Validación** | Pregunta clave: *¿estamos construyendo el producto correcto?* Confirma que el software satisface la necesidad real del usuario. Técnicas: pruebas de aceptación, pruebas con usuarios reales, prototipos, demostraciones, análisis de satisfacción. |
| 5 | **Revisiones técnicas** | Evaluaciones sistemáticas hechas por personas expertas sobre artefactos: requisitos, arquitectura, código, plan de pruebas, informe de métricas. Detectan defectos temprano, cuando cuestan menos. |
| 6 | **Auditorías** | Procesos más formales para verificar cumplimiento de estándares, normativas y procedimientos (norma ISO, requisitos de seguridad, control de cambios). Revisan el producto y también el proceso. |
| 7 | Estándares y metodologías para medir la calidad *(propuesta)* | Base para el informe de la semana: qué estándares y metodologías se usan para diseñar la medición de la calidad (ISO/IEC 25010, CMMI, PHVA vistos en la Semana 1) y qué estándares regulan las revisiones y auditorías (IEEE 1028) y los procesos y el plan de aseguramiento de la calidad (IEEE 730). |
| 8 | Casos prácticos de V&V y auditoría *(propuesta)* | Aplicar verificación, validación, revisión y auditoría a un mismo proyecto para ver en qué se diferencian. |

## ⚖️ Aclaración: cómo distinguir verificación de validación

Una forma común de distinguirlas es que la verificación se hace sobre artefactos sin ejecutar el software (inspecciones, análisis estático) y la validación sobre el software en ejecución. Es una simplificación. Lo que las separa es **contra qué se compara**:

- **Verificación:** se compara contra la especificación (requisitos, diseño, estándares). Puede ser estática (revisión de código) o dinámica (pruebas unitarias, de integración, de carga frente a un requisito de rendimiento, pentesting frente a un requisito de seguridad).
- **Validación:** se compara contra la necesidad real del usuario y del negocio (pruebas de aceptación, pruebas piloto, pruebas de usabilidad).

Al clasificar una actividad en la matriz de V&V, pregúntese primero *"¿frente a qué la estoy comprobando?"* y no *"¿se ejecuta el código?"*.

## 🔍 Cuadro comparativo para trabajar en clase

| Aspecto | Verificación | Validación | Revisión técnica | Auditoría |
|:--|:--|:--|:--|:--|
| Pregunta | ¿Lo construimos bien? | ¿Construimos lo correcto? | ¿El artefacto tiene defectos? | ¿Se cumplen estándares y procedimientos? |
| Se compara contra | Especificaciones, diseño, estándares | Necesidad real del usuario | Criterios de revisión y buenas prácticas | Norma, estándar o procedimiento |
| Quién participa | Equipo técnico | Usuarios y cliente | Personas expertas | Auditor (formal) |
| Cuándo | A lo largo del ciclo de vida | Antes de liberar y con el software en ejecución | En hitos definidos del proyecto | De forma periódica o ante un hito contractual |
| Resultado típico | Defectos corregidos y evidencia de pruebas | Aceptación o rechazo del usuario | Lista de hallazgos y acciones | Informe de auditoría con no conformidades |
| Ejemplos | Análisis estático, pruebas unitarias | Pruebas de aceptación, prototipos | Revisión de requisitos o de código | Auditoría de proceso o de seguridad |

*Las filas "Se compara contra", "Quién participa", "Cuándo" y "Resultado típico" amplían el contenido básico de la semana (se apoyan en IEEE 1028 y en la presentación de la semana); confirmar con el docente.*

## 💬 Preguntas para detonar la discusión

1. ¿Puede un software pasar la verificación y fallar la validación? Den un ejemplo.
2. ¿Qué artefactos de un proyecto de ustedes convendría someter a revisión técnica antes de programar?
3. ¿En qué se diferencia una revisión técnica de una auditoría?
4. ¿Por qué una auditoría revisa también el proceso y no solo el producto?

## 📝 Actividad evaluable de la semana

**Reporte de solución de problemas matemáticos. Evaluación de la calidad del software mediante métricas, verificación y auditoría** (código EDSTV011_A2). Es una actividad **individual**: 5 horas para desarrollarla y 6 horas para consultar los materiales.

**Qué hacer.** Usted es especialista en aseguramiento de la calidad y debe evaluar un sistema antes de su liberación a producción. El escenario es el caso **MediCitas v3.2**, en el documento de apoyo [Semana_2_Caso_MediCitas.md](Semana_2_Actividad/Semana_2_Caso_MediCitas.md). Ahí encontrará la descripción del sistema, el contexto, los actores, las funcionalidades críticas, las restricciones técnicas y regulatorias, y las evidencias (requisitos, bitácora de incidencias, control de cambios y resultados de pruebas). También trae las plantillas de la matriz de verificación y validación, de la lista de control de revisiones técnicas y del formato base de auditoría, y cinco preguntas de selección. Registre los pasos que siguió para resolver el caso y seleccione la respuesta correcta en cada pregunta.

**Qué debe contener el reporte**

1. **Hallazgos de seguridad:** mínimo 5, con su justificación y su impacto.
2. **Verificación y validación:** actividades de verificación (revisiones e inspecciones) y de validación (pruebas orientadas al usuario) aplicables al escenario.
3. **Lista de verificación de revisión técnica:** mínimo 10 ítems.
4. **Plan breve de auditoría:** objetivo, alcance, criterios y evidencias.
5. **Estándar o referencia:** elija uno (por ejemplo, ISO/IEC 25010) y aplíquelo al caso.
6. **Métricas:** mínimo 5, con fórmula o forma de medición y criterio de aceptación.
7. **Conclusiones y recomendaciones priorizadas.**

**Presentación y entrega**

- Portada con título del trabajo, nombre completo, materia y semana, nombre del profesor y fecha de entrega.
- Redacción clara y sin errores de ortografía.
- Fuentes de consulta al final, en formato APA.
- Archivo nombrado `primerapellido_primernombre_nombredelaactividad`, por ejemplo `romero_luis_reportedesoluciondeproblemasmatematicos`. Si usa una herramienta digital, pegue el enlace en un documento Word con sus datos.
- En la plataforma: **Empezar tarea**, cargar el archivo y **Entregar tarea**. Sin este último paso la entrega no queda registrada.

**Recursos básicos**

- Chavarría, A., Oré, S., & Pastor, C. (2016). Aseguramiento de la calidad en el proceso de desarrollo de software utilizando CMMI, TSP y PSP. *Revista Ibérica de Sistemas e Tecnologias de Informação*, (20), 62-77.
- Paredes, L., Benavides, L., & Sánchez, N. (2017). Guía de recomendación para la selección de un modelo de calidad para la mejora de procesos de software (SPI). *Revista Ciencias Estratégicas*.

**Recurso complementario**

- Urrea-Contreras, S., Flores-Rios, B., Astorga-Vargas, M., Ibarra-Esquer, J., González-Navarro, F. F., Velazquez-Solis, P., Albarracín, C., & Ardila, A. (2020). Propuesta de un marco de trabajo para la identificación y selección de algoritmos y herramientas de minería de procesos orientado a las organizaciones de desarrollo de software. *Revista Ibérica de Sistemas e Tecnologias de Informação*, (25), 348-363.

*Los dos recursos básicos tratan de CMMI y de modelos de calidad. Para los estándares de la actividad (ISO/IEC 25010, IEEE 1028 e IEEE 730) apóyese en la presentación de la semana.*

### Rúbrica (total: 5.0 puntos)

| Criterio | Insuficiente | Regular | Bueno | Excelente |
|:--|:--|:--|:--|:--|
| **Ortografía, gramática, cohesión y coherencia** | 0.2 — 8 o más errores que afectan la comprensión técnica | 0.3 — 5 a 7 errores que afectan parcialmente la claridad | 0.4 — 1 a 4 errores, redacción clara | **0.5** — Sin errores; redacción técnica clara, coherente y precisa |
| **Aplicación de verificación y validación** | 0.6 — Actividades superficiales y sin relación clara con el escenario | 0.9 — Actividades parcialmente adecuadas | 1.2 — Actividades claras; diferencia correctamente verificación y validación | **1.5** — Actividades completas, técnicamente fundamentadas y alineadas con el escenario |
| **Diseño de revisiones y auditoría** | 0.6 — Propuesta incompleta o sin criterios definidos | 0.9 — Procesos con estructura básica | 1.2 — Procesos con criterios y evidencias claras | **1.5** — Procesos estructurados, con alcance, criterios, evidencias y enfoque técnico sólido |
| **Uso de estándares y métricas de calidad** | 0.5 — Estándares o métricas sin aplicación clara al caso | 0.8 — Aplica parcialmente un estándar y define métricas básicas | 1.1 — Integra un estándar pertinente y métricas adecuadas al escenario | **1.5** — Integra un estándar reconocido (p. ej., ISO/IEC 25010) y define métricas claras, medibles y alineadas con atributos de calidad |

*Si no se entrega la actividad, se envía otra distinta o se detecta plagio total, la calificación es 0.0 en todos los criterios. Los hallazgos de seguridad y las conclusiones no tienen una fila propia: se valoran dentro de V&V y de estándares y métricas. Confirmar con el docente.*

## ✍️ Actividad sugerida en clase (propuesta)

Como práctica previa a la actividad evaluable, con un caso de proyecto (ejemplo: una tienda en línea con módulo de pago):

1. Definir **dos actividades de verificación** y **dos de validación**, indicando cuándo se ejecutan.
2. Elegir **un artefacto** para revisión técnica y listar qué criterios usaría el revisor.
3. Redactar **tres preguntas de auditoría** sobre el cumplimiento de un estándar.

## 🔑 Glosario rápido

- **Verificación:** comprobar que el producto se construye conforme a especificaciones, estándares y diseño.
- **Validación:** confirmar que el producto satisface la necesidad real del usuario.
- **Revisión técnica:** evaluación sistemática de un artefacto del proyecto por personas expertas.
- **Auditoría:** proceso formal que verifica el cumplimiento de estándares, normativas o procedimientos.
- **Plan de V&V:** documento que define qué se verifica y valida, con qué técnicas, cuándo y quién lo hace; forma parte del plan de aseguramiento de la calidad.
- **Inspección:** revisión formal con roles definidos y listas de verificación para detectar defectos en un artefacto (IEEE 1028).
- **Análisis estático:** revisión del código sin ejecutarlo.
- **Prueba de aceptación:** prueba con la que el usuario o cliente confirma que el software cubre su necesidad.

## ➡️ Puente hacia la Semana 3

Las revisiones, auditorías y pruebas producen hallazgos. La Semana 3 trata de **caracterizar esos defectos** de software.
