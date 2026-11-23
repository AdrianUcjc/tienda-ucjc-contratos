# Propuesta de aula — Black Friday UCJC (27/11/2026)

> Documento del profesor. **No es un contrato firmado.**  
> Sirve para el miércoles **25/11** (negociar / votar) y el viernes **27/11** (demo en la tienda).  
> Los tres eventos del flujo mínimo siguen **`firmado`** y **no se reescriben** aquí.

## Por qué esto y no reventar el `@1`

La tienda ya vende de punta a punta con:

```text
sesion-cambiada@1 → anadir-al-carrito@1 → pedido-confirmado@1
```

Black Friday es un **contexto temporal** (ofertas, badge, etiqueta en el pedido). Eso pide:

1. un **evento nuevo** de campaña (no existe hoy), y/o  
2. **campos opcionales** en contratos ya firmados (cambio menor), y/o  
3. un **`@2`** si el cambio rompe a alguien.

La moneda (`EUR` / `USD` / …), que ya empezó a circular en repos de alumnos, encaja en el mismo debate: o va como opcional en `@1`, o como `@2`, o se aparca.

## Paquete propuesto (tres piezas)

### A. Evento nuevo (recomendado) — `propuesto`

Fichero: [`ucjc-descubrimiento-campana-cambiada@1.md`](ucjc-descubrimiento-campana-cambiada@1.md)

```text
ucjc:descubrimiento:campana-cambiada@1
```

Descubrimiento anuncia si la campaña `black-friday-2026` está activa. Compra y Datos escuchan. Identidad puede escuchar.

**Voto en clase:** ¿lo firmamos el 25/11 para demo el 27/11?

### B. Campos opcionales en `@1` (cambio menor — solo si se vota)

No están aún en los ficheros `firmado`. Si la clase vota **cambio menor**, el profesor los añade al historial de cada `@1` **sin** subir de versión:

| Contrato firmado | Campo nuevo (opcional) | Para qué en Black Friday |
| --- | --- | --- |
| `anadir-al-carrito@1` | `precioOriginal` (número) | Precio tachado; `precio` sigue siendo el que paga |
| `anadir-al-carrito@1` | `etiqueta` (texto) | p. ej. `"black-friday"` |
| `pedido-confirmado@1` | `campaña` (texto) | p. ej. `"black-friday-2026"` para que Datos lo muestre |
| `pedido-confirmado@1` | `moneda` (texto) | `EUR` / `USD` / `GBP`; si falta → `EUR` (propuesta ya vista el 18/11) |

Si la clase vota **cambio mayor**, esos campos van a un fichero `@2` nuevo y hasta que se firme se sigue emitiendo solo `@1`.

Si vota **aparcar**, no se toca nada; solo queda el evento de campaña (o ni eso).

### C. Qué no hacemos

- No inventar eventos en el código sin fichero en este repo.
- No abrir Issues en repos de compañeros «en nombre del profesor».
- No exigir a Identidad un login especial de Black Friday (fuera de alcance).
- No mezclar monedas dentro del mismo pedido.

## Quién implementa qué (si se firma el 25/11)

| Equipo | Mínimo para la demo del 27/11 |
| --- | --- |
| Descubrimiento | Emitir `campana-cambiada@1` (on/off). Si hay campos opcionales: mandar `precio` rebajado + `precioOriginal` / `etiqueta` al añadir. |
| Compra | Escuchar campaña (badge). Si `moneda`/`campaña` opcionales: rellenarlas en `pedido-confirmado@1`. Tag nuevo. |
| Datos A / B | Escuchar campaña; si llega `campaña` o `moneda` en el pedido, mostrarlas. Tag nuevo. |
| Identidad | Opcional: una línea si `activa`. No bloquea la demo. |

## Relación con lo ya hecho por alumnos (23/11)

| Hecho | Cómo encaja |
| --- | --- |
| Descubrimiento `v0.2.5` (selector EUR/USD) | UI adelantada; el precio en USD **sin** campo `moneda` en el evento confunde a Compra. Hace falta el cauce de contratos. |
| Datos B `CONTRATO-MONEDA.md` en su repo | Buena intención; **no cuenta** hasta existir aquí como `propuesto`/`firmado` o como campo opcional votado. |
| Compra / Datos A sin tag del 20/11 | Black Friday es la excusa limpia para el tag nuevo del miércoles. |

## Orden de clase sugerido (25/11)

1. Leer este fichero + el contrato `campana-cambiada@1` (`propuesto`).
2. Votar: firmar campaña ¿sí/no?
3. Votar moneda + campos de oferta: menor / mayor / aparcar.
4. Si hay OK, el profesor marca `firmado` (o añade opcionales al historial) y los equipos publican tag antes del 27/11.
5. El 27/11 (o el lunes siguiente si no hay clase el viernes): demo en el shell con campaña encendida.

## Estado de este documento

- `2026-11-23` — Alta del paquete Black Friday en el repo de contratos (`propuesto`).
