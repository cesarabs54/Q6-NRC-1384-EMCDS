# Semana 3 — Aseguramiento de la calidad del software: caracterización de defectos

**Curso:** Estándares y Métricas de Calidad en el Desarrollo de Software
Los temas marcados como *propuesta* son sugerencias del docente y pueden ajustarse.

## Introducción

Le damos la bienvenida a la semana 3. En la semana 2 vimos cómo se comprueba la calidad mediante verificación, validación, revisiones y auditorías. Esas actividades producen **hallazgos**, y esta semana aprenderá a tratarlos de forma sistemática: **caracterizar los defectos** del software (qué tipo son, qué tan graves son, dónde se originaron y con qué frecuencia aparecen). Esa caracterización es la materia prima de las métricas de calidad y de la mejora continua. Se apoya en dos referentes: el estándar **ISO/IEC 29110**, pensado para entidades muy pequeñas, y el modelo de pruebas **TMMi nivel 2**.

## 🎯 Resultados de aprendizaje

- Identifica el aseguramiento de la calidad del software.
- Identifica la caracterización de los defectos de software.
- Contribuye al resultado del foro: *especifica la utilización de técnicas de gestión de la calidad, estándares y metodologías en el diseño y la medición de la calidad del software.*

## 🧭 Idea central de la semana

Un **defecto** es cualquier desviación entre el comportamiento esperado y el comportamiento real del software. Registrarlo no basta: hay que **caracterizarlo** (tipo, severidad, origen, ciclo en que se detectó) para poder medir la calidad, planificar pruebas según el riesgo, controlar el retrabajo y alimentar la mejora continua. Eso exige un proceso (ISO/IEC 29110, TMMi) y herramientas que lo sostengan (pruebas funcionales, de regresión e integración continua). Las métricas de defectos solo son útiles si se definen y se aplican con criterios comunes, es decir, **con estándares**. Esa es la pregunta que se discute en el foro.

## 🗂️ Orientación para la clase

| # | Bloque | Qué orientar en clase |
|:-:|:--|:--|
| 1 | Por qué importa la calidad y enlace con la Semana 2 | Las aplicaciones son cada vez más críticas para las organizaciones, pero en la región hay poca cultura de pruebas formales: la mayoría de las PYMEs y de las entidades muy pequeñas (EMPs) no tiene procesos estructurados. La falta de pruebas sistemáticas afecta tiempo, confiabilidad, usabilidad y costo. Las revisiones y auditorías de la Semana 2 producen hallazgos que ahora hay que caracterizar. |
| 2 | Modelos y estándares de prueba | Comparar TMM, TMMi, TPI, TMAP e ISO/IEC 29110 (ver tabla más abajo). Idea clave: los modelos de madurez dicen **qué** mejorar, pero no **cómo** llegar a hacerlo; por eso Escobar-Sánchez y Fuertes-Díaz proponen un modelo formal de pruebas funcionales. |
| 3 | **ISO/IEC 29110** | Serie de estándares para EMPs de hasta 25 personas. Perfil básico con dos procesos: Gestión del Proyecto (GP) e Implementación del Software (IS). Define **qué** hacer, no **cómo**; es adaptable a cualquier ciclo de vida (Scrum, cascada, TSP…) y permite certificación incremental. |
| 4 | **TMMi** | Modelo de madurez del proceso de pruebas, complementario a CMMI (visto en la Semana 2). Cinco niveles; el **nivel 2** es el punto de partida para formalizar las pruebas y se alinea con ISO/IEC 29110. |
| 5 | **Defecto y su caracterización** | Qué es un defecto y por qué caracterizarlo: permite planificar pruebas basadas en riesgo, reduce retrabajo y costos, aumenta la confiabilidad y alimenta la mejora continua. |
| 6 | Clasificación de defectos | Por **severidad**, por **origen** y por **tipo** (taxonomía del modelo TMMi nivel 2). Ver tablas más abajo. |
| 7 | **Métricas de defectos** | Densidad, tasa de detección, tasa de corrección, reincidencia y distribución por severidad. |
| 8 | **Ciclo de vida de un defecto** y flujo de defectos en el aseguramiento de la calidad | Recorrido de nueve fases, desde que el defecto se introduce hasta que se cierra con lecciones aprendidas. |
| 9 | **Integración continua (IC)** | Compilar y validar automáticamente cada cambio y avisar de inmediato las fallas. Detecta defectos temprano, evita regresiones y mantiene estable la rama principal (*main line*). |
| 10 | Caso de estudio: pruebas funcionales en una PYME | Sistema modular de administración educativa; 20 de 40 funcionalidades; dos ciclos de prueba más regresión; 100 incidentes. |
| 11 | Ejercicios prácticos *(propuesta)* | Clasificar y priorizar defectos; calcular métricas y proponer un plan de acción; argumentar sobre la práctica vital de ISO/IEC 29110. Las respuestas están más abajo. |

## 📊 Modelos y estándares de prueba de software

