---
name: prd-procesador
description: "Escribe el PRD de una integración con un nuevo procesador de pagos (banco, wallet, PSP, agregador) para transferencias entrantes/salientes o métodos de pago alternativos, a partir de una plantilla de 16 secciones. Úsala siempre que se pida un PRD, BRD, documento de requerimientos o spec para integrar un procesador, aliado, banco o billetera, aunque no se diga 'PRD' (ej. 'necesito documentar la integración con X', 'arma el doc para el nuevo método de pago local', 'bajemos a requerimientos lo de la nueva wallet')."
---

# prd-procesador: PRD de integración con un nuevo procesador de pagos

Produce el PRD de una integración de procesador usando `assets/plantilla.md` como estructura. Escríbelo en el idioma del usuario, con tono directo y concreto.

## Por qué esta skill existe

Un PRD de integración falla casi siempre por lo mismo: se escriben historias antes de cerrar con el procesador cómo confirma el pago, qué estados y errores devuelve y cómo se concilia. Por eso el orden de trabajo no es el de la plantilla: se cierran primero las secciones 5, 6 y 9, y el resto se apoya en ellas.

## Cómo trabajar

1. **Reunir lo que ya existe antes de preguntar.** Si el usuario da una key de ticket, links, documentación del procesador o un PRD anterior, léelos con las herramientas disponibles. Lo que se pueda extraer de ahí no se pregunta de nuevo.
2. **Cabecera (sección 1).** Pregunta lo mínimo: procesador y tipo, país(es), método de pago, key del ticket, equipo. El resto se deduce o se pregunta después.
3. **Entrevista en este orden**, de a un bloque por vez, no las 16 secciones de golpe:
   - Primero **5 (perfil del procesador), 6 (flujo, mapeo de estados y de errores) y 9 (conciliación)**: es donde aparecen las sorpresas tarde.
   - Después 2, 3 y 4 (problema, métricas, alcance MVP vs fase 2).
   - Después 7 y 8 (requerimientos funcionales y no funcionales).
   - Por último 10 a 16 (costos, legal, UX, pruebas, riesgos, épicas, aprobaciones).
   Si el usuario trae material, convierte cada bloque en un borrador y pídele que corrija, en vez de hacerle preguntas abiertas.
4. **No inventar.** Cifras, SLAs, límites, tarifas, nombres y fechas que no se sepan van como pregunta abierta en la sección 14, con dueño si se conoce. Un hueco declarado es mejor que un dato plausible pero falso, porque el PRD lo leen tecnología, operaciones, legal y riesgo.
5. **Podar.** Elimina las secciones o ítems que no corresponden (por ejemplo, suscripciones si es solo transferencia entrante) en lugar de dejarlos vacíos.
6. **Requerimientos con criterio de aceptación verificable.** Cada RF lleva ID (RF-01…), prioridad P0/P1/P2 y un criterio que QA pueda comprobar. Cubre siempre: validaciones por país, configuración por comercio o cuenta, idempotencia, expiración y notificaciones al comercio.
7. **Tablas de mapeo (sección 6).** Estado/código del procesador → estado/código interno, con descripción y si es reintentable. Si falta el catálogo del procesador, deja la tabla con las filas conocidas y una pregunta abierta.
8. **Cierre.** Antes de entregar, revisa que cada métrica de la sección 3 tenga línea base y meta o una pregunta abierta, que las secciones 5, 6 y 9 no estén vacías y que la sección 14 liste todo lo pendiente. Resume al final en 3 líneas lo que falta cerrar con el procesador.

## Dónde se guarda

Pregunta al usuario dónde guardarlo. Si no tiene preferencia, usa `prd-<procesador>-<pais>-<metodo>.md` en la carpeta de trabajo (slug en minúsculas con guiones). Estado inicial: **Borrador**. Si quiere publicarlo en una wiki o crear épicas en el gestor de tickets, ofrécelo como paso siguiente y no lo hagas sin su sí.
