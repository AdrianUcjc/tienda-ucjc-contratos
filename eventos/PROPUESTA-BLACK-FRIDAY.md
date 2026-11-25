# Black Friday — mesa de hoy (25/11/2026) → demo 27/11

`campana-cambiada@1` ya está **`firmado`**.  
Siguen en **`propuesto`** (hoy se decide): `pedido-confirmado@2` y **`moneda-cambiada@1`** (nuevo).

El flujo mínimo (`@1`) no se borra.

## Quién toca qué

| Equipo | Campaña (firmado) | Pedido `@2` | Moneda (nuevo) |
| --- | --- | --- | --- |
| Identidad | No | No | No |
| Descubrimiento | Emite | No | Emite |
| Compra | Escucha | Emite `@2` | Escucha |
| Datos A / B | Escuchan | Escuchan `@2` | Opcional |

## 1 — `campana-cambiada@1` · **firmado**

[`ucjc-descubrimiento-campana-cambiada@1.md`](ucjc-descubrimiento-campana-cambiada@1.md)

Para el viernes: Compra y Datos A/B deben **escucharlo** de verdad (banner / etiqueta).  
Si no lo escucháis, el contrato firmado no se nota en la tienda.

## 2 — `pedido-confirmado@2` · **propuesto**

[`ucjc-compra-pedido-confirmado@2.md`](ucjc-compra-pedido-confirmado@2.md)

Elegid **una** en clase:

| Opción | Esfuerzo | Qué pasa |
| --- | --- | --- |
| Firmar el `@2` | Alto | Compra emite `@2` con `moneda` (+ `campaña` opcional); Datos escuchan `@2`. El `@1` **sigue** hasta que Digáis lo contrario. |
| Cambio menor en el `@1` | Bajo | No hay `@2`. En el `@1` se añaden `moneda` y `campaña` **opcionales**. |
| Aparcar | Ninguno | Seguimos solo con euros y `@1`. |

**Ojo PR #3 (Adrián):** no mergear tal cual. Quiere firmar `@2` (bien) pero marca `sesion-cambiada@1` como deprecado en el README (mal: eso es Identidad).

Firmas ya en el fichero: Datos A (Hans). Faltan Compra (emisor limpio) y Datos B.

## 3 — `moneda-cambiada@1` · **propuesto · nuevo hoy**

[`ucjc-descubrimiento-moneda-cambiada@1.md`](ucjc-descubrimiento-moneda-cambiada@1.md)

En el shell (corte `v0.3.10`) Descubrimiento A/B ya cambian EUR/USD (y Compra C habla de libras).  
Sin este contrato, Compra no se entera de la moneda del catálogo.

| Opción | Esfuerzo | Qué pasa |
| --- | --- | --- |
| Firmar hoy | Medio | Descubrimiento emite; Compra escucha (carrito / checkout). |
| Aparcar | Ninguno | Cada pieza sigue con su moneda local; el pedido puede mentir. |

## Orden de la mesa (25/11)

1. Demo rápida del shell `v0.3.10` (A/B/C).
2. Recordar: `campana-cambiada@1` firmado → ¿quién ya escucha?
3. Decidir `@2` / cambio menor / aparcar.
4. Decidir `moneda-cambiada@1` sí / no.
5. Encargo viernes 27/11: solo lo **firmado** hoy cuenta en la demo.

## Historial

- `2026-11-23` — A y B en `propuesto`; Identidad fuera; A simplificada.
- `2026-11-23` — A (`campana-cambiada@1`) → **`firmado`** (merge PR #1 · Daniel Molina / Descubrimiento).
- `2026-11-25` — Mesa de aula: añadir `moneda-cambiada@1`; aviso PR #3; shell `v0.3.10`.
