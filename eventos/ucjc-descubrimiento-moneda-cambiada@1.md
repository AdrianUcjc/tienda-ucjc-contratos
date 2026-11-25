# Contrato: `ucjc:descubrimiento:moneda-cambiada@1`

## Nombre del evento

```text
ucjc:descubrimiento:moneda-cambiada@1
```

Nombre de fichero: `ucjc-descubrimiento-moneda-cambiada@1.md`

## Versión

| Campo | Valor |
| --- | --- |
| Versión del contrato del evento | `1` |
| ¿Sustituye a una versión anterior? | no |

## Equipo emisor

**Descubrimiento**

## Equipos consumidores

- **Compra**
- **Datos** (A y B) — opcional; útil si muestran importes

Identidad no interviene.

## Descripción

Descubrimiento avisa cuando el catálogo cambia de moneda de visualización
(`EUR`, `USD`, `GBP`, …). También avisa al cargar la pieza con la moneda actual.

Compra puede usarlo para etiquetar el carrito o al confirmar el pedido
(junto con `pedido-confirmado@2` si se firma).

No sustituye a `anadir-al-carrito@1`: el precio de cada línea sigue yendo en
el `detail` de ese evento; este contrato solo dice **en qué moneda** está el
catálogo ahora.

## Campos y tipos (`event.detail`)

| Campo | Tipo | Obligatorio / opcional | Descripción |
| --- | --- | --- | --- |
| `moneda` | texto | obligatorio | Código ISO corto: `EUR`, `USD`, `GBP` |
| `momento` | texto (ISO 8601) | obligatorio | Cuándo se anuncia el cambio |

## Campos obligatorios y opcionales

- **Obligatorios:** `moneda`, `momento`
- **Opcionales:** ninguno

## Ejemplo de payload

```json
{
  "moneda": "USD",
  "momento": "2026-11-25T10:15:00+01:00"
}
```

## Decisiones descartadas

| Idea | Motivo del descarte |
| --- | --- |
| Meter `moneda` obligatorio en `anadir-al-carrito@1` | Rompe consumidores que ya escuchan `@1` sin ese campo |
| Que Compra adivine la moneda sin evento | Dos piezas no comparten estado; haría falta acoplamiento |

## Responsables que aprueban

| Equipo | Rol | Nombre del responsable | Fecha | Firma / visto bueno |
| --- | --- | --- | --- | --- |
| Descubrimiento | Emisor | | | |
| Compra | Consumidor | | | |
| Datos A | Consumidor | | | |
| Datos B | Consumidor | | | |

## Estado del contrato

- [x] `propuesto`
- [ ] `firmado`
- [ ] `deprecado`

## Historial

- `2026-11-25` — Propuesta del profesor (Black Friday / aula 25/11). En el shell ya hay selectores EUR/USD en Descubrimiento; falta el contrato.
