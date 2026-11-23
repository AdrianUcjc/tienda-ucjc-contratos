# Contrato: ucjc:compra:envio-gratuito@1

## Nombre del evento

```text
ucjc:compra:envio-gratuito@1
```
Nombre de fichero: `ucjc-compra-envio-gratuito@1.md`

## Versión

| Campo | Valor |
| --- | --- |
| Versión del evento | `1` |
| ¿Sustituye a una versión anterior? | `no` |

## Equipo emisor

`Compra`

## Equipos consumidores

- `Datos (A y B)`

## Descripción

Evento que informa de si un pedido cumple las condiciones para disponer de envío gratuito. Se considera que un pedido tiene envío gratuito cuando el importe total de la compra es igual o superior a 80 €.

## Campos y tipos

| Campo | Tipo | Obligatorio / opcional | Descripción |
| --- | --- | --- | --- |
| `<evio_gratuito>` | `booleano` | obligatorio | |
| `Indica si el pedido cumple las condiciones para tener envío gratuito.`|
| `<pedidoId>` | `string` | obligatorio | |
| `Identificador del pedido al que corresponde el evento.`|

## Campos obligatorios y opcionales

- **Obligatorios:** `<envio_gratuito>`
- **Opcionales:** `ninguno`.

## Ejemplo de payload

```json
{
  "pedidoId": "PED-2026-1101",
  "envio_gratuito": true
}
```
```json
{
  "pedidoId": "PED-2026-1101",
  "envio_gratuito": false
}
```

El ejemplo debe coincidir con la tabla de campos. No añadáis claves que no estén documentadas.

## Responsables que aprobaron el contrato

| Equipo | Rol | Nombre del responsable | Fecha | Firma / visto bueno |
| --- | --- | --- | --- | --- |
| `<compra>` | Emisor | `Adrián Pingarrón`| `2026-11-23`| `-`|
| `<datos>` | Consumidor | | | |

## Estado del contrato

- [x] `propuesto` — borrador en negociación; aún no se implementa como referencia.
- [ ] `firmado` — aprobado por emisor y consumidores; es la referencia compartida.
- [ ] `deprecado` — sustituido por una versión nueva; se mantiene temporalmente por compatibilidad.

## Historial

- `<2026-11-23>` — creación
