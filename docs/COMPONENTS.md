# Índice

- [¿Por qué?](#por-qué)
  - [Contenido](#contenido)
  - [Estilo](#estilo)
  - [Lógica](#lógica)
  - [Todo en todas partes al mismo tiempo](#todo-en-todas-partes-al-mismo-tiempo)
- [¿Qué son?](#qué-son)
- [¿Cómo se ven?](#cómo-se-ven)
  - [Pensar en componentes](#pensar-en-componentes)
- [Componentes definidos](#componentes-definidos)
  - [`Boton.astro`](#botonastro)
  - [`Etiqueta.astro`](#etiquetaastro)
  - [`Footer.astro`](#footerastro)
  - [`Formulas.astro`](#formulasastro)
  - [`Nav.astro`](#navastro)
  - [`Seccion.astro`](#seccionastro)
  - [`Tarjeta.astro`](#tarjetaastro)

---

## ¿Por qué?

Antes de entender cómo funciona y cómo se define un componente, veamos cómo se crea una página web. A estas alturas seguramente ya sabes cómo hacer una: no la mejor ni la más bonita, pero sí una que funcione. Aun así, este resumen te será útil.

Con ustedes, esta es mi página web. Tiembla, Mark Zuckerberg:

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width" />
    <title>CaraLibro</title>

    <style>
      h1 {
        color: blue;
      }
    </style>

    <script>
      console.log('¿Dónde están mis millones? cfffff');
    </script>

  </head>

  <body>
    <h1>CaraLibro</h1>
    <p>Mi idea muy original</p>
  </body>

</html>
```

Dejando de lado las bromas, esta pequeña página web nos ayudará a entender qué es y por qué son tan importantes los componentes.

Veamos de qué está compuesta nuestra idea millonaria. Aunque todo el archivo está escrito en HTML, hay tres partes clave. Leyendo la página de arriba hacia abajo, vemos una etiqueta `<style>` con reglas de estilo, una `<script>` con lógica y un `<body>` con el contenido. Vamos a revisar cada una.

## Contenido

```html
<h1>CaraLibro</h1>
<p>Mi idea muy original</p>
```

Dentro de la programación, [Markup](https://en.wikipedia.org/wiki/Markup_language) es una "familia" de lenguajes que definen la estructura de un documento.

> [!NOTE]
> Este archivo que estás leyendo está escrito en [Markdown](https://www.markdownguide.org/), un lenguaje de markup.

HTML (HyperText **Markup** Language) define la estructura de la página. Este lenguaje define "elementos" (esta idea será importante más adelante en tu aventura); estos tienen la forma de etiquetas. Cada etiqueta tiene atributos para modificar la estructura interna del elemento.

## Estilo

```css
h1 {
  color: blue;
}
```

Con el contenido estructurado, alguien debe darle estilo. CSS nos proporciona herramientas, a través de selectores y propiedades, para dar características a elementos específicos de la página.

## Lógica

```js
console.log('¿Dónde están mis millones? cfffff');
```

Si fuera solo por las dos secciones anteriores, nuestra página sería incapaz de presentar contenido dinámico. JavaScript es el veneno que los desarrolladores web escogieron para llenar su código de bugs y vaciar su vida de felicidad. Odio y resentimiento aparte, JavaScript, a diferencia de HTML o CSS, nos da toda la potencia de un lenguaje de programación para interactuar con nuestra página.

## Todo en todas partes al mismo tiempo

Entendida la estructura de la página, imaginemos éxito en nuestro futuro, muchos pavos en nuestra cuenta y demasiado contenido en nuestra página. Veamos cómo se vería ese lindo futuro:

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width" />
    <title>CaraLibro</title>

    <style>
      .
      .
      .
      h1 {
        color: blue;
      }
      .
      .
      .
    </style>

    <script>
      .
      .
      .
      console.log('¿Dónde están mis millones? cfffff');
      .
      .
      .
    </script>

  </head>

  <body>
    .
    .
    .
    <h1>CaraLibro</h1>
    <p>Mi idea muy original</p>
    .
    .
    .
  </body>

</html>
```

Aquí el contenido, el estilo y la lógica se han expandido. Sin embargo, para el ojo atento, las interacciones entre estructura, estilo y lógica siguen siendo las mismas. El problema es que todas conviven en el mismo lugar, interfiriendo entre sí.

Claro que podríamos mover el `<style>` a un archivo `.css` y el `<script>` a un archivo `.js`, e importarlos en el `.html`. Sin embargo, ahora las interacciones quedan separadas en distintos archivos.

¿No te gustaría poder tener el contenido, sus reglas de estilo y sus interacciones lógicas en un mismo lugar, sin tener que navegar entre múltiples archivos y fragmentos? Estás de suerte: te presento los componentes.

Un componente, en un proyecto saludable, es la unidad básica a partir de la cual se construyen jerarquías más amplias hasta llegar a la página.

# ¿Qué son?

Un componente se define en un archivo `.astro`. Estos son plantillas que generan HTML simple y plano.

¿Y el estilo y la lógica? No temas: en un componente puedes poner tanto CSS como JavaScript (o TypeScript), aunque por favor que sea poco. Todo esto se compila en *build time* y al navegador se le entrega HTML rápido y optimizado.

# ¿Cómo se ven?

Un componente se compone de dos partes: el Frontmatter y la plantilla. Ambas trabajan juntas para hacer lo que sea.

```astro
---
const quien = "pues yo cffff"
---

<p>Hola {quien}</p>

<style>
  p {
    color: blue;
  }
</style>
```

Astro usa `---` para delimitar el Frontmatter. Aquí podemos escribir TypeScript para importar otros componentes, importar otros frameworks de componentes, importar datos, crear variables o acceder a los [props](https://docs.astro.build/en/basics/astro-components/#component-props) de nuestro componente.

El delimitador funciona como división visual, pero más importante aún, como división entre nosotros y el platónico usuario. Esta división garantiza que podemos obtener datos de bases de datos, pasar valores sensibles y, en general, ejecutar nuestra lógica sin que pase por el navegador del usuario.

La plantilla determina el HTML que será entregado. Podemos escribir HTML plano; sin embargo, Astro nos permite usar un sabor de [JSX](https://docs.astro.build/en/reference/astro-syntax/), con lo que podemos espolvorear JavaScript en nuestro HTML, así como también usar [reglas especiales de Astro](https://docs.astro.build/en/reference/directives-reference/).

## Pensar en componentes

Los componentes nos permiten crear etiquetas personalizadas y componerlas para crear interfaces más complejas, manteniendo los archivos simples y los elementos cerca de los estilos que los modifican y la lógica que los transforma.

---

# Componentes definidos

A continuación se describen los componentes que conforman el proyecto.

## `Boton.astro`

Envuelve un enlace `<a>` con estilos de botón. Recibe tres props: `href` (obligatorio) para la URL de destino, `target` para controlar si abre en la misma pestaña o en una nueva, y `class` para agregar clases adicionales. Su contenido se define a través de un `<slot />`, lo que permite poner cualquier texto o ícono dentro. Incluye una animación de hover que eleva el botón y cambia su color de naranja a dorado.

## `Etiqueta.astro`

Renderiza una etiqueta tipo "badge" o "chip". Es inteligente respecto a su tag: si recibe una prop `href`, se convierte en un enlace `<a>`; de lo contrario, renderiza un `<p>`. Acepta `colorFondo` y `colorTexto` tomados del sistema de colores del proyecto, con valores por defecto de azul y blanco respectivamente. Añade decoración con el símbolo `✦` antes y después del contenido vía CSS.

## `Footer.astro`

Pie de página del sitio. Contiene una lista de enlaces a redes sociales (Gmail, Facebook, YouTube) con sus respectivos íconos SVG, y el nombre de la organización. Visualmente aparece como una "pestaña" anclada al fondo de la página con bordes redondeados en la parte superior. Incluye una barra de color fija en la parte inferior de la pantalla.

## `Formulas.astro`

Fondo decorativo animado que muestra fórmulas físicas flotando por la pantalla. Las fórmulas rebotan contra los bordes de la ventana como partículas. Guarda su estado en `localStorage` para que la posición de cada fórmula persista entre navegaciones. También reescala las posiciones al cambiar el tamaño de la ventana.

## `Nav.astro`

Barra de navegación principal del sitio. Muestra el logo de la organización y los enlaces a las secciones: Convocatoria, Recursos, Resultados y Nosotros. Detecta la ruta activa para resaltarla visualmente como una pestaña que "cuelga" de la barra superior. En dispositivos móviles, los enlaces se ocultan y se revelan con un botón hamburguesa animado.

## `Seccion.astro`

Contenedor semántico para secciones de página. Recibe un `titulo` obligatorio, un `acento` de color para personalizar el encabezado y la línea lateral, y una `alineacion` para el contenido. Incluye una animación de entrada: cuando la sección entra al viewport, una línea vertical crece hacia abajo y luego el contenido aparece deslizándose desde la izquierda.

## `Tarjeta.astro`

Contenedor con apariencia de tarjeta (fondo blanco, bordes redondeados, sombra sutil). Acepta un `titulo` opcional que, si se provee, se muestra como una etiqueta flotante centrada en el borde superior de la tarjeta, activando además un estilo "resaltado" con borde más grueso. El color del borde y la etiqueta se controla con la prop `acento`.
