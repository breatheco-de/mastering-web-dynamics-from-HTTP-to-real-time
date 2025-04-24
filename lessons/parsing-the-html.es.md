---
title: "Analizando el HTML: Cómo el Navegador Construye la Página que Ves"
description: >
  Descubre cómo el navegador interpreta el HTML recibido desde el servidor para construir la estructura visual de una página web. Esta lección explica cómo se forma el DOM, qué bloquea su análisis y por qué este paso es clave en la carga de cualquier sitio.
tags: ["HTML", "DOM", "navegador", "estructura web", "web", "renderizado"]
---

## El navegador como arquitecto

Una vez que el servidor envía **la respuesta** con el contenido de la página (por ejemplo, un archivo HTML), el navegador comienza su trabajo, recibiendo ese contenido y lo **analiza línea por línea para construir la estructura visual de la página** que vas a ver en tu pantalla. 

Imagina que el navegador es un arquitecto que recibe los planos de una casa (el HTML). Lee las instrucciones desde el inicio, interpreta las partes clave (estructura, decoración, funciones), y va montando cada elemento en su lugar. Si los planos tienen adjuntos como imágenes, manuales técnicos o permisos (hojas de estilo o scripts), el arquitecto necesita revisarlos antes de seguir.

Este paso se conoce como **análisis del HTML**, y da origen a una estructura interna llamada **DOM** (Modelo de Objeto del Documento), que es esencial para cualquier página web.

### DOM: la estructura invisible de cada página

El DOM es una representación en forma de árbol de todos los elementos HTML que componen la página. Por ejemplo, un archivo como este:

```html
<html>
  <head><title>Mi sitio</title></head>
  <body><h1>Bienvenido</h1><p>Hola mundo</p></body>
</html>
```

Se transforma en algo así dentro del navegador:

```css
html
├── head
│   └── title
└── body
    ├── h1
    └── p
```

El navegador **construye este árbol mientras analiza el HTML**, y luego lo utiliza para mostrar visualmente la página.


### ¿Cómo lo analiza?

1. Empieza por el `<html>` y baja línea por línea.

2. Lee primero el `<head>`, donde suele encontrar:

    - Títulos (`<title>`)

    - Hojas de estilo (`<link>`)

    - Scripts (`<script>`)

Luego pasa al `<body>`, que contiene lo que se verá en pantalla: texto, imágenes, botones, etc.

### ¿Qué puede bloquear el análisis?

Hay cosas que pueden detener o retrasar el proceso:

- Hojas de estilo externas (`<link rel="stylesheet">`): El navegador no sigue analizando hasta descargarlas, porque afectan el diseño.
- Scripts sin atributo `defer` o `async`: Si encuentra un `<script>` tradicional, lo ejecuta antes de seguir leyendo, lo que puede frenar el análisis general.

> Por eso es tan importante optimizar el orden en que se cargan recursos: para que el navegador pueda construir la página lo más rápido posible.


```mermaid
sequenceDiagram
    participant Navegador

    Navegador->>Navegador: Recibe HTML desde el servidor
    Navegador->>Navegador: Analiza el <head> (estilos, scripts)
    Navegador->>Navegador: Analiza el <body> (contenido visual)
    Navegador->>Navegador: Construye el DOM
    Navegador->>Pantalla: Muestra la página al usuario
```

