# Assist the browser with resource hints
- Resource hints can help developers further optimize page load time by informing the browser how to load and prioritize resources
- An initial set of resource hints such as ***preconnect*** and ***dns-prefetch*** were the first to be introduced. Over time, however, ***preload***, and the Fetch Priority API have followed to provide additional capabilities.
- Resource hints instruct the browser to perform certain actions ahead of time that could improve loading performance. Resource hints can perform actions such as performing early DNS lookups, connecting to servers ahead of time, and even fetching resources before the browser would ordinarily discover them.

## preconnect
The preconnect hint is used to establish a connection to another origin from where you are fetching critical resources. 
For example, you may be hosting your images or assets on a CDN or other cross-origin:

```
<link rel="preconnect" href="https://example.com">
```

By using preconnect, you anticipate that the browser plans to connect to a specific cross-origin server in the very near future, and that the browser should open that connection as soon as possible, ideally before waiting for the HTML parser or preload scanner to do so.

If you have a large amount of cross-origin resources on a page, use preconnect for those resources which are the most critical to the current page.

A common use case for preconnect is Google Fonts. Google Fonts recommends that you preconnect to the https://fonts.googleapis.com domain that serves the @font-face declarations and to the https://fonts.gstatic.com domain that serves the font files.

```
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
```

## dns-prefetch
While opening connections to cross-origin servers early can significantly improve initial page load time, it may not be either reasonable or possible to establish connections to many 
cross-origin servers at once. If you're concerned that you may be overusing preconnect, a much less costly resource hint is the dns-prefetch hint.


Per its name, dns-prefetch doesn't establish a connection to a cross-origin server, but rather just performs the DNS lookup for it ahead of time. A DNS lookup occurs when a domain 
name is resolved to its underlying IP address. While layers of DNS caches at the device and network levels help to make this a generally fast process, it still takes some amount of time.


```
<link rel="dns-prefetch" href="https://fonts.googleapis.com">
<link rel="dns-prefetch" href="https://fonts.gstatic.com">
```



## preload
The preload directive is used to initiate an early request for a resource required for rendering the page:

```
<link rel="preload" href="/lcp-image.jpg" as="image">
```

- Preload directives should be limited to late-discovered critical resources. The most common use cases are font files, CSS files fetched through @import declarations, 
or CSS background-image resources that are likely to be Largest Contentful Paint (LCP) candidates. In such cases, these files wouldn't be discovered by the preload scanner as the 
resource is referenced in external resources.


<img width="953" alt="image" src="https://github.com/user-attachments/assets/99e81a34-f70f-4c57-83db-df6e9c0364f0">


Similarly to preconnect, the preload directive requires the crossorigin attribute if you are preloading a CORS resource—such as fonts. If you don't add the crossorigin attribute—or add it for non-CORS requests—then the resource is downloaded by the browser twice, wasting bandwidth that could have been better spent on other resources.


```
<link rel="preload" href="/font.woff2" as="font" crossorigin>
```

## prefetch
The prefetch directive is used to initiate a low priority request for a resource likely to be used for future navigations:
```
<link rel="prefetch" href="/next-page.css" as="style">
```


## Fetch Priority API
You can use the Fetch Priority API through its fetchpriority attribute to increase the priority of a resource. You can use the attribute with <link>, <img>, and <script> elements.
```
<div class="gallery">
  <div class="poster">
    <img src="img/poster-1.jpg" fetchpriority="high">
  </div>
  <div class="thumbnails">
    <img src="img/thumbnail-2.jpg" fetchpriority="low">
    <img src="img/thumbnail-3.jpg" fetchpriority="low">
    <img src="img/thumbnail-4.jpg" fetchpriority="low">
  </div>
</div>
```





