| Modelo | Publicación | Niveles | Gestión de riesgos | Aplicabilidad a EMPs |
|:--|:-:|:-:|:-:|:--|
| TMM | 1996 | 5 niveles | ✔ | Complejo para PYMEs |
| TMMi | 2008 | 5 niveles | ✔ | Requiere adaptación |
| TPI | 1998 | N/A | ✔ | Solo mejora, no estructura |
| TMAP | 1995 | N/A | ✔ | Muy extenso para EMPs |
| ISO/IEC 29110 | 2011 | Perfil básico | ✔ | Diseñado para EMPs |

*Fuente: Escobar-Sánchez y Fuertes-Díaz (2015); Muñoz et al. (2019). La presentación menciona también ISO/IEC 9126, que en la Semana 2 se reemplazó por ISO/IEC 25010; conviene aclararlo en clase.*

### Los cinco niveles de TMMi

| Nivel | Nombre | Qué lo caracteriza | Áreas de proceso (figura de la presentación) |
|:-:|:--|:--|:--|
| 1 | Inicial | Pruebas caóticas, sin proceso definido ni distinción entre pruebas y depuración. | — |
| 2 | Gestionado | Política de pruebas, planificación, seguimiento y diseño basado en riesgo. | Política y estrategia de pruebas; planificación de pruebas; monitorización y control de pruebas; diseño y ejecución de pruebas; entorno de pruebas. |
| 3 | Definido | Proceso estándar de pruebas integrado en el ciclo de vida del software. | Organización de pruebas; programa de formación de pruebas; ciclo de vida de pruebas e integración; pruebas no funcionales; revisiones entre pares. |
| 4 | Medido | Métricas cuantitativas para evaluar la calidad y la efectividad de las pruebas. | Mediciones de pruebas; evaluación de la calidad del producto; revisiones entre pares avanzadas. |
| 5 | Optimizado | Mejora continua, prevención de defectos y automatización avanzada. | Prevención de defectos; control de calidad; optimización del proceso de pruebas. |

*En la figura de la presentación el nivel 4 aparece como "Gestión y Medición"; el texto de la diapositiva lo llama "Medido".*

### Modelo formal de pruebas funcionales (Escobar-Sánchez y Fuertes-Díaz, 2015)

Modelo independiente del proceso de desarrollo, basado en el **ciclo de prueba** y compuesto por **cuatro fases**: Especificación, Planificación, Ejecución y Evaluación. Sus casos de prueba se generan con técnicas de caja negra (partición de equivalencia y valor límite) y una matriz relaciona funcionalidades con casos. Se aplicó a una PYME y mostró su eficiencia, pero también que hace falta desarrollar una **cultura de calidad organizacional**.

Flujo del modelo según el diagrama de la presentación (diapositiva 20):

| Fase | Pasos |
|:--|:--|
| 1. Especificación | Necesidad del cliente → revisión de requerimientos → ¿funcionalidades aceptadas por los clientes? (si no, se vuelve a revisar) → análisis de riesgos → ¿funcionalidades priorizadas? |
| 2. Planificación | Definición de los ciclos de prueba → planificación de la prueba. |
| 3. Ejecución | Diseño de la prueba → configuración del entorno de pruebas → ejecución del ciclo de prueba, con seguimiento y control → ¿se realizaron todos los ciclos? (si no, se repite). |
| 4. Evaluación (resultados) | Evaluación del proceso de pruebas → fin. |

## 🏷️ ISO/IEC 29110 en detalle

| Proceso del perfil básico | Actividades |
|:--|:--|
| **Gestión del Proyecto (GP)** | Planificación, seguimiento, control (incluido el control de cambios) y cierre del proyecto dentro de calidad, tiempo y costo. |
| **Implementación del Software (IS)** | Análisis de requisitos, diseño, construcción, integración, pruebas y entrega. |

**Ventajas de implementarlo** (según la presentación):

- *Para la organización:* mejor gestión de proyectos y control de costos; más competitividad; acceso a licitaciones que exigen certificación; camino hacia ISO 9001 o CMMI.
- *Para el proceso:* menos retrabajo gracias a la verificación y validación; documentación y trazabilidad estandarizadas; detección y caracterización sistemática de defectos.
- *Para el producto:* mayor confiabilidad, menor densidad de defectos y más satisfacción del cliente.

**Seis buenas prácticas destacadas**

| # | Práctica | Qué se espera |
|:-:|:--|:--|
| 1 | Verificación y validación | Confirmar que el software cumple requisitos y expectativas del cliente en cada entrega. |
| 2 | Casos y procedimientos de prueba | Diseñar, documentar y ejecutar pruebas sistemáticas antes de cada entrega. |
| 3 | Registro de trazabilidad | Vincular requisito → diseño → código → prueba para rastrear cambios e impactos. |
| 4 | Control de versiones | Documentar la estrategia de control de versiones y del repositorio. |
| 5 | Gestión de cambios | Evaluar el impacto técnico, en tiempo y en costo de cada solicitud antes de aceptarla. |
| 6 | Reuniones con el cliente | Conducir reuniones formales, registrar acuerdos y seguirlos hasta su cierre. |

### Debilidades de las EMPs al implementarlo (Muñoz, Peralta y Laporte, 2019)

