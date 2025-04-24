---
title: "Prioritizing Resource Requests: How the Browser Decides What to Load First"
description: >
    Explore how the browser manages resources referenced in an HTML page (such as stylesheets, images, and scripts). Learn what gets loaded first, what can block rendering, and how to optimize the delivery of visual content.
tags: ["browser", "web resources", "HTML", "loading", "priority", "web performance"]
---

<todo>This lesson is not about parsing HTML or the visual part of rendering a website, here we want to focus on HTTP and loading resources becasue understanding this is amazing for debugging web. We are asumming you already know or read about what HTTP is, understands requests and the typical webste and its structure, actually the first time a website is rendered is already covere on another lesson</todo>

<todo>
 - Add a secion about "onload" and how it use used or how important it is to javascript
- Async and defer comes first than onload
</todo>

Once the browser has finished parsing the HTML and building the DOM, its work is far from over. It now needs to **load all the additional resources** mentioned on the page to ensure it looks and functions correctly. These resources include: Stylesheets (CSS), images, JavaScript scripts, custom fonts, videos, or other multimedia files.

The question is, does it load them all at the same time? What happens if there are too many? This is where **resource prioritization** comes into play.

The browser detects various tags in the HTML that indicate external resources:

- `<link>` → CSS
- `<img>` → images
- `<script>` → JavaScript
- `<video>`, `<audio>`, `<source>` → media
- `@font-face` → custom fonts

Each of these resources requires an **additional request** to be downloaded. But the browser doesn’t load them in just any order; it **prioritizes what is essential to display the page correctly**.

### What gets loaded first?

Browsers follow certain priority rules:

1. **CSS first:** Stylesheets block the rendering of the page because they affect how it looks. The browser won’t display anything until the CSS is ready.

2. **JavaScript after CSS:** Scripts can also block rendering if they are in the `<head>` and don’t use `defer` or `async`.

3. **Images and other visual resources:** These are loaded in the background, once the main content is being processed.

### Why does this priority matter?

Because it **directly impacts the page load time**. If the browser takes too long to load a critical resource (like a blocking CSS or a large script), the user will see a blank screen for longer.

Knowing this allows you to:

- Optimize the order of your HTML code
- Use attributes like `defer`, `async`, `loading="lazy"`
- Improve the loading experience for your users

If we compare this process to a professional kitchen, it would look something like this:

- The chef first heats the pan (CSS).
- Then starts preparing the base ingredients (HTML + visual structure).
- Meanwhile, others bring the secondary ingredients (images, videos, scripts).
- Only when everything is in place, the dish is presented.

The browser works the same way: **it loads the essentials first, and the decorative elements later**.

```mermaid
flowchart TD
        A[The browser finishes reading the HTML] --> B[Detects links to external resources]
        B --> C{Is it CSS?}
        C -- Yes --> D[Load immediately and block rendering]
        C -- No --> E{Is it JS in <head>?}
        E -- Yes --> F[Execute before proceeding]
        E -- No --> G{Is it an image or multimedia resource?}
        G -- Yes --> H[Load in the background]
        H --> I[Display page to the user]
        F --> I
        D --> I
```

<todo>
 - Explain "above the fold" and 'below the fold" y como se relaciona con loading=lazy y como esto impacta al usuario
 - Sugiere que se piquen los scripts y css para separar above y below the fold.
</todo>

<code> Add useful debugging cases were this information is important </code>
