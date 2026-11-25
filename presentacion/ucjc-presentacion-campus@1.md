# Contrato: `ucjc-presentacion-campus@1`

## Nombre

```text
ucjc-presentacion-campus@1
```

No es un evento del bus. Es el contrato de estilo y script comunes que impone el shell. Desde que se firma, la tienda tiene un solo criterio de CSS y de JS.

## Versión

| Campo | Valor |
| --- | --- |
| Versión del contrato | `1` |
| ¿Sustituye a una versión anterior? | no |

## Quién lo impone

El profesor, desde el shell. Ficheros:

- `comun/campus.css`: variables `--ucjc-*` en `:root` y clases `.ucjc-btn`, `.ucjc-btn-primary`, `.ucjc-label`, `.ucjc-title`.
- `comun/campus.js`: `window.ucjcCampus` (`emitir`, `escuchar`, `leerTokens`, `version`).

En la tienda en vivo:

- https://cesar-andress.github.io/tienda-ucjc-shell/comun/campus.css
- https://cesar-andress.github.io/tienda-ucjc-shell/comun/campus.js

El shell carga los dos ficheros antes que cualquier `remote.js`.

## Quién firma

Cada variante enchufada en la tienda, por medio del responsable del repo que la publica. La firma obliga al hueco: cualquier variante que quiera ocupar `identidad`, `descubrimiento`, `compra` o `datos` tiene que cumplir este contrato, la haya hecho el equipo de esa pieza o otro.

## Entrada en vigor

| Fecha | Qué ocurre |
| --- | --- |
| Miércoles 25/11/2026 | Propuesta del profesor. Se discute en aula. |
| Lunes 30/11/2026 | Firma en aula. Cada variante trae una release con color y tipografía en variables. Defensa oral de cada grupo. |
| Miércoles 2/12/2026 | Toda release nueva cumple el contrato completo. |
| Miércoles 9/12/2026 | El shell solo enchufa variantes conformes. Las demás pasan al relleno. |

## Variables disponibles

| Variable | Uso |
| --- | --- |
| `--ucjc-ink` | texto principal |
| `--ucjc-muted` | texto secundario |
| `--ucjc-fog` | fondo de página |
| `--ucjc-mist` | fondo suave, separadores |
| `--ucjc-panel` | superficie de tarjetas y texto sobre la marca |
| `--ucjc-edge` | bordes |
| `--ucjc-brand` | color de marca |
| `--ucjc-brand-bright` | marca en acciones y estados activos |
| `--ucjc-leaf` | éxito |
| `--ucjc-warn` | aviso y error |
| `--ucjc-font-sans` | texto (Figtree) |
| `--ucjc-font-display` | títulos (Fraunces) |
| `--ucjc-radius` | radio de esquinas |
| `--ucjc-space`, `--ucjc-space-lg` | espaciado |
| `--ucjc-ease` | curva de animación |

Si falta una variable que necesitáis, se pide por PR a este contrato. No se inventa en la pieza.

## Qué obliga

### CSS

1. Solo se pinta vuestro custom element. Nada en `html`, `body` ni en los huecos de otras piezas.
2. Color, tipografía, radios y espaciados salen de las variables `--ucjc-*`, siempre con valor de reserva: `var(--ucjc-brand, #0b3d4a)`. Un color escrito a mano solo puede aparecer como valor de reserva.
3. Tipografía: `--ucjc-font-sans` y `--ucjc-font-display`. Ni `@font-face`, ni `<link>` de fuentes, ni `font-family` propia.
4. Ningún `!important`.

### JS

5. Solo se emiten eventos firmados en `eventos/`, con `window.dispatchEvent` o con `ucjcCampus.emitir` (mismo efecto).
6. Lo que se escucha se deja de escuchar: el listener que se pone en `window` al montar la pieza se quita en `disconnectedCallback`. `ucjcCampus.escuchar` devuelve la función que lo quita.
7. Al arrancar se comprueba `window.ucjcCampus?.version === '1'`. Si no está (por ejemplo, en la página de demo del repo, fuera de la tienda), la pieza sigue funcionando con los valores de reserva y `window.dispatchEvent`.
8. Hay al menos un test que comprueba el `detail` de cada evento que la pieza emite.

