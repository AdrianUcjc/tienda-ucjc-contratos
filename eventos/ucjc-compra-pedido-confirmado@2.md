# Contrato: `ucjc:compra:pedido-confirmado@2`

## Nombre del evento

```text
ucjc:compra:pedido-confirmado@2
```

Nombre de fichero: `ucjc-compra-pedido-confirmado@2.md`

## Versión

| Campo | Valor |
| --- | --- |
| Versión del contrato del evento | `2` |
| ¿Sustituye a una versión anterior? | sí: `ucjc:compra:pedido-confirmado@1` (el `@1` sigue válido hasta que la clase diga lo contrario) |

## Equipo emisor

**Compra**

## Equipos consumidores

- **Datos** (variante A)
- **Datos** (variante B)

## Descripción

Igual que el `@1`: Compra lo emite al confirmar el pedido; Datos lo guarda y lo muestra.  
En el `@2` el pedido lleva **moneda** y, si aplica, el **código de campaña** (Black Friday u otra).

Mientras este contrato esté solo `propuesto`, Compra debe seguir emitiendo el `@1`.

## Campos y tipos (`event.detail`)

| Campo | Tipo | Obligatorio / opcional | Descripción |
| --- | --- | --- | --- |
| `pedidoId` | texto | obligatorio | Id del pedido, lo genera Compra. |
| `usuarioId` | texto | obligatorio | Usuario que confirma (el de la sesión). |
| `creadoEn` | texto (ISO 8601) | obligatorio | Instantánea de la confirmación. |
| `total` | número | obligatorio | Importe total en la moneda de `moneda`. |
| `lineas` | lista de objetos | obligatorio | Líneas del pedido. |
| `moneda` | texto | obligatorio | `EUR`, `USD` o `GBP`. Un solo pedido, una sola moneda. |
| `campaña` | texto | opcional | Código de campaña (`black-friday-2026`). Si no hay campaña, no se manda. |

### Elementos de `lineas[]`

| Campo | Tipo | Obligatorio / opcional | Descripción |
| --- | --- | --- | --- |
| `productoId` | texto | obligatorio | Id de producto. |
| `nombre` | texto | obligatorio | Nombre para mostrar. |
| `precio` | número | obligatorio | Precio unitario en la moneda del pedido. |
| `cantidad` | número | obligatorio | Unidades (≥ 1). |

## Campos obligatorios y opcionales

- **Obligatorios:** `pedidoId`, `usuarioId`, `creadoEn`, `total`, `lineas`, `moneda`
- **Opcionales:** `campaña`

## Ejemplo de payload

```json
{
  "pedidoId": "PED-2026-1101",
  "usuarioId": "u-123",
  "creadoEn": "2026-11-27T11:05:00+01:00",
  "moneda": "EUR",
  "campaña": "black-friday-2026",
  "total": 31.98,
  "lineas": [
    {
      "productoId": "prod-101",
      "nombre": "Camiseta UCJC",
      "precio": 15.99,
      "cantidad": 2
    }
  ]
}
```

## Responsables que aprueban

| Equipo | Rol | Nombre del responsable | Fecha | Firma / visto bueno |
| --- | --- | --- | --- | --- |
| Compra | Emisor | | | |
| Datos A | Consumidor | | | |
| Datos B | Consumidor | | | |

## Estado del contrato

- [x] `propuesto` — el profesor lo pone; la clase decide si se acepta
- [ ] `firmado`
- [ ] `deprecado`

## Historial

- `2026-11-23` — Propuesta del profesor para Black Friday: pedido con moneda y campaña.
