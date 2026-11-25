# Contrato: presentación campus `@1`

## Nombre

```text
ucjc-presentacion-campus@1
```

No es un evento de bus. Es el contrato de **CSS y JS comunes** que impone el shell.

## Versión

| Campo | Valor |
| --- | --- |
| Versión | `1` |
| ¿Sustituye a una versión anterior? | no |

## Quién lo impone

**Profesor** (shell). Ficheros en el repo del shell:

- `comun/campus.css` — variables `--ucjc-*` y clases `.ucjc-btn`, `.ucjc-label`, `.ucjc-title`
- `comun/campus.js` — `window.ucjcCampus` (`dispatch`, `on`, `tokens`, `version`)

URL en Pages (mismo origen que la tienda):

- https://cesar-andress.github.io/tienda-ucjc-shell/comun/campus.css
- https://cesar-andress.github.io/tienda-ucjc-shell/comun/campus.js

## Quién firma

Todos los equipos de pieza (cada responsable una vez; vale para variantes A/B/C del mismo equipo):

- Identidad
- Descubrimiento
- Compra
- Datos

## Qué obliga

1. **No** pintar `html`, `body` ni huecos de otras piezas. Solo vuestro custom element.
2. Colores, tipografía y radios de la UI de producto: usar las variables `--ucjc-*` del shell (heredan dentro del Shadow DOM). No inventéis una paleta paralela para botones/títulos principales.
3. Podéis usar las clases `.ucjc-btn`, `.ucjc-btn-primary`, `.ucjc-label`, `.ucjc-title` si os encajan; no son obligatorias si ya usáis las variables.
4. Eventos: solo nombres firmados en `eventos/`. Podéis emitir con `window.dispatchEvent` o con `ucjcCampus.dispatch` (mismo resultado).
5. Al cargar, comprobar `window.ucjcCampus?.version === '1'` (o `tokens().presentacion`). Si falta, la pieza puede seguir, pero en clase se considera incumplimiento del contrato.
6. Tipografía: Figtree / Fraunces vía variables; no carguéis otra familia global en el documento.

## Qué no obliga

- El layout interno de vuestra pieza (rejilla, modales, etc.).
- Que uses Shadow DOM (recomendado, no obligatorio).
- Campos nuevos en eventos: eso va en contratos de `eventos/`.

## Ejemplo mínimo (dentro del CE)

```js
const brand = getComputedStyle(document.documentElement)
  .getPropertyValue('--ucjc-brand').trim();

// o
const { brand: b } = window.ucjcCampus.tokens();

window.ucjcCampus.dispatch('ucjc:descubrimiento:anadir-al-carrito@1', {
  productoId: 'prod-1',
  nombre: 'Camiseta',
  precio: 19.99,
  cantidad: 1,
});
```

```css
:host {
  color: var(--ucjc-ink);
  font-family: var(--ucjc-font-sans);
}
button.comprar {
  background: var(--ucjc-brand);
  color: #fff;
  border-radius: var(--ucjc-radius);
}
```

## Responsables que aprueban

| Equipo | Rol | Nombre del responsable | Fecha | Firma / visto bueno |
| --- | --- | --- | --- | --- |
| Identidad | Consumidor | | | |
| Descubrimiento | Consumidor | | | |
| Compra | Consumidor | | | |
| Datos | Consumidor | | | |

## Estado del contrato

- [x] `propuesto`
- [ ] `firmado`
- [ ] `deprecado`

## Historial

- `2026-11-25` — Propuesta del profesor: CSS/JS comunes desde el shell; firma de los cuatro equipos.
