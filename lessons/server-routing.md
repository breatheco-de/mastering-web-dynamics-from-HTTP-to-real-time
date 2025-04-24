---
title: "Server Routing: How to Reach the Right Resource"
description: >
    Discover how web servers interpret a URL's path to deliver the correct resource. This lesson explains server request routing with a clear analogy and diagrams to visualize the process.
tags: ["routing", "web server", "URL", "HTTP", "resources", "web"]
---

<todo> Agregar un parrafo aqui para introduct la lectura, por ejemplo; "Usualy servers exist with the purpose of answer other clients requests, for example: Someone somwhere is trying to access a website example.com. Be example.com is not an IP address, and servers can only be addressed using IP addresses, and that is why clents use DNS's to first find the IP of the server they want to request, and then we forwward the request to that IP, you can read more about the whole process in <a href="#">resolving dns</a> </todo>

## Which Door Do We Go To?

Once the browser has the server's IP address (thanks to DNS), it sends an **HTTP request** to access a specific resource. For example, if the user types:

```text
https://www.example.com/about
```
The browser connects to the server at `www.example.com` and says: “Hello, I want to see the `/about` page.”

This is where the **server router** comes into play, analyzing the URL and deciding **which resource to deliver**. It's like a receptionist who listens to your request and directs you to the appropriate department:

- `/about` → Information page
- `/contact` → Contact form
- `/products` → Catalog

If the route doesn't exist, the server responds with something like:

```text
404 Not Found - That resource was not found!
```

Imagine a store with many departments. When you make a request (“I want to see the products”), the system has to take your request to the **correct shelf**. If such a shelf doesn't exist, they tell you: “We don't have that.”

```mermaid
sequenceDiagram
        participant Browser
        participant Server

        Browser->>Server: GET /about
        Server->>Server: Analyze the route
        Server-->>Browser: Respond with the /about page
```

Understanding routing is key to knowing how websites organize their content and how servers intelligently respond to each visit. It's like having a good customer service system, knowing which counter to direct each request to, or how to respond if something is unavailable.
