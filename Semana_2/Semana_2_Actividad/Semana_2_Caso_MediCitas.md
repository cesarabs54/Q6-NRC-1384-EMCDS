# Semana 2 — Documento de apoyo: Caso MediCitas v3.2

**Curso:** Estándares y Métricas de Calidad en el Desarrollo de Software
**Actividad:** Reporte de solución de problemas matemáticos. Evaluación de la calidad del software mediante métricas, verificación y auditoría (EDSTV011_A2)

> Caso ficticio elaborado para el curso. La organización, los proveedores, los identificadores y las cifras son inventados; las normas citadas sí existen.

## Cómo usar este documento

Usted actúa como **especialista en aseguramiento de la calidad del software** y debe evaluar MediCitas v3.2 antes de su liberación a producción. Lea las secciones 1 y 2 (escenario y evidencias), complete las plantillas de las secciones 3, 4 y 5, y responda las preguntas de la sección 6. Después integre todo en su reporte, con los elementos que pide el PDF de la actividad.

Cite las evidencias por su código (por ejemplo, INC-101 o CR-202) y deje a la vista los pasos de cálculo de cada métrica.

---

## 1. Descripción general del sistema y contexto

**MediCitas** es el sistema de gestión de citas e historias clínicas de **IPS Salud Especial**, una red de 12 clínicas ambulatorias en Bogotá y municipios cercanos. La versión **3.2** está en preparación e incluye dos novedades: un **módulo de telemedicina** (videoconsulta) y el **rediseño de la autenticación con inicio de sesión único (SSO)**.

### Contexto organizacional

- Equipo Scrum de 8 personas: 1 Product Owner, 1 Scrum Master, 4 desarrolladores y 2 personas que dedican parte de su tiempo a pruebas. **No hay un área de QA independiente.**
- La liberación está fijada por contrato **dentro de 3 semanas**, con el alcance de la v3.2 ya **congelado** (*change freeze*).
- Hay presión comercial por lanzar telemedicina antes que una IPS competidora.
- Infraestructura híbrida: servidores propios para los datos clínicos y AWS para telemedicina.

### Actores involucrados

- Pacientes (app móvil y portal web), personal médico y personal administrativo.
- Administrador de TI / DBA y oficial de protección de datos.
- Equipo de desarrollo Scrum.
- Proveedores externos: la pasarela de pagos **PayGateCol** y la API de **WhatsApp Business**.

### Funcionalidades críticas

1. Autenticación y gestión de sesiones (incluye SSO).
2. Agendamiento y cancelación de citas médicas.
3. Consulta y edición de historias clínicas electrónicas (HCE).
4. Emisión de órdenes médicas y recetas electrónicas.
5. Facturación electrónica integrada con la DIAN.
6. Módulo de telemedicina (videoconsulta), en desarrollo.
7. Notificaciones y recordatorios por SMS y WhatsApp.
8. Reportes gerenciales e indicadores clínicos.

### Restricciones técnicas y regulatorias

- Ley 1581 de 2012 y Decreto 1377 de 2013: protección de datos personales.
- Resolución 1995 de 1999: custodia y seguridad de la historia clínica.
- Resoluciones 2654 de 2019 y 3100 de 2019: telesalud y habilitación de servicios, incluida telemedicina.
- PCI-DSS: datos de tarjetas en el módulo de pagos.
- Disponibilidad mínima de **99.5 %** en horario de atención (7 a. m. a 9 p. m.).
- Integración *batch* nocturna con el sistema legado AS/400 (facturación).
- Fecha de liberación y alcance congelados contractualmente.

---

## 2. Evidencias disponibles

### 2.1 Fragmentos de requisitos

| ID | Requisito | Estado según el equipo |
|:--|:--|:--|
| RF-014 | La autenticación debe ofrecer segundo factor (2FA), exigible para los roles críticos. | 2FA implementado, pero **opcional** para todos los roles. |
| RF-022 | Los datos clínicos deben almacenarse cifrados en reposo con AES-256. | Implementado; **sin verificación** de que todos los campos estén cifrados. |
| RF-031 | El agendamiento debe responder en 2 s o menos (percentil 95) con 100 usuarios concurrentes. | Sin prueba de carga. |
| RF-045 | Todo acceso de lectura y escritura a la HCE debe quedar registrado de forma inmutable. | Implementado parcialmente. |
| RF-052 | El módulo de pagos debe cumplir PCI-DSS. | Sin auditoría de cumplimiento. |
| RF-060 | El canal de videoconsulta debe viajar cifrado de extremo a extremo. | Implementado en pruebas; sin casos de prueba ejecutados. |
| CR-201 | El SSO debe funcionar para médicos, administrativos y pacientes, sin bloqueos. | En validación con usuarios piloto. |

