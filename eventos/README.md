# Carpeta `eventos/`

Aquí viven los contratos de la tienda (un fichero Markdown por evento) y las propuestas de aula.

- Repositorio **público**. Si el fichero no está en esta carpeta de `main`, **no cuenta** para la tienda.
- Hoy (**23/11/2026**, tag del repo **`v0.2.1`**): los tres del flujo mínimo siguen **`firmado`**. Hay propuestas **Black Friday** en estado `propuesto` (no implementar hasta firmar en clase).
- Mapa del camino punta a punta: [`FLUJO-MINIMO.md`](FLUJO-MINIMO.md).
- Paquete Black Friday: [`PROPUESTA-BLACK-FRIDAY.md`](PROPUESTA-BLACK-FRIDAY.md).
- El [ejemplo de formato](EJEMPLO-como-rellenar.md) sigue siendo solo plantilla (**no implementar**).
- No dejéis borradores en la **raíz** del repositorio. No mutéis un `@1` firmado sin voto de clase: proponer versión nueva, evento nuevo, o campos opcionales documentados.

## Contratos activos (`firmado`)

| Evento | Fichero |
| --- | --- |
| `ucjc:identidad:sesion-cambiada@1` | [`ucjc-identidad-sesion-cambiada@1.md`](ucjc-identidad-sesion-cambiada@1.md) |
| `ucjc:descubrimiento:anadir-al-carrito@1` | [`ucjc-descubrimiento-anadir-al-carrito@1.md`](ucjc-descubrimiento-anadir-al-carrito@1.md) |
| `ucjc:compra:pedido-confirmado@1` | [`ucjc-compra-pedido-confirmado@1.md`](ucjc-compra-pedido-confirmado@1.md) |

## Propuestas (`propuesto`) — Black Friday 27/11

| Evento / doc | Fichero | Notas |
| --- | --- | --- |
| `ucjc:descubrimiento:campana-cambiada@1` | [`ucjc-descubrimiento-campana-cambiada@1.md`](ucjc-descubrimiento-campana-cambiada@1.md) | Campaña on/off (emite Descubrimiento) |
| Paquete BF + moneda / ofertas | [`PROPUESTA-BLACK-FRIDAY.md`](PROPUESTA-BLACK-FRIDAY.md) | Voto 25/11: menor / mayor / aparcar |

## Cómo proponer un contrato nuevo

1. Copiad [`../PLANTILLA-EVENTO.md`](../PLANTILLA-EVENTO.md).
2. Mirad el ejemplo: [`EJEMPLO-como-rellenar.md`](EJEMPLO-como-rellenar.md) (**no implementar**).
3. Guardad el fichero aquí, p. ej. `ucjc-descubrimiento-anadir-al-carrito@2.md`.
4. Abrid un Pull Request. El profesor fusiona a `main` cuando el estado sea `firmado` (o deja `propuesto` visible para negociar en clase).