Estudio de práctica en **13 EMPs del Estado de Zacatecas, México** (se consideró debilidad la que aparece en al menos 9 EMPs). Resultados que conviene citar en clase y en el foro:

| EMPs afectadas (de 13) | Debilidad |
|:-:|:--|
| 13 | No corregir los defectos encontrados hasta que la prueba unitaria se pase con éxito. |
| 12 | No realizar actividades de **verificación y validación**. |
| 12 | No desarrollar ni documentar **casos y procedimientos de prueba**. |
| 12 | No llevar **registros de trazabilidad**. |
| 11 | No documentar la versión preliminar del manual de usuario. |
| 10 | No documentar la estrategia de control de versiones, no respaldar el repositorio, no conducir reuniones con el cliente con registro de acuerdos, no evaluar el avance frente al plan. |
| 9 | No realizar solicitudes de cambio, no describir producto, alcance, objetivos y entregables en el plan, no establecer el entorno de desarrollo, no desarrollar pruebas unitarias. |

Conclusión del artículo: las EMPs deben fortalecer sobre todo las prácticas de aseguramiento de la calidad (verificación y validación), los casos de prueba (unitarios y de integración), los registros de trazabilidad, las solicitudes de cambio y los informes de seguimiento.

### Ruta mínima viable de V&V para una EMP

| Paso | Qué hacer |
|:-:|:--|
| 1. Planificar | Definir qué funcionalidades se prueban, quién prueba y cuándo (plan de pruebas de una página). |
| 2. Diseñar casos | Para cada funcionalidad crítica: entrada → acción → resultado esperado (la presentación propone mínimo 3 casos por módulo). |
| 3. Ejecutar | El tester ejecuta los casos y registra incidentes con tipo, severidad y evidencia (captura o registro). |
| 4. Corregir y re-probar | El desarrollador corrige; el tester verifica la corrección y ejecuta prueba de regresión. |
| 5. Cerrar y registrar | Informe final con métricas (densidad, tasa de detección) y lecciones aprendidas para el siguiente ciclo. |

*Herramientas mínimas: hoja de cálculo de casos, repositorio git y lista de chequeo de cierre.*

## 🐞 Caracterización de defectos

### Clasificación por severidad

| Severidad | Descripción |
|:--|:--|
| **Crítico** | Detiene el sistema o afecta funciones esenciales. |
| **Alto** | Afecta funcionalidades principales sin detener el sistema. |
| **Medio** | Afecta funciones secundarias. |
| **Bajo** | Problemas cosméticos o de presentación. |

### Clasificación por origen

| Origen | Ejemplos |
|:--|:--|
| Requisitos | Ambigüedad, omisiones, contradicciones. |
| Diseño | Arquitectura incorrecta, flujos mal definidos. |
| Codificación | Errores sintácticos, lógica incorrecta. |
| Integración | Reprocesos por cambios concurrentes, fallos en despliegues. |
| Pruebas | Casos mal diseñados, cobertura insuficiente. |

### Clasificación por tipo (taxonomía del modelo TMMi nivel 2)

| Tipo | Qué es | Ejemplos |
|:--|:--|:--|
| **Funcionalidad incorrecta** | El módulo no implementa la especificación acordada con el cliente. | Lógica mal implementada, reglas de negocio incompletas, cálculos erróneos. |
| **Interfaz de usuario** | Defectos en la interfaz. | Mensajes confusos, campos incorrectos, flujos no intuitivos, controles mal ubicados, inconsistencias visuales, problemas de usabilidad. |
| **Mensajes erróneos o faltantes** | Mensajes de error o informativos ausentes, incorrectos o inapropiados. | Falta de validaciones, mensajes ambiguos, ausencia de retroalimentación al usuario. |
| **Regresión** | Cambios en el código que generan fallos nuevos en funcionalidades previas. | Una corrección rompe algo que antes funcionaba. |

### Aclaración: severidad no es lo mismo que prioridad

La **severidad** mide qué tan grave es el efecto técnico del defecto. La **prioridad** indica en qué orden se corrige, y combina la severidad con el **impacto en el negocio** (cuántos usuarios afecta, si hay alternativa, si hay plazo contractual). Por eso en el Ejercicio 1 el orden de corrección no es solo el orden de severidad. Al clasificar un defecto, pregúntese primero *"¿qué tan grave es?"* y después *"¿qué tan pronto conviene corregirlo?"*.

### Error, defecto y fallo

La diapositiva 7 distingue tres conceptos:

| Concepto | Definición |
|:--|:--|
| **Error** | Acción humana que produce un resultado incorrecto. |
| **Defecto** | Desperfecto en un componente que puede causar que este falle en sus funciones. |
| **Fallo** | Manifestación visible de un defecto. |

Es decir, el error de una persona deja un defecto en un artefacto (requisito, diseño o código) y ese defecto se hace visible como fallo cuando el software se ejecuta. *(Propuesta)* **Incidente** es el reporte de un comportamiento anómalo, que luego se analiza para confirmar si hay un defecto.

## 📏 Métricas asociadas a defectos