### Nota técnica sobre las clases

Las clases `.ucjc-*` viven en la hoja del documento y no entran en el Shadow DOM. Dentro de vuestra pieza no se aplican: usad las variables, que sí se heredan.

## Qué no obliga

- El diseño interno de la pieza (rejillas, modales, animaciones).
- Usar las clases `.ucjc-*`.
- Usar Shadow DOM (recomendado; hoy lo usan las diez variantes).
- Campos nuevos en eventos: eso va en los contratos de `eventos/`.

## Cómo se comprueba

- Se mira la release del tag que enchufa el shell, no la rama `main`.
- DevTools sobre la pieza dentro de la tienda: se elige un color al azar y se mira si sale de una variable `--ucjc-*` o está escrito a mano.
- Consola filtrada por `[evento ucjc]`: cada evento emitido tiene nombre firmado.
- Si una regla no se cumple, la variante no es conforme.

## Ejemplo mínimo

```css
:host {
  display: block;
  color: var(--ucjc-ink, #1a242c);
  font-family: var(--ucjc-font-sans, "Segoe UI", sans-serif);
}
button.comprar {
  background: var(--ucjc-brand, #0b3d4a);
  color: var(--ucjc-panel, #fbfcfb);
  border-radius: var(--ucjc-radius, 6px);
  padding: var(--ucjc-space, 0.75rem);
}
```

```js
const EV_CAMPANA = 'ucjc:descubrimiento:campana-cambiada@1';

class UcjcCompra extends HTMLElement {
  #quitar = null;

  connectedCallback() {
    if (window.ucjcCampus?.version !== '1') console.warn('[compra] sin campus');
    const alCambiar = (e) => this.#pintarCampana(e.detail);
    this.#quitar = window.ucjcCampus
      ? window.ucjcCampus.escuchar(EV_CAMPANA, alCambiar)
      : (window.addEventListener(EV_CAMPANA, alCambiar),
         () => window.removeEventListener(EV_CAMPANA, alCambiar));
  }

  disconnectedCallback() {
    this.#quitar?.();
  }

  #pintarCampana(detail) { /* ... */ }
}
```

## Responsables que aprueban

Una fila por variante. La release es el tag que demuestra la conformidad.

| Variante | Repo | Responsable | Release conforme | Fecha | Firma / visto bueno |
| --- | --- | --- | --- | --- | --- |
| Identidad A | `ucjc-ecommerce-identidad/tienda-ucjc-identidad` | | | | |
| Identidad B | `Juampee/ucjc-identidad-plus` | | | | |
| Descubrimiento A | `dani84mol/tienda-ucjc-descubrimiento` | | | | |
| Descubrimiento B | `tienda-ucjc-compra/tienda-ucjc-descubrimiento-B` | | | | |
| Descubrimiento C | `Juampee/descubrimiento-muy-mejorado` | | | | |
| Compra A | `tienda-ucjc-compra/tienda-ucjc-compra` | | | | |
| Compra B | `ucjc-ecommerce-identidad/tienda-ucjc-compra-b` | | | | |
| Compra C | `dani84mol/tienda-ucjc-compra` | | | | |
| Datos A | `hansjeffas/tienda-ucjc-datos` | | | | |
| Datos B | `Juampee/ucjc-datos-alt2` | | | | |

## Estado del contrato

- [x] `propuesto`
- [ ] `firmado`
- [ ] `deprecado`

## Historial

- `2026-11-25` — Propuesta del profesor: estilo y script comunes desde el shell; firman los cuatro equipos.
- `2026-11-25` — API en español (`emitir` / `escuchar` / `leerTokens`).
- `2026-11-25` — Firma por variante, fechas de entrada en vigor, valores de reserva, sin `!important`, listeners que se quitan, un test por evento emitido; ejemplo sin colores escritos a mano; nota sobre las clases y el Shadow DOM.