### 2.2 Extracto de la bitácora de incidencias

| ID | Fecha | Incidente | Estado |
|:--|:--|:--|:--|
| INC-101 | 2026-05-12 | Un médico accedió a historias clínicas de pacientes que no tenía asignados al cambiar el número de ID en la URL. | Abierto |
| INC-102 | 2026-05-19 | La cuenta administrativa `admin_ti` la comparten 4 personas y sus contraseñas no expiran. | Abierto |
| INC-103 | 2026-05-27 | El canal de videoconsulta se transmitió sin cifrar. La configuración de pruebas pasó a producción (ver CR-202). | Abierto |
| INC-104 | 2026-06-03 | Los logs de la pasarela de pagos muestran el número completo de la tarjeta, sin enmascarar. | Abierto |
| INC-105 | 2026-06-10 | Auditoría interna: el sistema registra las escrituras en la historia clínica, pero no las lecturas (ver RF-045). | Abierto |
| INC-106 | 2026-06-17 | El *batch* nocturno de facturación hacia AS/400 falló 3 veces en 4 semanas y ninguna falla generó alerta. | Abierto |
| INC-107 | 2026-06-24 | Los reportes gerenciales tardan más de 30 s cuando se consulta un mes completo. | Abierto, prioridad baja |

### 2.3 Lista de control de cambios

| ID | Cambio | Despliegue | Revisión y aprobación registrada |
|:--|:--|:--|:--|
| CR-201 | Rediseño del SSO | Staging | Sí |
| CR-202 | Configuración del servidor de videoconferencia | **Producción** | **No** |
| CR-203 | Ajuste de plantillas de recordatorios por WhatsApp | Producción | Sí |
| CR-204 | Actualización del esquema de facturación DIAN | Producción | Sí |
| CR-205 | Parche en el módulo de recetas electrónicas | **Producción** | **No** |

### 2.4 Resultados de pruebas preliminares

| ID | Prueba | Estado | Resultado |
|:--|:--|:--|:--|
| PT-01 | Pruebas funcionales de agendamiento y cancelación de citas | Ejecutada | Aprobada. Sin pruebas de carga (ver RF-031). |
| PT-02 | Pruebas de integración de facturación electrónica con la DIAN | Ejecutada | Aprobada con observaciones menores. |
| PT-03 | Pentesting sobre la historia clínica electrónica | **No ejecutada** | Sin tiempo asignado en el sprint. |
| PT-04 | Prueba de carga del módulo de telemedicina | **No ejecutada** | Pendiente de entorno en AWS. |

Las cuatro son las **pruebas críticas** planificadas para la v3.2. No existen casos de prueba ejecutados para RF-031 ni para RF-060.

Sobre la **disponibilidad** (99.5 %): el equipo no tiene medición formal ni monitoreo continuo.

---

## 3. Matriz de verificación y validación (plantilla)

Complete las columnas **Tipo**, **Técnica y responsable** y **Criterio de aceptación**. La fila de ejemplo muestra el nivel de detalle esperado.

| N.º | Requisito o funcionalidad | Tipo (Verificación o Validación) | Técnica y responsable | Criterio de aceptación |
|:-:|:--|:--|:--|:--|
| Ej. | RF-014 — Autenticación 2FA | Verificación | Revisión de código e inspección de configuración — Líder técnico | 2FA disponible y exigible para los roles críticos |
| 1 | RF-022 — Cifrado de la HCE en reposo (AES-256) | | | |
| 2 | RF-031 — Rendimiento del agendamiento bajo carga | | | |
| 3 | RF-045 — Trazabilidad de accesos a la HCE | | | |
| 4 | RF-052 — Cumplimiento PCI-DSS en pagos | | | |
| 5 | RF-060 — Cifrado extremo a extremo del video | | | |
| 6 | CR-201 — Autenticación SSO | | | |
| 7 | Control de acceso por rol a la HCE (INC-101) | | | |
| 8 | Integración *batch* nocturna con AS/400 (INC-106) | | | |
| 9 | Módulo de telemedicina: experiencia de usuario | | | |