| Métrica | Fórmula o forma de medición | Para qué sirve |
|:--|:--|:--|
| **Densidad de defectos** | Defectos / KLOC o defectos / funcionalidad | Comparar la calidad entre módulos o versiones. |
| **Tasa de detección** | Defectos encontrados por ciclo de prueba (o por caso ejecutado, como en el Ejercicio 2) | Evaluar la efectividad de las pruebas. |
| **Tasa de corrección** | Tiempo promedio para resolver un defecto | Medir la capacidad de respuesta del equipo. |
| **Reincidencia** | % de defectos reabiertos | Detectar correcciones deficientes y regresiones. |
| **Distribución por severidad** | Cantidad (o %) de defectos por nivel | Priorizar los esfuerzos de mejora. |

*La presentación rotula estas métricas como "(ISO/IEC 29110)", pero el estándar define **qué** procesos y registros se exigen, no un catálogo de métricas. Las métricas que aquí se usan provienen de los indicadores del modelo de Escobar-Sánchez y Fuertes-Díaz (incidentes por funcionalidad, por caso ejecutado y casos por funcionalidad). Conviene aclararlo en clase.*

### Cómo usa ISO/IEC 29110 la caracterización de defectos

El estándar exige gestión disciplinada de verificación y validación, registro y análisis de no conformidades, control de cambios y correcciones, y retroalimentación para la mejora continua. La caracterización de defectos es el insumo principal para cumplir esos requisitos.

## 🔄 Ciclo de vida de un defecto y flujo de calidad

![Ciclo de vida de un defecto de software](Ciclo%20de%20vida%20de%20un%20defecto%20de%20software.png)

| # | Fase | Qué ocurre |
|:-:|:--|:--|
| 1 | Introducción del defecto | Se introduce en requisitos, diseño o codificación. |
| 2 | Detección | Mediante pruebas funcionales, integración continua o pruebas de regresión. |
| 3 | Registro | Evidencia, pasos para reproducir, severidad y prioridad. |
| 4 | Clasificación | Tipo (interfaz, lógica, mensajes), origen e impacto. |
| 5 | Asignación | Se asigna a un equipo de desarrollo y a un responsable. |
| 6 | Corrección | Ajuste del código y validación local. |
| 7 | Reintegración continua | *Commit*, *build* automático, pruebas unitarias y funcionales. |
| 8 | Verificación de la fijación | QA valida la corrección y ejecuta pruebas de regresión. |
| 9 | Cierre del defecto | Documentación y lecciones aprendidas. |

![Flujo de defectos en el proceso de aseguramiento de la calidad](Flujo%20de%20Defectos%20en%20el%20Proceso%20de%20Aseguramiento%20de%20la%20Calidad.png)

El flujo de defectos recorre: requisitos → diseño → codificación → **integración continua** (compilación automática, pruebas unitarias y validación de cambios) → **pruebas funcionales** (caja negra y regresión) → detección de defectos (incidentes reportados) → clasificación (severidad, tipo, origen) → corrección → reintegración continua (nuevo *build* y pruebas) → cierre del defecto.

### Integración continua y defectos

Según la monografía de González y Lozano (2020), la IC consiste en prácticas y herramientas que compilan y prueban la aplicación automáticamente con frecuencia, y notifican de inmediato las fallas. Propone que cada desarrollador integre su trabajo al menos una vez al día, con un servidor de integración (el caso de estudio usó Jenkins con SVN). Si las pruebas fallan, se vuelve a la última versión funcional y se avisa a los desarrolladores.

Beneficios: detecta defectos temprano, evita regresiones, mantiene estable la *main line*, automatiza las pruebas unitarias y de integración y reduce los defectos por integración tardía. La diapositiva 15 resume las ventajas en cuatro puntos: resolución temprana de defectos, identificación de problemas de integración entre componentes, mayor exhaustividad que las pruebas unitarias y mayor cobertura de las pruebas. La misma monografía advierte que, sin estándares de calidad definidos por la empresa ni inspecciones continuas del código, los equipos enfrentan reprocesos en los **mantenimientos adaptativos, evolutivos o perfectivos**. Esa relación es útil para la pregunta del foro.

## 🧪 Caso de estudio: pruebas funcionales en una PYME

Sistema modular de administración educativa. El alcance acordado con el cliente fue de **20 funcionalidades de las 40** especificadas al inicio, priorizadas por prioridad, complejidad y criticidad. Se hicieron dos ciclos de prueba de 4 semanas cada uno, más una semana de evaluación con pruebas de regresión.

| Grupo | Prioridad | Complejidad | Criticidad | Funcionalidades | Ejemplos |
|:-:|:-:|:-:|:-:|:-:|:--|
| 1 | Alta | Alta | Alta | 5 | Autenticación multifactor (MFA) para administradores; pagos electrónicos con validación bancaria; facturación electrónica DIAN; inventario en tiempo real; motor de reglas de negocio. |
| 2 | Alta | Alta | Media | 5 | Dashboard de KPI; integración vía API REST; roles y permisos personalizados; programación de tareas; auditoría de actividades del usuario. |
| 3 | Alta | Media | Media | 5 | Gestión de usuarios; búsqueda avanzada; exportación a PDF y Excel; notificaciones por correo; historial de cambios por registro. |
| 4 | Media | Media | Media | 5 | Personalización del perfil; preferencias del sistema; categorías o etiquetas; estadísticas básicas; adjuntar archivos. |

