---
titulo: "Cargar contenido dinámicamente: post-load, herramientas modernas y casos reales"
descripcion: >
  Aprende cómo las aplicaciones modernas cargan datos después de renderizar la interfaz inicial. Esta lección explora el concepto de post-load, las herramientas actuales para hacer peticiones, y los casos de uso más comunes como filtros, buscadores y feeds dinámicos.
tags: ["JavaScript", "fetch", "axios", "post-load", "APIs", "carga dinámica"]
---


En el desarrollo web moderno, no todo el contenido se entrega junto con la carga inicial de la página. Muchas aplicaciones muestran primero la estructura básica (HTML, CSS, JavaScript) y luego solicitan contenido adicional según la interacción del usuario o las necesidades del momento.

A este enfoque se lo conoce como **carga post-load**. Es una práctica esencial para mejorar la velocidad percibida, reducir el uso de datos y ofrecer experiencias más fluidas e interactivas.

En esta lección vas a aprender:

- Qué es post-load y por qué cambió la forma de construir interfaces.
- Qué herramientas y patrones modernos existen para hacer solicitudes asincrónicas.
- Qué tipos de funcionalidades reales utilizan esta técnica y cómo funcionan.



## ¿Qué es post-load?

El término *post-load* se refiere a la práctica de **cargar datos o contenido después de que la página ya fue renderizada por el navegador**.

Esto significa que cuando una página web se carga, solo trae consigo la estructura básica. Luego, mediante JavaScript, se realizan peticiones al servidor para obtener información adicional, como resultados de búsqueda, listados, comentarios, etc.

Por ejemplo, al abrir una tienda online, podés ver primero la estructura general del sitio. Pero cuando buscás un producto, aplicás filtros o hacés scroll, los nuevos resultados llegan desde el servidor sin necesidad de recargar toda la página. Eso es post-load.

Esta técnica permite:

- Acelerar el tiempo de carga inicial.
- Adaptar dinámicamente el contenido a la interacción del usuario.
- Optimizar el uso de datos y recursos del navegador.


## Herramientas modernas para hacer peticiones (las "22 maneras")

Cuando hablamos de hacer una petición a un servidor, en realidad existen muchas formas distintas de lograrlo. La elección depende del contexto, la complejidad del proyecto y los objetivos específicos de cada situación.

Aquí agrupamos las **formas modernas más utilizadas**, no como una lista para memorizar, sino para ofrecer un mapa conceptual claro del ecosistema actual.

### 1. Peticiones con `fetch()` (API nativa)

- `fetch(url)`: solicitud GET básica.
- `fetch(url, { method: 'POST' })`: solicitud POST.
- `fetch` con `async/await`: sintaxis más legible.
- Uso de `headers`: envío de tokens, JSON, etc.
- `AbortController`: cancelar solicitudes.
- `FormData`: envío de archivos.
- `ReadableStream`: procesamiento por partes.

### 2. Usar `axios` (librería externa)

- `axios.get`, `axios.post`: solicitudes simples.
- `axios.create(config)`: instancias configuradas.
- Interceptores (`interceptors.request/response`): modificar o controlar flujos.
- Cancelación de solicitudes (obsoleto pero útil en apps legadas).
- Configuración global de base URL, headers, etc.

### 3. Casos avanzados y contextos específicos

- `XMLHttpRequest`: técnica antigua, aún presente.
- `jQuery.ajax()`: usado en entornos legados.
- GraphQL con `fetch` o `apollo-client`.
- Librerías como `useSWR`, `react-query`: peticiones con cache en React.
- `WebSockets`: comunicación en tiempo real.
- `sendBeacon()`: para estadísticas o trazas en segundo plano.
- `Image()`: tracking por carga de imágenes.

La clave está en entender **cuándo usar cada herramienta**, más que en saber todas.


## Casos comunes de post-load

El contenido dinámico no es solo una mejora de UX: es una necesidad real en múltiples tipos de interfaces. A continuación analizamos tres de los casos más comunes donde el post-load es fundamental.

### Buscadores en tiempo real

Cuando el usuario escribe en un campo de búsqueda, espera ver resultados al instante, sin necesidad de presionar Enter ni recargar la página.

Esto se logra escuchando el evento `input`, y haciendo una solicitud al servidor cada vez que el texto cambia (idealmente con control de frecuencia mediante debounce).

```js
input.addEventListener("input", async (e) => {
  const res = await fetch(`/api?q=${e.target.value}`);
  const data = await res.json();
  renderResultados(data);
});
```

### Filtros dinámicos

El usuario marca filtros (categorías, rangos, etiquetas) y el contenido se adapta automáticamente. Esto se utiliza en tiendas online, listados de productos, catálogos, entre otros.

```js
fetch(`/api/items?categoria=${categoria}&precio=${precio}`)
  .then(res => res.json())
  .then(setResultados);
```
No hay recarga de página, solo cambio en el DOM con los nuevos datos.

### Feeds y contenido progresivo

En redes sociales o dashboards, el contenido se actualiza periódicamente o al hacer scroll. En estos casos, se usan técnicas como scroll infinito, actualizaciones por intervalo o WebSockets.

```js
window.addEventListener("scroll", async () => {
  if (window.innerHeight + window.scrollY >= document.body.offsetHeight) {
    const res = await fetch("/api/feed?page=2");
    const data = await res.json();
    agregarAlDOM(data);
  }
});
```

Cargar contenido dinámicamente después del `load` ya no es una opción técnica, es un estándar de las aplicaciones modernas. Entender el concepto de post-load, dominar las herramientas disponibles y reconocer sus aplicaciones reales te permite construir experiencias web más eficientes, rápidas y orientadas al usuario.