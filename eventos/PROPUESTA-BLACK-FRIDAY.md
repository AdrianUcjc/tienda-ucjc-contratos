# Black Friday — qué propone el profesor (27/11/2026)

El profesor deja aquí contratos en estado **`propuesto`**.  
En clase, cada responsable **acepta** (firma en la tabla del contrato).  
Hasta que no esté **`firmado`**, no es la referencia de la tienda.

Los tres eventos del flujo mínimo siguen **`firmado`** y no se reescriben:

```text
ucjc:identidad:sesion-cambiada@1
ucjc:descubrimiento:anadir-al-carrito@1
ucjc:compra:pedido-confirmado@1
```

## 1. Evento nuevo (a aceptar)

Fichero: [`ucjc-descubrimiento-campana-cambiada@1.md`](ucjc-descubrimiento-campana-cambiada@1.md)

```text
ucjc:descubrimiento:campana-cambiada@1
```

Descubrimiento dice si la campaña `black-friday-2026` está encendida o apagada.  
Compra y Datos lo escuchan. Identidad puede escucharlo.

**Aceptación:** firmas en la tabla de responsables de ese fichero.

## 2. Campos opcionales (solo si la clase quiere)

Si aceptáis un **cambio menor**, el profesor los añade a los `@1` ya firmados
(siguen siendo opcionales; quien no los mande no rompe a nadie):

| Contrato | Campo | Uso en Black Friday |
| --- | --- | --- |
| `anadir-al-carrito@1` | `precioOriginal` (número) | Precio tachado; `precio` es el que se paga |
| `anadir-al-carrito@1` | `etiqueta` (texto) | Por ejemplo `"black-friday"` |
| `pedido-confirmado@1` | `campaña` (texto) | Por ejemplo `"black-friday-2026"` |
| `pedido-confirmado@1` | `moneda` (texto) | `EUR`, `USD` o `GBP`; si falta, euros |

Si preferís **cambio mayor**, esos campos van a un `@2` nuevo.  
Si preferís **aparcar**, no se añaden.

## 3. Después de aceptar

1. El profesor marca `firmado` (o escribe los opcionales en el historial del `@1`).
2. Cada equipo publica un tag que cumpla lo aceptado.
3. El viernes 27/11 (Black Friday) se enseña en la tienda con la campaña encendida.

## Historial

- `2026-11-23` — Propuesta del profesor en este repositorio.
