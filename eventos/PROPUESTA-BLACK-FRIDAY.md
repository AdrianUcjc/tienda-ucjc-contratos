# Black Friday — qué propone el profesor (27/11/2026)

El profesor deja contratos en **`propuesto`**.  
En clase **decidís** y, si hay acuerdo, firmáis la tabla de responsables.  
Solo lo **`firmado`** manda en la tienda.

Los tres del flujo mínimo siguen firmados y no se borran:

```text
ucjc:identidad:sesion-cambiada@1
ucjc:descubrimiento:anadir-al-carrito@1
ucjc:compra:pedido-confirmado@1
```

## Contrato A — campaña (aceptar o no)

[`ucjc-descubrimiento-campana-cambiada@1.md`](ucjc-descubrimiento-campana-cambiada@1.md)

```text
ucjc:descubrimiento:campana-cambiada@1
```

Descubrimiento enciende o apaga Black Friday. Compra y Datos escuchan.

**Decisión:** ¿lo firmamos? sí / no / con cambios.

## Contrato B — pedido con moneda (aceptar o no)

[`ucjc-compra-pedido-confirmado@2.md`](ucjc-compra-pedido-confirmado@2.md)

```text
ucjc:compra:pedido-confirmado@2
```

Igual que el pedido actual, pero con `moneda` obligatoria (`EUR` / `USD` / `GBP`)
y `campaña` opcional (`black-friday-2026`).

**Decisión (elegid una):**

| Opción | Qué significa |
| --- | --- |
| Firmar el `@2` | Compra pasa a emitir `@2` cuando esté listo; Datos escucha `@2`. El `@1` queda para compatibilidad. |
| Cambio menor en el `@1` | No hay `@2`. Se añaden `moneda` y `campaña` como **opcionales** al `@1` ya firmado. |
| Aparcar | Ni `@2` ni opcionales. Seguimos solo con euros y sin etiqueta de campaña en el pedido. |

## Después de decidir

1. Firmas en las tablas de los ficheros que aceptéis.
2. El profesor marca `firmado` (o escribe el cambio menor en el historial del `@1`).
3. Tags nuevos antes del viernes 27/11.

## Historial

- `2026-11-23` — Campaña `@1` y pedido `@2` en `propuesto`.