Pista: clasifique cada fila por **contra qué se compara** (especificación o necesidad del usuario), no por si se ejecuta el código.

---

## 4. Lista de control de revisión técnica (plantilla)

Marque cada ítem como **Sí**, **No** o **N. A.** (no hay evidencia en el escenario) y justifique con el código de la evidencia.

| N.º | Ítem de revisión | Cumple | Observaciones y evidencia |
|:-:|:--|:-:|:--|
| 1 | El código fuente cumple los estándares de codificación definidos por el equipo. | | |
| 2 | Existe trazabilidad entre los requisitos y los casos de prueba. | | |
| 3 | Todos los cambios fueron documentados y aprobados antes de su despliegue. | | |
| 4 | Los mecanismos de autenticación y autorización protegen los recursos críticos. | | |
| 5 | La información sensible se almacena y transmite cifrada. | | |
| 6 | Existen registros de auditoría para accesos y modificaciones a información crítica. | | |
| 7 | Se ejecutaron pruebas de seguridad (pentesting) antes de la liberación. | | |
| 8 | Se ejecutaron pruebas de carga y rendimiento sobre los módulos críticos. | | |
| 9 | El manejo de datos personales cumple la Ley 1581 de 2012. | | |
| 10 | El manejo de la historia clínica cumple la Resolución 1995 de 1999. | | |
| 11 | El módulo de telemedicina cumple la Resolución 2654 de 2019. | | |
| 12 | Existen alertas automáticas ante fallos de procesos críticos. | | |
| 13 | La documentación técnica y de usuario está actualizada para la versión a liberar. | | |
| 14 | Los riesgos técnicos y regulatorios identificados fueron mitigados antes de la liberación. | | |

La actividad exige **mínimo 10 ítems**. Puede conservar estos 14, ajustarlos o añadir otros que su análisis justifique.

---

## 5. Formato base de auditoría

### 5.1 Plan de auditoría

| Elemento | Contenido |
|:--|:--|
| Objetivo | |
| Alcance | |
| Criterios de auditoría (normas y estándares) | |
| Equipo auditor | |
| Fecha de ejecución | |
| Evidencias a recolectar | |

### 5.2 Hallazgos de auditoría

Severidad: **Alta**, **Media** o **Baja**. Registre al menos 5 hallazgos de seguridad.

| N.º | Hallazgo | Criterio incumplido | Evidencia | Severidad | Recomendación |
|:-:|:--|:--|:--|:-:|:--|
| 1 | | | | | |
| 2 | | | | | |
| 3 | | | | | |
| 4 | | | | | |
| 5 | | | | | |

### 5.3 Conclusión general de la auditoría

Escriba su conclusión: ¿está MediCitas v3.2 en condiciones de liberarse? Justifique con los hallazgos y recomiende qué hacer antes de la fecha contractual.

---

## 6. Preguntas de selección

Elija la respuesta correcta y muestre el procedimiento cuando haya cálculo.

1. Antes de liberar, el Product Owner y un grupo piloto confirman que médicos, administrativos y pacientes pueden iniciar sesión con el nuevo SSO sin bloqueos. Esta actividad es una:
   - a) Verificación
   - b) Validación
   - c) Auditoría
   - d) Revisión de gestión

2. ¿Qué característica de ISO/IEC 25010 compromete principalmente INC-102 (cuenta administrativa compartida)?
   - a) Seguridad (responsabilidad)
   - b) Fiabilidad
   - c) Compatibilidad
   - d) Portabilidad

3. Para auditar MediCitas v3.2, ¿quién debería liderar la auditoría?
   - a) El Scrum Master
   - b) Un auditor externo, independiente del equipo Scrum
   - c) El desarrollador del módulo de telemedicina
   - d) El Product Owner

4. ¿Qué porcentaje de los cambios de la sección 2.3 se desplegó sin revisión ni aprobación registrada?
   - a) 20 %
   - b) 40 %
   - c) 60 %
   - d) 80 %

5. ¿Qué porcentaje de las pruebas críticas de la sección 2.4 fue ejecutado?
   - a) 25 %
   - b) 40 %
   - c) 50 %
   - d) 75 %