*Los ejemplos de funcionalidades están en la presentación; el artículo solo da los grupos y sus cantidades. La tabla de la diapositiva 16 (tomada del artículo) muestra "Alta, Alta, Alta" en las dos primeras filas, mientras que la diapositiva 17 describe el grupo 2 con criticidad **media**. Aquí se usó la de la diapositiva 17, que coincide con su descripción ("no detienen el sistema si fallan"); confirmar cuál es la correcta.*

| Ciclo | Incidentes |
|:--|:-:|
| Ciclo 1 | 59 |
| Ciclo 2 | 21 |
| Regresión | 20 |
| **Total** | **100** |

Interpretación didáctica: la reducción progresiva evidencia madurez del proceso; la regresión confirma la importancia de automatizar pruebas; la mayoría de los incidentes eran de mensajes e interfaz, no de lógica crítica. El artículo señala que son incidentes de baja importancia que se reducen de forma significativa en la segunda versión, y que el segundo ciclo tuvo un aumento relativo de incidentes porque el producto sufrió alteraciones importantes en su funcionalidad. Los resultados mostraron satisfacción del cliente, medida con una encuesta de 1 (malo) a 5 (excelente).

## ✍️ Ejercicios prácticos *(propuesta; vienen de la presentación)*

### Ejercicio 1. Clasificar y priorizar defectos

**Escenario.** Una EMP de 4 personas desarrolla un sistema de facturación. En el Ciclo 1 se detectaron seis incidentes: (A) el botón "Guardar" no responde; (B) el logo aparece pixelado en pantallas HD; (C) el cálculo del IVA es incorrecto cuando hay descuentos; (D) no aparece el mensaje de error al ingresar un NIT inválido; (E) el menú de navegación se desordena en móvil; (F) el sistema no guarda facturas con más de 50 ítems.

**Qué hacer.** Clasificar cada incidente por tipo, severidad y origen probable, y ordenarlos por prioridad de corrección justificando el criterio. **Entregable:** tabla con Incidente | Tipo | Severidad | Origen | Prioridad | Justificación.

| Incidente | Tipo | Severidad | Origen | Prioridad y razón |
|:--|:--|:--|:--|:--|
| (A) Botón no responde | Implementación | Crítico | Codificación | N.º 1. Bloquea guardar la factura. |
| (F) Falla con más de 50 ítems | Implementación | Crítico | Requisitos | N.º 2. Impide el uso en casos reales. |
| (C) IVA incorrecto con descuentos | Implementación | Alto | Codificación | N.º 3. Error de negocio grave. |
| (D) Sin mensaje por NIT inválido | Mensaje | Alto | Diseño | N.º 4. Afecta la validación del usuario. |
| (E) Menú desordenado en móvil | Interfaz | Medio | Diseño | N.º 5. Usabilidad afectada. |
| (B) Logo pixelado | Interfaz | Bajo | Diseño | N.º 6. Solo cosmético. |

*Clave didáctica: la prioridad combina severidad e impacto en el negocio, no solo el nivel técnico.*

*Observaciones para la retroalimentación (propuesta; confirmar con el docente):* la presentación llama "implementación" al tipo que su taxonomía nombra "funcionalidad incorrecta". Algunos orígenes admiten otra respuesta si se argumenta bien: el mensaje que falta en (D) podría ser de requisitos o de codificación, y la falla de (F) también podría ser de diseño. Conviene valorar la justificación más que coincidir con la tabla.

### Ejercicio 2. Calcular métricas y proponer un plan de acción

**Escenario.** La misma EMP cerró el Ciclo 2 con 8 funcionalidades probadas, 51 casos ejecutados y 21 incidentes (3 críticos, 4 altos, 10 medios y 4 bajos). El Ciclo 1 tuvo 20 funcionalidades, 134 casos y 59 incidentes.

**Qué hacer.** Calcular densidad de defectos y tasa de detección por ciclo, analizar la tendencia y redactar un plan de acción de tres medidas para reducir los defectos críticos y altos en el Ciclo 3. **Entregable:** hoja de cálculo con métricas, párrafo de análisis y plan de acción (máximo 15 líneas).

| Métrica | Ciclo 1 | Ciclo 2 | Tendencia |
|:--|:-:|:-:|:--|
| Funcionalidades | 20 | 8 | — |
| Casos ejecutados | 134 | 51 | — |
| Incidentes | 59 | 21 | ↓ 64 % |
| Densidad (defectos / funcionalidad) | 2,95 | 2,63 | ↓ Mejora |
| Tasa de detección (defectos / caso) | 0,44 | 0,41 | ↓ Mejora |

Plan de acción sugerido para el Ciclo 3:

1. Revisión de código (*code review*) antes de ejecutar pruebas, enfocada en la lógica de negocio.
2. Automatizar pruebas de regresión con los casos críticos de los Ciclos 1 y 2 para detectar recurrencias.
3. Aplicar partición de equivalencia en las validaciones de entrada para reducir los mensajes erróneos.

*Los cálculos coinciden (59/20 = 2,95; 21/8 = 2,63; 59/134 = 0,44; 21/51 = 0,41; 3 + 4 + 10 + 4 = 21). Al interpretar, conviene que el estudiante note que el Ciclo 2 probó menos funcionalidades (8 frente a 20), así que la caída de 64 % en incidentes no se debe leer solo como mejora del proceso. Además, en el Ciclo 2 siguen apareciendo 3 críticos y 4 altos (33 % del total), lo que justifica el plan de acción. Es una lectura adicional a la de la presentación.*

### Ejercicio 3. Pregunta de reflexión sobre ISO/IEC 29110

> *"El estándar ISO/IEC 29110 presenta un conjunto de buenas prácticas que buscan reforzar los procesos en la gestión de proyectos y el desarrollo de software. ¿Cuál de ellas considera vital y por qué se debería implementar en cualquier empresa de desarrollo de software?"*

**Estructura sugerida:** (1) identificar la práctica con el nombre exacto del estándar y su proceso; (2) argumentar con evidencia del caso (métricas, debilidades en las 13 EMPs); (3) generalizar su valor sin importar el tamaño o sector; (4) proponer al menos 2 acciones concretas con recursos mínimos. **Entregable:** argumento escrito de máximo 300 palabras o exposición oral de 3 minutos, citando al menos una métrica del caso.

| Criterio (5 pts cada uno) | Excelente (5) | Aceptable (3) | Insuficiente (1) |
|:--|:--|:--|:--|
| **Identificación** | Nombra la práctica con la terminología exacta del estándar y el proceso al que pertenece. | Nombra la práctica sin precisar el proceso. | Menciona una práctica genérica sin relación clara con el estándar. |
| **Argumentación** | Sustenta con datos cuantitativos del caso (métricas, % de EMPs afectadas). | Argumenta cualitativamente, sin cifras. | Solo opina, sin evidencia ni referencia. |
| **Generalización** | Explica la aplicabilidad en distintos contextos (tamaño, sector, metodología). | Dice que aplica en general, sin desarrollarlo. | Limita la práctica a un contexto específico. |
| **Plan de acción** | Propone 2 o más acciones específicas, realizables y coherentes con una EMP. | Propone 1 acción concreta. | No propone acciones o son demasiado genéricas. |

*Total: 20 puntos. Calificación mínima aprobatoria: 12/20.*

## 📝 Actividad evaluable de la semana: foro de discusión

**Foro de discusión. Métricas de calidad: de la teoría a la práctica en proyectos de software** (código EDSTV011_F3). Es una actividad **colaborativa**: 5 horas para desarrollarla y 2 horas para consultar los materiales. Contribuye al resultado de aprendizaje: *especifica la utilización de técnicas de gestión de la calidad, estándares y metodologías en el diseño y la medición de la calidad del software.*

**Pregunta orientadora**

> ¿Cómo influye la correcta definición y aplicación de métricas de calidad en el mantenimiento y evolución del *software*, y qué riesgos surgen si se implementan de manera inadecuada sin contemplar el uso de estándares?

**Cómo participar**

1. Ingrese a la plataforma y lea con atención la pregunta con la que el profesor abrió el foro.
2. **Intervención 1:** redacte un texto que responda la pregunta, con suficientes argumentos. Dé clic en **Responder**, escriba el título en **Asunto**, redacte en **Mensaje** y dé clic en **Enviar al foro**.
3. **Intervención 2:** seleccione como mínimo **dos** intervenciones de compañeros y a cada una dé una **réplica argumentada** a partir de los recursos revisados.
4. Tome en cuenta lo revisado en la semana y su experiencia al desarrollar la actividad. Su contribución debe ser **respetuosa**, **bien fundamentada** y de **al menos 10 líneas**.

**Recursos básicos**

- Escobar-Sánchez, M., & Fuertes-Díaz, W. (2015). Modelo formal de pruebas funcionales de software para alcanzar el nivel de madurez integrado 2. *Revista Facultad de Ingeniería*, 24(39), 31-42.
- Muñoz, M., Peralta, M., & Laporte, C. Y. (2019). Análisis de las debilidades que presentan las entidades muy pequeñas al implementar el estándar ISO/IEC 29110: Una comparativa entre estado del arte y el estado de la práctica. *Revista Ibérica de Sistemas e Tecnologias de Informação*.
- Hernández, G., Martínez, Á., Jiménez, R., & Jiménez, F. (2020). Cómo los profesionales perciben la relevancia de las métricas de productividad para un equipo ágil de desarrollo de software. *Revista Ibérica de Sistemas e Tecnologias de Informação*, 596-609.

**Recurso complementario**

- González-Sánchez, J., Montero-Simarro, F., & Gutiérrez-Vela, F. (2012). Evolución del concepto de usabilidad como indicador de calidad del software. *El Profesional de la Información*, 21(5), 529-536.

