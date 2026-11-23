# Contrato: `ucjc:descubrimiento:campana-cambiada@1`

## Nombre del evento

```text
ucjc:descubrimiento:campana-cambiada@1
```

Nombre de fichero: `ucjc-descubrimiento-campana-cambiada@1.md`

## Versión

| Campo | Valor |
| --- | --- |
| Versión del contrato del evento | `1` |
| ¿Sustituye a una versión anterior? | no |

## Equipo emisor

**Descubrimiento**

## Equipos consumidores

- **Compra**
- **Datos** (variante A y variante B)
- **Identidad** (opcional)

## Descripción

Descubrimiento emite este evento cuando enciende o apaga una campaña del catálogo
(por ejemplo Black Friday). También lo emite una vez al cargar la pieza, con el
estado actual, para quien entre después.

Quien escucha actualiza lo que muestra. Este evento no sustituye a
`anadir-al-carrito@1` ni a `pedido-confirmado@1`.

## Campos y tipos (`event.detail`)

| Campo | Tipo | Obligatorio / opcional | Descripción |
| --- | --- | --- | --- |
| `activa` | booleano | obligatorio | `true` si la campaña está encendida. |
| `codigo` | texto | obligatorio | Identificador de la campaña, sin espacios (`black-friday-2026`). |
| `etiqueta` | texto | obligatorio | Texto corto para pantalla («Black Friday UCJC»). |
| `momento` | texto (ISO 8601) | obligatorio | Cuándo se anuncia este estado. |
| `descuentoPct` | número | opcional | Descuento de escaparate (0–100). Orientativo. |
| `hasta` | texto (ISO 8601) | opcional | Cuándo termina la campaña. |

## Campos obligatorios y opcionales

- **Obligatorios:** `activa`, `codigo`, `etiqueta`, `momento`
- **Opcionales:** `descuentoPct`, `hasta`

## Ejemplo de payload

```json
{
  "activa": true,
  "codigo": "black-friday-2026",
  "etiqueta": "Black Friday UCJC",
  "momento": "2026-11-27T09:00:00+01:00",
  "descuentoPct": 20,
  "hasta": "2026-11-28T00:00:00+01:00"
}
```

```json
{
  "activa": false,
  "codigo": "black-friday-2026",
  "etiqueta": "Black Friday UCJC",
  "momento": "2026-11-28T00:00:00+01:00"
}
```

## Responsables que aprueban

| Equipo | Rol | Nombre del responsable | Fecha | Firma / visto bueno |
| --- | --- | --- | --- | --- |
| Descubrimiento | Emisor | | | |
| Compra | Consumidor | | | |
| Datos A | Consumidor | | | |
| Datos B | Consumidor | | | |
| Identidad | Consumidor (opcional) | | | |

## Estado del contrato

- [x] `propuesto` — lo pone el profesor; hace falta el OK de los responsables en clase
- [ ] `firmado`
- [ ] `deprecado`

## Historial

- `2026-11-23` — Propuesta del profesor para Black Friday (27/11). No cambia los tres `@1` ya firmados.
