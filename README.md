# Java para principiantes

[![script/cibuild](https://github.com/javaprincipiantes/javaprincipiantes.github.io/actions/workflows/ci.yaml/badge.svg)](https://github.com/javaprincipiantes/javaprincipiantes.github.io/actions/workflows/ci.yaml)

Guía para quienes empiezan a desarrollar aplicaciones de consola en Java.
Se publica con GitHub Pages en **<https://javaprincipiantes.github.io>**.

## Cómo correr el sitio localmente

```sh
script/bootstrap      # instala las dependencias
bundle exec jekyll serve
```

Queda disponible en <http://localhost:4000>.

## Cómo correr las validaciones

```sh
script/cibuild
```

Es lo mismo que corre el CI en cada push: construye el sitio, revisa los enlaces
y los hashes de integridad con `html-proofer`, pasa `rubocop` y valida `index.html`
y la hoja de estilos contra los validadores del W3C.

Las validaciones del W3C y de enlaces necesitan conexión a internet.

## Estructura

| Ruta | Qué contiene |
| --- | --- |
| `index.md` | portada con el índice completo de la guía |
| `content/` | una página de Markdown por sección |
| `_data/nav.yml` | secciones que arma la barra lateral; hay que agregar acá toda sección nueva |
| `_layouts/default.html` | única plantilla: cabecera, barra lateral, contenido y pie |
| `_includes/` | fragmentos del `<head>`: colores de tema y analytics |
| `_sass/_paleta.scss` | paleta completa como custom properties, con modo claro y oscuro |
| `_sass/_syntax.scss` | coloreado de sintaxis de Rouge |
| `_sass/main.scss` | estilos de base, grilla y componentes |
| `assets/` | hoja de estilos e imágenes de los ejemplos |

## Cómo agregar una sección

1. Crear `content/mi-seccion.md` con el front matter `layout: default`.
2. Agregarla a `_data/nav.yml` para que aparezca en la barra lateral.
3. Enlazarla desde el índice de `index.md`.

## Sobre los estilos

El sitio no usa un tema de Jekyll: los estilos son propios y viven en `_sass/`.
Los colores nunca se escriben en las reglas, siempre salen de las custom properties
de `_sass/_paleta.scss`, así el modo oscuro es una sola redefinición de esa paleta.

No se cargan fuentes ni hojas de estilo externas a propósito: `html-proofer` corre
con `--check-sri` y los CDN de fuentes no publican hashes de integridad.

El sitio nació como un fork de [Hacker](https://github.com/pages-themes/hacker),
el tema de GitHub Pages, que ya no se usa.

## Licencia

[CC0 1.0 Universal](LICENSE).
