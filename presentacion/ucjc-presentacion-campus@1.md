# Contrato: `ucjc-presentacion-campus@1`

## Nombre

```text
ucjc-presentacion-campus@1
```

No es un evento del bus. Es el contrato de **estilo y script comunes** que impone el shell.

## Versión

| Campo | Valor |
| --- | --- |
| Versión del contrato | `1` |
| ¿Sustituye a una versión anterior? | no |

## Quién lo impone

**Profesor** (shell). Ficheros:

- `comun/campus.css` — variables `--ucjc-*` y clases `.ucjc-btn`, `.ucjc-label`, `.ucjc-title`
- `comun/campus.js` — `window.ucjcCampus` (`emitir`, `escuchar`, `leerTokens`, `version`)

En la tienda en vivo:

- https://cesar-andress.github.io/tienda-ucjc-shell/comun/campus.css
- https://cesar-andress.github.io/tienda-ucjc-shell/comun/campus.js

## Quién firma

Los cuatro equipos (un responsable por equipo; cubre variantes A/B/C):

- Identidad
- Descubrimiento
- Compra
- Datos

## Descripción

El shell carga el CSS y el JS de campus **antes** que vuestro `remote.js`.  
Así todas las piezas comparten colores, tipografía y una forma sencilla de emitir o escuchar eventos `ucjc:*`.

## Qué obliga

1. No pintéis `html`, `body` ni los huecos de otras piezas. Solo vuestro custom element.
2. Para colores, tipografía y radios de la interfaz usad las variables `--ucjc-*` del shell (llegan al Shadow DOM). No montéis otra paleta para botones y títulos principales.
3. Podéis usar `.ucjc-btn`, `.ucjc-btn-primary`, `.ucjc-label` y `.ucjc-title` si os vienen bien; no son obligatorias si ya usáis las variables.
4. Los eventos solo con nombres firmados en `eventos/`. Podéis usar `window.dispatchEvent` o `ucjcCampus.emitir` (mismo efecto).
5. Al arrancar, comprobad `window.ucjcCampus?.version === '1'`. Si no está, la pieza puede seguir funcionando, pero en clase cuenta como incumplimiento.
6. Tipografía: Figtree y Fraunces a través de las variables. No carguéis otra familia global en el documento.

## Qué no obliga

- El diseño interno de vuestra pieza (rejillas, modales, etc.).
- Usar Shadow DOM (recomendado, no obligatorio).
- Campos nuevos en eventos: eso va en los contratos de `eventos/`.

## Ejemplo mínimo

```js
const { marca } = window.ucjcCampus.leerTokens();

window.ucjcCampus.emitir('ucjc:descubrimiento:anadir-al-carrito@1', {
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
| Identidad | Firmante | | | |
| Descubrimiento | Firmante | | | |
| Compra | Firmante | | | |
| Datos | Firmante | | | |

## Estado del contrato

- [x] `propuesto`
- [ ] `firmado`
- [ ] `deprecado`

## Historial

- `2026-11-25` — Propuesta del profesor: estilo y script comunes desde el shell; firman los cuatro equipos.
- `2026-11-25` — API en español (`emitir` / `escuchar` / `leerTokens`).
