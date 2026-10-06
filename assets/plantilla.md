# PRD: Integración de nuevo procesador de pagos

> Plantilla para integrar procesadores de transferencias (IN/OUT) y métodos de pago alternativos. Lo que no aplique, bórralo; lo que no sepas todavía, déjalo como pregunta abierta en la sección 14.

---

## 1. Resumen ejecutivo
- **Nombre de la iniciativa / Key del ticket:**
- **Procesador:** (nombre, tipo: banco, wallet, PSP, agregador)
- **País(es):**
- **Método de pago:** (transferencia entrante, transferencia saliente, botón, QR, suscripción, etc.)
- **PM / Tech Lead / Equipo:**
- **Estado:** Borrador / En revisión / Aprobado
- **Resumen en 3 líneas:** qué se integra, para quién y por qué ahora.

## 2. Contexto y problema
- ¿Qué problema de negocio resuelve? (cobertura, costos, conversión, requerimiento de un cliente o regulatorio)
- ¿Qué pasa hoy sin este procesador?
- Clientes que lo solicitan, con volumen estimado.

## 3. Objetivos y métricas de éxito

| Objetivo | Métrica | Línea base | Meta | Plazo |
|---|---|---|---|---|
| | Volumen transaccionado / # transacciones | | | |
| | Tasa de aprobación | | | |
| | Tiempo de confirmación | | | |
| | Tasa de conciliación automática | | | |

**No objetivos:** qué queda explícitamente fuera.

## 4. Alcance
- **Incluye (MVP):**
- **Fase 2 / posteriores:**
- **Fuera de alcance:**
- **Flujos soportados:** pago, confirmación, expiración, cancelación, reverso, reembolso, consulta de estado.

## 5. Perfil del procesador
- Documentación técnica (links, versión de API, sandbox)
- Autenticación (OAuth, API key, firma, certificados, mTLS)
- Modelo de confirmación: síncrono, asíncrono por webhook, polling, o mixto
- Ambientes y credenciales: QA, UAT, producción
- SLAs, horarios de operación y ventanas de mantenimiento
- Límites: monto mínimo y máximo, límites diarios, TPS, rate limits
- Monedas soportadas
- Contacto técnico y comercial en el procesador

## 6. Flujo funcional
Diagrama o descripción paso a paso del flujo feliz, y luego:
- Flujos alternos: rechazo, timeout, usuario abandona, pago tardío, doble confirmación
- Mapeo de estados del procesador a estados internos (tabla)
- Mapeo de códigos de error/rechazo a códigos internos (tabla)

| Estado/código procesador | Estado/código interno | Descripción | ¿Reintentable? |
|---|---|---|---|
| | | | |

## 7. Requerimientos funcionales

| ID | Requerimiento | Prioridad (P0/P1/P2) | Criterio de aceptación |
|---|---|---|---|
| RF-01 | | | |

Considerar siempre:
- Campos requeridos del pagador y del comercio, con validaciones por país
- Configuración por comercio o cuenta (¿multiprocesador? ¿credenciales por comercio?)
- Idempotencia y manejo de duplicados
- Expiración y vigencia de la transacción
- Notificaciones (webhooks) hacia el comercio

## 8. Requerimientos no funcionales
- Disponibilidad y latencia esperadas
- Seguridad: manejo de secretos, cifrado, datos personales, cumplimiento
- Observabilidad: logs, métricas, alertas, dashboards
- Resiliencia: circuit breaker, reintentos, fallback
- Escalabilidad y volumen proyectado

## 9. Conciliación y operaciones
- Archivos o reportes de conciliación del procesador (formato, frecuencia, canal)
- Llaves de cruce entre la transacción propia y el registro del procesador
- Manejo de diferencias: pagos no reflejados, montos distintos, duplicados
- Proceso de liquidación (plazos, cuentas, calendario)
- Soporte y escalamiento: runbook para operaciones y atención al cliente
- Monitoreo de transacciones pendientes o "colgadas"

## 10. Costos y modelo comercial
- Tarifa del procesador (fija, variable, escalonada, mínimos mensuales)
- Costo de integración o setup
- Precio propuesto a clientes
- Impuestos y retenciones por país
- Impacto en margen y facturación

## 11. Legal, compliance y riesgo
- Contrato o acuerdo con el procesador (estado, firmantes)
- Requisitos regulatorios del país (licencias, reportes, KYC/AML)
- Evaluación de riesgo y fraude
- Obligaciones contractuales relevantes (SLAs, penalidades, exclusividades)

## 12. UX / UI y panel de administración
- Experiencia del pagador (pantallas, copy, estados de error)
- Configuración en el panel: alta del procesador, permisos y roles
- Reportes y vistas para el comercio
- Documentación pública y para desarrolladores (API, SDK, guías)

## 13. Plan de pruebas y salida a producción
- **QA:** casos felices, rechazos, timeouts, duplicados, montos límite
- **UAT con el procesador:** certificación o checklist que ellos exigen
- **Piloto:** clientes alfa, volumen limitado, criterios de éxito y rollback
- **Rollout:** feature flags, por país o cliente, calendario
- **Plan de rollback**
- **Comunicación:** comercial, soporte, operaciones

## 14. Dependencias, riesgos y preguntas abiertas

| Tipo | Descripción | Dueño | Mitigación / Fecha |
|---|---|---|---|
| Dependencia | | | |
| Riesgo | | | |
| Pregunta abierta | | | |

## 15. Épicas, historias y estimación
- Épicas e historias asociadas (con keys del gestor de tickets)
- Equipos involucrados: Backend, Frontend, UX, QA, Operaciones, Conciliación, Comercial, Legal
- Estimación de esfuerzo y fechas objetivo por hito

## 16. Stakeholders y aprobaciones

| Área | Nombre | Rol (Responsable/Aprobador/Informado) | Aprobado |
|---|---|---|---|
| Producto | | | |
| Tecnología | | | |
| Operaciones | | | |
| Legal | | | |
| Comercial | | | |
| Riesgo | | | |

---

**Tip:** las secciones 5 (confirmación), 6 (mapeo de estados y errores) y 9 (conciliación) suelen ser donde aparecen las sorpresas tarde. Conviene cerrarlas con el procesador antes de escribir historias.
