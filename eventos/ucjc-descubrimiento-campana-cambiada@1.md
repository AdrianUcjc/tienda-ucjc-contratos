# Contrato: `ucjc:descubrimiento:campana-cambiada@1`

> **Estado: `propuesto` (23/11/2026).**  
> Borrador del profesor para el corte Black Friday (viernes 27/11).  
> **No implementar todavía** como referencia: primero OK en clase (miércoles 25/11) y firmas de emisor + consumidores.  
> Los tres contratos del flujo mínimo `@1` **no** se tocan.

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

**Descubrimiento** (dueño del catálogo y de las ofertas visibles)

## Equipos consumidores

- **Compra** (badge / mensaje en el carrito; no cambia el nombre de `pedido-confirmado@1`)
- **Datos** (variantes A y B: pueden etiquetar pedidos hechos durante la campaña)
- **Identidad** (opcional: mensaje de bienvenida; no es obligatorio para el flujo)

## Descripción

Descubrimiento emite este evento cuando **activa o desactiva** una campaña comercial del catálogo (p. ej. Black Friday 2026).  
Lo emite:

1. al cargar la pieza, con el estado actual de la campaña (para quien llegue tarde),
2. cada vez que la campaña pasa de inactiva a activa o al revés (botón de demo / horario).

Quien escucha actualiza su UI. **No** sustituye a `anadir-al-carrito@1` ni a `pedido-confirmado@1`: solo informa del contexto de campaña.

## Campos y tipos (`event.detail`)

| Campo | Tipo | Obligatorio / opcional | Descripción |
| --- | --- | --- | --- |
| `activa` | booleano | obligatorio | `true` si la campaña está en vigor ahora. |
| `codigo` | texto | obligatorio | Identificador estable de la campaña (`black-friday-2026`). Sin espacios. |
| `etiqueta` | texto | obligatorio | Texto corto para mostrar («Black Friday UCJC»). |
| `momento` | texto (ISO 8601) | obligatorio | Instantánea en la que se anuncia este estado. |
| `descuentoPct` | número | opcional | Porcentaje orientativo de descuento de escaparate (0–100). No obliga a Compra a recalcular. |
| `hasta` | texto (ISO 8601) | opcional | Fin previsto de la campaña. Si no viene, la pieza emisora no promete fecha. |

## Campos obligatorios y opcionales

- **Obligatorios:** `activa`, `codigo`, `etiqueta`, `momento`
- **Opcionales:** `descuentoPct`, `hasta`

## Ejemplo de payload

Campaña Black Friday encendida:

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

Campaña apagada:

```json
{
  "activa": false,
  "codigo": "black-friday-2026",
  "etiqueta": "Black Friday UCJC",
  "momento": "2026-11-28T00:00:00+01:00"
}
```

## Qué hace cada pieza (si se firma)

| Pieza | Comportamiento esperado |
| --- | --- |
| Descubrimiento | Emite al cargar y al conmutar. Puede marcar productos en oferta en su UI. |
| Compra | Si `activa`, muestra la `etiqueta` cerca del carrito. Sigue emitiendo `pedido-confirmado@1`. |
| Datos A/B | Pueden guardar `codigo` de campaña junto al pedido **solo** si también se acepta el campo opcional `campaña` en `pedido-confirmado` (ver `PROPUESTA-BLACK-FRIDAY.md`). |
| Identidad | Opcional: una línea de texto bajo el login. |

## Responsables que aprueban

| Equipo | Rol | Nombre del responsable | Fecha | Firma / visto bueno |
| --- | --- | --- | --- | --- |
| Descubrimiento | Emisor | |  | pendiente clase 25/11 |
| Compra | Consumidor | |  | pendiente |
| Datos A | Consumidor | |  | pendiente |
| Datos B | Consumidor | |  | pendiente |
| Identidad | Consumidor (opcional) | |  | pendiente |

## Estado del contrato

- [x] `propuesto`
- [ ] `firmado`
- [ ] `deprecado`

## Historial

- `2026-11-23` — Borrador del profesor para el corte Black Friday (27/11): campaña como evento nuevo, sin mutar los tres `@1` firmados.
