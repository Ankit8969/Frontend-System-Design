# Welcome to Learn Performance!
Web performance is a crucial aspect of web development that focuses on the speed at which pages load, as well as how responsive they are to user input. When you optimize your website for performance, you're giving users a better experience. Better user experiences go a long way toward helping you achieve the goals you had in mind for your website.
- General HTML performance considerations
- Understanding the critical path
- Optimize resource loading
- Assist the browser with resource hints
- Image performance
- Video performance
- Optimize web fonts
- Code-split JavaScript
- Lazy load images and <iframe> elements
- Prefetching, prerendering, and service worker precaching
- An overview of web workers
- A concrete web worker use case


## General HTML performance considerations
- Minimize redirects: It means using a url shorter, redirecting from one to another so that it may slow down your website.

- Redirects slow down page load speed because it requires the browser to make an additional HTTP request at the new location to retrieve the resource. There are two types of redirects:
1. Same-origin redirects that occur entirely within your origin. These types of redirects are completely within your control, as the logic for managing them resides entirely on your web server.
2. Cross-origin redirects that are initiated by another origin. These types of redirects are typically out of your control.
- Cache HTML responses
- Measure server response times
- Compression


## Understanding the critical path
The critical rendering path refers to the steps involved until the web page starts rendering in the browser. To render pages, browsers need the HTML document itself as well as all the critical resources necessary for rendering that document.
- In this module, however, we'll look more at what the browser does after it downloads the HTML document in order to render the page.

### Progressive rendering
Progressive rendering is a technique in web development to enhance user experience by displaying parts of a webpage or app as they load, instead of waiting for the entire page to be ready. This approach is particularly useful for improving performance on slower networks or devices, allowing users to interact with content incrementally rather than waiting for a full render.

### The (critical) rendering path
The sequence of steps the browser takes before performing that initial render is known as the critical rendering path.

### The rendering path involves the following steps:
- Constructing the Document Object Model (DOM) from the HTML.
- Constructing the CSS Object Model (CSSOM) from the CSS.
- Applying any JavaScript that alters the DOM or CSSOM.
- Constructing the render tree from the DOM and CSSOM.
- Perform style and layout operations on the page to see what elements fit where.
- Paint the pixels of the elements in memory.
- Composite the pixels if any of them overlap.
- Physically draw all the resulting pixels to screen.

![image](https://github.com/user-attachments/assets/ade1fbc5-cce5-4623-922b-e6751a71545e)

### What resources are on the critical rendering path?
The browser needs to wait for some critical resources to download before it can complete the initial render. These resources include:
- Part of the HTML.
- Render-blocking CSS in the <head> element.
- Render-blocking JavaScript in the <head> element.

A key point is that the browser processes HTML in a streaming fashion. As soon as the browser gets any portion of a page's HTML, the browser starts processing it. The browser can then—and often does—decide to render it well before receiving the rest of a page's HTML.
Importantly, for the initial render, the browser will not typically wait for:
- All of the HTML.
- Fonts.
- Images.
- Non-render-blocking JavaScript outside of the <head> element (for example, <script> elements placed at the end of the HTML).
- Non-render-blocking CSS outside of the <head> element, or CSS with a media attribute value that does not apply to the current viewport.


- The <head> element is key to processing the critical rendering path.
- Optimizing the <head> element's contents is a key aspect of web performance.
```
To understand the critical rendering path for now, though, you only need to know that the <head> element contains metadata about the page and its resources, but no actual content the user can see.
Visible content is contained within the <body> element that follows the <head> element. Before the browser can render any content, it needs both the content to render as well as the metadata about
how to render it.

However, not all resources referenced in the <head> element are strictly necessary for the initial page render, so the browser only waits for those that are. To identify which resources are in the
critical rendering path, you need to understand render-blocking and parser-blocking CSS and JavaScript.
```

### Render-blocking resources
Some resources are deemed so critical that the browser pauses page rendering until it has dealt with them. CSS falls into this category by default.

When a browser sees CSS—whether it's inline CSS in a <style> element, or an externally referenced resource specified by a 'link rel=stylesheet href="..."'
element—the browser avoids rendering any more content until it has completed downloading and processing that CSS.















