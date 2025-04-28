---
title: "Depurando Solicitudes de API: Cómo ver y corregir errores en el navegador"
description: >
  Aprende cómo usar las herramientas de desarrollo del navegador para observar, analizar y solucionar problemas en las solicitudes HTTP realizadas por JavaScript. Esta lección te enseña a interpretar errores, entender tiempos de respuesta y mejorar la interacción con APIs.
tags: ["depuración", "API", "HTTP", "navegador", "herramientas de desarrollo", "errores"]
---


Cuando una página web usa JavaScript para hacer solicitudes a una [API](https://4geeks.com/es/lesson/comprendiendo-rest-apis?search=api), no siempre todo sale perfecto. Pueden ocurrir errores de red, respuestas incompletas o problemas en el servidor. Por suerte, los navegadores modernos nos dan **herramientas de desarrollo** que nos permiten **ver qué está pasando detrás de escena**, qué solicitudes se envían, qué respuestas llegan y en cuánto tiempo.

Aprender a usar estas herramientas es **clave para entender, detectar y solucionar problemas** cuando trabajas con [APIs](https://4geeks.com/es/lesson/comprendiendo-rest-apis?search=api).


### ¿Cómo ver y analizar cada solicitud de tu aplicación?

En la mayoría de los navegadores (como Chrome, Firefox o Edge), puedes abrir las **herramientas de desarrollo** presionando: `F12` o clic derecho ➔ **"Inspeccionar"** ➔ pestaña **"Red"** (o "Network"). La pestaña **Red** muestra en tiempo real cada solicitud que hace la página, el tipo de solicitud (GET, POST, etc.), el estado de la respuesta (200, 404, 500...), el tamaño de la respuesta y el tiempo que tardó. 

Imagina que eres un chef y algo sale mal en la cocina, ha sucedido un problema con un plato que está incompleto o mal servido. Sin herramientas, solo puedes adivinar qué falló, pero con herramientas de inspección puedes ver todo el pedido, los ingredientes, el tiempo de cocción y hasta si el camarero se olvidó algo. La pestaña **"Red"** del navegador es como una cámara que **graba cada paso del pedido** para que puedas ver qué pasó en caso de problemas.

![browser-inspect](../assets/browser-inspect.png)



En la imagen se muestran varias pestañas para explorar:

- **Headers**: muestra los encabezados enviados y recibidos.
- **Preview**: vista previa de cómo se verían los datos.
- **Response**: muestra el contenido real de la respuesta (por ejemplo, un JSON completo). La pestaña **Response** es muy útil para ver qué datos llegaron realmente y analizar si el contenido es el esperado.
- **Timing**: muestra cuánto tiempo tardó en completarse.


En la pestaña **Headers** podemos observar detalles como la URL solicitada, el método HTTP usado(GET, POST, PUT, DELETE) y el código de estado para saber si la solicitud fue exitosa (`200 OK`) o si hubo un error (`404 Not Found`, `500 Internal Server Error`, etc.). Es importante que tengas en cuenta que en la pestaña **Red** del navegador, no todas las solicitudes provienen de JavaScript. Algunas son automáticas, como cargar imágenes, hojas de estilo o scripts. Usa los filtros **("XHR" o "Fetch")** para ver solo las solicitudes hechas dinámicamente por tu código, como `fetch()` o `XMLHttpRequest`.

> 💡 Ten en cuenta que aunque todos los navegadores modernos (Chrome, Firefox, Edge, Safari) ofrecen herramientas de inspección muy similares, puede haber **pequeñas diferencias en los nombres o en la disposición de las pestañas**.  Sin embargo, los conceptos que aprendiste aquí aplican en todos los casos.


El **Inspector de herramientas de desarrollo** del navegador es uno de los aliados más poderosos que vas a tener como desarrollador web. Dentro de él, la pestaña **"Red"** te permite ver, entender y corregir cómo viajan los datos entre tu página y los servidores.

Ahora que conoces esta herramienta, te invitamos a abrir cualquier sitio web, explorar el inspector, entrar en la pestaña **Network** y observar qué solicitudes se realizan, qué datos llegan, y qué errores podrían aparecer.


## ¿Listo para demostrar que ya ves la web como un pro? 😎

Responde estas preguntas para poner a prueba lo que aprendiste sobre cómo depurar solicitudes de API en el navegador:

**¿Cuál de las siguientes opciones describe mejor lo que ves en la pestaña "Red" (Network) del Inspector?**
- [ ] Los elementos gráficos y su estilo.
- [ ] Las solicitudes HTTP que la página realiza y sus respuestas.
- [ ] Los errores de JavaScript en el código.
- [ ] La estructura jerárquica del HTML.

**¿Qué tipo de solicitudes te interesa filtrar si quieres ver las que hace JavaScript dinámicamente?**
- [ ] Document
- [ ] Img
- [ ] XHR o Fetch
- [ ] Stylesheet

**¿Dónde puedes ver el contenido real (por ejemplo, un JSON) que el servidor respondió?**
- [ ] En la pestaña Headers.
- [ ] En la pestaña Preview.
- [ ] En la pestaña Response.
- [ ] En la pestaña Timing.

**Si ves un error `404 Not Found` en una solicitud, ¿qué significa?**
- [ ] Que el servidor tardó demasiado en responder.
- [ ] Que la URL solicitada no existe en el servidor.
- [ ] Que el navegador bloqueó la solicitud.
- [ ] Que los datos llegaron incompletos.

**¿Cuál de las siguientes afirmaciones es correcta?**
- [ ] Todas las solicitudes que ves en la pestaña Red son hechas manualmente por JavaScript.
- [ ] Solamente las solicitudes de tipo XHR o Fetch suelen ser iniciadas por JavaScript.
- [ ] La pestaña "Red" muestra únicamente errores de red.
- [ ] La pestaña "Console" sirve para ver las solicitudes HTTP.



