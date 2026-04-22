- [Como contribuir a un proyecto](#Como-contribuir-a-un-proyecto)
    - [Github](#Github)
    - [Fork](#Fork)
    - [Clone](#Clone)
    - [Push](#Push)
- [Como contribuir a este proyecto](#Como-contribuir-a-este-proyecto)
    - [Conceptos clave](#Conceptos-clave)
        - [Node y npm](#Node-y-npm)
        - [Frameworks](#Frameworks)
    - [Arquitectura](#Arquitectura)
        - [Astro](#Astro)
        - [Motion one](#Motion-one)
        - [Components](#Components)

# Como contribuir a un proyecto

## Github

[Github](https://theelephantcoder.github.io/History-of-GitHub/) es la plataforma de hospedaje
de proyectos de codigo abierto usando git. En esta seccion te explico como usarlo para trabajar en un
proyecto.

> [!NOTE]
> Antes de aprender a contrubuir a repositorios de Github es necesario que conozcas los 
> [basicos de git](https://git-scm.com/).

En los repositorios dentro de tu perfil de github o en los cuales tienes permios de hacer cambios
trabajar en el proyecto es tan facil como [clonar el repositorio](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository)
,hacer cambios, [capturar los cambios en un commit](https://git-scm.com/docs/git-commit)
y [subir los cambios al repositorio de Github](https://docs.github.com/en/get-started/using-git/pushing-commits-to-a-remote-repository). 
Sin embargo en proyectos en los cuales no tienes permiso de hacer cambio el flujo de trabajo cambia. En esta seccion,
vas a aprender a colaborar en cualquier poryecto hospedado en github aunque las mismas ideas se mantienen 
para [alternativas de hosteo de proyectos](https://www.geeksforgeeks.org/blogs/top-10-github-alternatives-that-you-can-consider/)

## Fork

Lo primero es tener tu propia copia del proyecto en el que quieres trabajar, esto se le conoce como "fork".
Esta copia actua como tu espacio de trabajo dentro del codigo del proyecto, aqui puedes hacer cambios y sugerir
los cambios en el repositorio original, esto lo veremos mas adelante.

Para hacer un fork dentro de Github dirigete al repo, en la parte superior derecha da click en el botton *Fork*.
Esto te llevara a una lista de opciones para crear tu fork. En *Owner* escoje tu perfil, por predeterminado, el nombre del fork
sera el mismo del repositorio original. Las demas opciones por ahora no son importantes. Clickea *Create fork*.

## Clone

Ya tienes un fork del repositorio en tu perfil de github. Ahora necestias tener el codigo del proyecto de forma local.
Para esto ve a la pagina del fork, localiza el boton *Code*, copia la URL del repositorio. Usa esta URL para clonar el 
poryecto de forma local con [git clone](https://git-scm.com/docs/git-clone)

```
git clone https://github.com/TU-USUARIO/EL-REPO
```

Con eso los archivos deberian clonarse en un directorio nuevo bajo el nombre del projecto

```
git clone https://github.com/TU-USUARIO/EL-REPO
> Cloning into `EL-REPO`...
> remote: Counting objects: 10, done.
> remote: Compressing objects: 100% (8/8), done.
> remove: Total 10 (delta 1), reused 10 (delta 1)
> Unpacking objects: 100% (10/10), done.
```

Antes de hacer cambios es conveniente crear un `branch` y cambiarte a ella. Esto hara mas facil tus contribuciones al proyecto.

```
git branch NOMBRE-BRANCH
git checkout NOMBRE-BRANCH
```

## Push

A esta altura puedes empezar a hacer los cambios al codigo del proyecto en tu editor de texto favorito. Despues de hacer los cambios y 
guardarlos pon los archivos cambiados en la zona de `stage` y registralos en un `commit`

```
git add ARCHIVO-CAMBIADO
git commit -m "descripcion de los cambios"
```

Estos cambios estan guardadas de forma local, para actualizar el repositorio de github "empuja" los cambios al remoto.

```
git push
```

> [!NOTE]
> Esta pequeña guia usa git mediante comandos de terminal, sin embargo puedes usar [herramientas graficas](https://github.com/dictcp/awesome-git)
> que faciliten estos pasos.

# Como contribuir a este proyecto

Antes de señalar las reglas de contribución al proyecto, vale la pena revisar
los conceptos necesarios para ayudar al desarrollo del sitio web.

> [!NOTE]
> Se asume que tiene conceptos básicos de [HTML](https://developer.mozilla.org/en-US/docs/Web/HTML), [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) y [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript).

## Conceptos clave

### Node y npm

Después de trabajar con JavaScript dentro del navegador, es fácil darse cuenta de que
[JavaScript es un gran lenguaje de programación](https://github.com/denysdovhan/wtfjs).
Por lo tanto, resulta natural pensar en utilizarlo fuera del navegador, como cualquier
otro lenguaje.

Con este objetivo, Ryan Dahl creó en 2009 [Node.js](https://nodejs.org/en), con la idea de liberar a JavaScript
del navegador. Esto dio lugar al desarrollo de más herramientas necesarias en la
programación moderna.

Entre ellas se encuentra [npm](https://www.npmjs.com/) (Node Package Manager), una herramienta que permite
publicar, instalar y compartir código escrito en JavaScript con otros desarrolladores.

En conjunto, Node.js y npm transforman el desarrollo web en un proceso más estructurado,
donde no solo se escribe código para el navegador, sino que también se construye un
entorno de trabajo más completo y eficiente.

### Frameworks

Es natural que, en el desarrollo de una página web, se comience maquetando la estructura
del sitio usando etiquetas de HTML y posteriormente se cree un sistema visual a partir
de reglas de estilo con CSS. Esto daría como resultado un sitio estático.

Si se desea añadir reactividad dinámica, la etiqueta `script` permite utilizar JavaScript
para modificar estilos y elementos de forma programática. A partir de `querySelector()` y
`addEventListener()`, se pueden definir una serie de reglas que modifiquen el documento.

Estas reglas, a su vez, pueden organizarse en funciones de JavaScript con las que se
componen interacciones más complejas. Llegado a este punto, lo que hemos logrado es crear
nuestro propio "framework de JavaScript", que abstrae los métodos nativos en funciones
propias, adaptadas a nuestras necesidades.

## Arquitectura

El projecto fue creado apartir de la plantilla [principal de astro]() usando nodejs y npm.
Ya que tengas el codigo de forma local, utliza el comando `npm run dev` para comprobar que 
tu entorno funciona correctamente, este lanza un servidor local, abre la pagina con tu navegador 
para ver el sito.

Para trabajar en el proyecto ten a la mano la siguiente tabla de commandos:

| Command                   | Action                                           |
| :------------------------ | :----------------------------------------------- |
| `npm install`             | instala las dependencias                         |
| `npm run dev`             | inicia un server local ne `localhost:4321`       |
| `npm run build`           | compilar el sitio para produccio en `./dist/`    |
| `npm run preview`         | vista preview del sito de forma local            |
| `npm run astro ...`       | CLI comandos como `astro add`, `astro check`     |
| `npm run astro -- --help` | obtener ayuda con la CLI de Astro                |

Asi como [la documentacion de astro](https://docs.astro.build)
 
### Astro
 
[Astro](https://astro.build/) es el framework con el que está construido el sitio. Su característica
principal es que genera páginas con el mínimo de JavaScript posible: el contenido se renderiza en el
servidor y solo se envía HTML y CSS al navegador de forma predeterminada.
 
La unidad básica de Astro es el archivo `.astro`. Estos archivos tienen tres secciones: el
*frontmatter*, delimitado por `---`, donde se escribe lógica en JavaScript o TypeScript que se
ejecuta en tiempo de compilación; el *template*, donde se define la estructura HTML de forma similar
a JSX; y los bloques opcionales `<style>` y `<script>`, para estilos y comportamiento en el cliente.
 
```
---
// frontmatter: lógica en tiempo de compilación
const mensaje = "Hola mundo";
---
 
<!-- template: estructura HTML -->
<p>{mensaje}</p>
 
<style>
  /* estilos con scope automático al componente */
  p { color: red; }
</style>
```
 
> [!NOTE]
> Los estilos dentro de `<style>` en un archivo `.astro` tienen scope automático al componente,
> por lo que no afectan al resto de la página. Para estilos globales se usa el atributo `is:global`.
 
### Motion
 
[Motion](https://motion.dev/) es la biblioteca de animaciones del proyecto. Se importa directamente
en los bloques `<script>` de los componentes `.astro` y se usa para añadir animaciones e
interacciones visuales.
 
En el proyecto se usa de dos maneras. La función `animate` aplica una animación a uno o varios
elementos del DOM:
 
```js
import { animate } from "motion";
 
animate(elemento, { scaleY: [0, 1.1, 1] }, { duration: 0.5 });
```
 
La función `hover` ejecuta una animación al pasar el cursor sobre un elemento y la revierte al salir:
 
```js
import { animate, hover } from "motion";
 
hover(".motion-hover", (element) => {
  animate(element, { scale: 1.5 });
  return () => animate(element, { scale: 1 });
});
```
 
Para que `hover` funcione sobre un elemento, este debe tener la clase `motion-hover` y la propiedad
CSS `display: inline-block`, que ya está definida de forma global en `Layout.astro`.
 
### Componentes
 
El proyecto organiza la interfaz en componentes `.astro` ubicados en `src/components/`. Cada
componente encapsula su propio HTML, CSS y JavaScript en un solo archivo.

Para más información sobre qué es un componente y cuáles hemos definido en este proyecto, dirigete a [Components.md](./Components.md).
 