*La carpeta `Semana_3_Articulos` contiene los dos primeros recursos básicos y, además, la monografía de González y Lozano (2020) sobre integración continua. Faltan en la carpeta el artículo de Hernández et al. (2020) y el recurso complementario; por eso este documento no resume sus contenidos. Conviene agregarlos para completar la guía del foro.*

### Rúbrica (total: 5.0 puntos)

| Criterio | Insuficiente | Regular | Bueno | Excelente |
|:--|:--|:--|:--|:--|
| **Pertinencia de las participaciones** | 0.8 — No evidencia dominio del tema, no genera debate ni retoma información para enriquecer el diálogo | 1.2 — Dominio superficial; genera debate con información irrelevante y endeble | 1.6 — Evidencia dominio; genera debate con información complementaria | **2.0** — Profundo dominio; genera debate con información relevante y consistente |
| **Capacidad de análisis en el debate con sus compañeros** | 0.3 — No analiza las intervenciones ni plantea debate | 0.5 — Analiza de forma ambigua e imprecisa; solo retoma los argumentos de sus pares | 0.7 — Analiza con claridad y mínimas imprecisiones; controvierte los argumentos | **1.0** — Analiza con claridad y precisión; controvierte críticamente los argumentos |
| **Abordaje de preguntas** | 0.8 — No responde la pregunta; ideas que no corresponden al tema | 1.2 — Responde de forma superficial; ideas sin relación directa con el tema | 1.6 — Responde de manera general; ideas que corresponden al tema | **2.0** — Responde con claridad y precisión; ideas totalmente alineadas con el tema |

*Quien no participa obtiene 0 en todos los criterios (nivel "No evaluable"). Los encabezados del PDF (1.9, 2.9, 3.9 y 5) no coinciden con los puntajes de cada fila (que suman 5.0); aquí se usan los puntajes de las filas. Confirmar con el docente.*

### Ideas para fundamentar la Intervención 1 *(propuesta)*

La pregunta tiene dos partes. Una intervención sólida responde ambas y se apoya en los recursos.

**1. Cómo influyen las métricas bien definidas en el mantenimiento y la evolución**

- Las métricas de defectos (densidad, tasa de detección, reincidencia, distribución por severidad) convierten el registro de incidentes en información para **decidir**: qué módulos refactorizar, dónde reforzar pruebas, cuándo liberar. Ver la caracterización de defectos arriba.
- La **regresión** es el riesgo típico de la evolución: en el caso de estudio hubo 20 incidentes de regresión sobre 100. Medirla y automatizar las pruebas de regresión protege cada cambio posterior.
- La **reincidencia** (% de defectos reabiertos) y la tasa de corrección muestran si el mantenimiento realmente resuelve las causas.
- La **integración continua** aplica las métricas en cada cambio: detecta defectos temprano, evita regresiones y mantiene estable la rama principal.
- La **trazabilidad** (requisito → diseño → código → prueba, práctica de ISO/IEC 29110) permite medir el impacto de un cambio antes de aceptarlo. En el estudio de Muñoz et al., 12 de 13 EMPs no la llevaban.
- Medir el **origen** de los defectos (requisitos, diseño, codificación, integración, pruebas) orienta la mejora hacia el proceso y no solo hacia el parche.

**2. Riesgos de implementarlas mal o sin estándares**

- **Métricas inconsistentes o no comparables:** sin definiciones comunes (qué es un defecto, cómo se mide la severidad, qué se cuenta como KLOC o como funcionalidad), los números cambian de un equipo o ciclo a otro y no sirven para comparar. Ejemplo del Ejercicio 2: el alcance de cada ciclo distinto altera la lectura de la densidad.
- **Mantenimiento sin criterio:** la monografía de IC señala reprocesos en mantenimientos adaptativos, evolutivos y perfectivos cuando no hay estándares de calidad definidos ni inspección continua del código.
- **Decisiones basadas en datos erróneos o incompletos:** priorizar por la métrica equivocada o por severidad sin considerar el impacto en el negocio.
- **Métricas sin proceso ni cultura de calidad:** los modelos dicen *qué* mejorar, pero no *cómo*, y Escobar-Sánchez y Fuertes-Díaz concluyen que hace falta desarrollar una cultura de calidad organizacional.
- **Complejidad desproporcionada:** adoptar un modelo completo (TMM, TMAP) en una EMP es inviable; por eso ISO/IEC 29110 está diseñado para entidades pequeñas y no exige más de lo razonable.
- **Perder el acceso a oportunidades:** sin un referente reconocido es más difícil acceder a licitaciones o avanzar hacia ISO 9001 o CMMI.
- **Efecto perverso de las métricas:** cuando la métrica se vuelve la meta (por ejemplo, ocultar defectos para bajar la densidad), deja de medir la calidad. *(Reflexión general, no proviene de los recursos; conviene respaldarla con el artículo de métricas de productividad de Hernández et al. una vez disponible.)*

### Guía para la Intervención 2 (réplicas) *(propuesta)*

Una réplica con nivel "excelente" **controvierte con argumentos**, no solo resume. Pautas:

1. Resuma en una línea el argumento del compañero y diga si lo comparte, lo matiza o discrepa.
2. Agregue un dato o una fuente que el compañero no usó (por ejemplo, una cifra de las 13 EMPs o del caso de 100 incidentes).
3. Plantee un contraejemplo, una limitación o una pregunta que haga avanzar el debate (por ejemplo: *"¿qué pasa si la métrica se mide sin un criterio común de severidad?"*).
4. Mantenga un tono respetuoso y escriba al menos 10 líneas.

## 💬 Preguntas para detonar la discusión

1. ¿Por qué un equipo pequeño que "no tiene tiempo para medir" corre más riesgo que uno que mide poco pero con criterio?
2. Si la densidad de defectos baja de un ciclo a otro, ¿en qué casos esa mejora podría ser engañosa? (Pista: Ejercicio 2.)
3. ¿Qué diferencia hay entre la severidad y la prioridad de un defecto? Den un ejemplo donde no coincidan.
4. ¿Qué defectos de regresión podría evitar la integración continua y cuáles no?
5. ISO/IEC 29110 define *qué* hacer y no *cómo*. ¿Es una ventaja o una limitación para medir la calidad?

## ✍️ Actividad sugerida en clase *(propuesta)*

Como práctica previa al foro, con un proyecto conocido por el grupo:

1. Registrar **cinco defectos** reales o simulados y caracterizarlos (tipo, severidad, origen).
2. Calcular **dos métricas** (por ejemplo, densidad y distribución por severidad).
3. Decidir cuál de las seis buenas prácticas de ISO/IEC 29110 aplicaría primero y justificarlo.

## 🔑 Glosario rápido

- **Defecto:** desviación entre el comportamiento esperado y el comportamiento real del software.
- **Incidente:** reporte de un comportamiento anómalo detectado en una prueba o en uso.
- **Caracterización de defectos:** clasificación de los defectos por tipo, severidad y origen para medir y mejorar la calidad.
- **Severidad:** gravedad técnica del defecto (crítico, alto, medio, bajo).
- **Prioridad:** orden de corrección, que combina severidad e impacto en el negocio.
- **Regresión:** fallo nuevo en una funcionalidad previa causado por un cambio en el código.
- **Prueba funcional:** prueba de caja negra que contrasta el comportamiento del software con la especificación.
- **Densidad de defectos:** defectos por KLOC o por funcionalidad.
- **Entidad Muy Pequeña (EMP o VSE):** organización o proyecto de hasta 25 personas dedicadas al desarrollo de software.
- **ISO/IEC 29110:** serie de estándares de ingeniería de software para EMPs; su perfil básico tiene los procesos de Gestión del Proyecto e Implementación del Software.
- **TMMi:** modelo de madurez de pruebas de software, de cinco niveles; complementa a CMMI.
- **Trazabilidad:** vínculo requisito → diseño → código → prueba que permite rastrear cambios e impactos.
- **Integración continua (IC):** práctica de compilar y validar automáticamente cada cambio al código, con notificación inmediata de las fallas.
- **Rama principal (*main line*):** línea de código estable que se integra y se libera.

## 📚 Fuentes de la semana

- Escobar-Sánchez, M., & Fuertes-Díaz, W. (2015). Modelo formal de pruebas funcionales de software para alcanzar el nivel de madurez integrado 2. *Revista Facultad de Ingeniería*, 24(39), 31-42.
- Muñoz, M., Peralta, M., & Laporte, C. Y. (2019). Análisis de las debilidades que presentan las entidades muy pequeñas al implementar el estándar ISO/IEC 29110: Una comparativa entre estado del arte y el estado de la práctica. *Revista Ibérica de Sistemas e Tecnologias de Informação*, (34), 85-96.
- González Rodríguez, J. C. A., & Lozano Pinto, O. F. (2020). *Aseguramiento de la calidad del software mediante la implementación de integración continua* [Monografía de grado]. Universidad Piloto de Colombia, Seccional Alto Magdalena.
- Presentaciones de la semana: *Estándares y métricas de calidad* e *ISO/IEC 29110*.

*Algunas cifras de la presentación no aparecen en los artículos de la carpeta: "40-80 % del costo de desarrollo se destina a corregir defectos", "TMMi nivel 1 en la mayoría de las organizaciones de la región" y "corregir en pruebas cuesta hasta 10 veces menos que en producción". Si se citan en el foro, conviene buscar la fuente original. Además, la presentación dice que V&V fue "la debilidad más frecuente (12/13)": en el artículo, 12 de 13 EMPs la presentan, pero la más frecuente es no corregir defectos hasta pasar la prueba unitaria (13/13).*

## ➡️ Puente hacia la Semana 4

Muchos defectos nacen en los **requisitos** (ambigüedad, omisiones, contradicciones), y son los más caros de corregir. En el Ejercicio 1, el límite de 50 ítems por factura es un ejemplo. La Semana 4 trata de la **especificación de requisitos del software**: cómo escribir requisitos claros, verificables y trazables para evitar esos defectos desde el origen.
