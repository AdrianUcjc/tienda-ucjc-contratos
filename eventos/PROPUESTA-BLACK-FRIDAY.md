# Black Friday — propuestas del profesor (27/11/2026)

`campana-cambiada@1` ya está **`firmado`** (PR #1 · Descubrimiento, 23/11).  
Sigue en **`propuesto`**: `pedido-confirmado@2`. Hasta que no esté **`firmado`**, no cuenta.

El flujo mínimo (`@1`) no se borra.

## Quién toca qué

| Equipo | Contrato A (campaña) | Contrato B (pedido `@2`) |
| --- | --- | --- |
| Identidad | No | No |
| Descubrimiento | Emite (botón on/off) | No |
| Compra | Escucha (un texto) | Emite el `@2` |
| Datos A / B | Escuchan (un texto) | Escuchan el `@2` |

La A es sencilla.  
La B es la que puede costar: Compra y las dos Datos tienen que ir a la vez.

## A — `campana-cambiada@1` · **firmado**

[`ucjc-descubrimiento-campana-cambiada@1.md`](ucjc-descubrimiento-campana-cambiada@1.md)

Firmado vía PR #1 (dani84mol / Descubrimiento). Compra y Datos deben escucharlo.

## B — `pedido-confirmado@2`

[`ucjc-compra-pedido-confirmado@2.md`](ucjc-compra-pedido-confirmado@2.md)

Elegid **una**:

| Opción | Esfuerzo | Qué pasa |
| --- | --- | --- |
| Firmar el `@2` | Alto | Compra emite `@2`; Datos escuchan `@2`. |
| Cambio menor en el `@1` | Bajo | No hay `@2`. En el `@1` se añaden `moneda` y `campaña` **opcionales**. Quien no los mande sigue igual. |
| Aparcar | Ninguno | Seguimos solo con euros. |

## Historial

- `2026-11-23` — A y B en `propuesto`; Identidad fuera; A simplificada.
- `2026-11-23` — A (`campana-cambiada@1`) → **`firmado`** (merge PR #1).
