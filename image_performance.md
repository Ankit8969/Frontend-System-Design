# Image performance
Images are often the heaviest and most prevalent resource on the web. As a result, optimizing images can significantly improve performance on your website. In most cases, optimizing images means reducing the network time by sending fewer bytes, but you can also optimize the amount of bytes sent to the user by serving images that are properly sized for the user's device.

```
Images can be added to a page using the <img> or <picture> elements, or the CSS background-image property.
```

Handling image performance effectively can significantly improve load times, reduce data usage, and enhance user experience on websites. Here are some best practices to optimize image performance:
## Use Appropriate Image Formats
- JPEG: Good for photos with complex colors. Use for high-quality images that don’t require transparency.
- PNG: Supports transparency and is best for images with sharp edges or limited colors (e.g., logos).

## WebP/AVIF: Modern formats offering better compression and quality, but check browser support.
- SVG: Ideal for vector graphics, such as icons or logos, since they scale without loss of quality.
## Resize Images for Each Device
Serve images in sizes appropriate to the device. Use multiple resolutions and the ```<img srcset>``` attribute or CSS background-image with media queries to serve smaller images to mobile devices.
Tools like Cloudinary or Imgix can dynamically resize and serve images based on device resolution.
## Use Responsive Images
Use the ```<picture>``` element or srcset and sizes attributes to specify different images for different screen resolutions and sizes.
```
<picture>
    <source srcset="image-small.jpg" media="(max-width: 600px)">
    <source srcset="image-large.jpg" media="(min-width: 601px)">
    <img src="image.jpg" alt="Example image">
</picture>
```

## Implement Lazy Loading
Load images only when they are about to enter the viewport. Use the loading="lazy" attribute on ```<img>``` tags:
```
<img src="image.jpg" loading="lazy" alt="Lazy loaded image">
```
This reduces initial page load time and saves bandwidth for users who may not scroll through the entire page.

## Compress Images
Reduce file sizes using tools like TinyPNG, ImageOptim, or Adobe Photoshop’s “Save for Web” feature. For large projects, automate compression with build tools like Webpack, Gulp, or dedicated image optimization services.
### Compression methods:
- Lossy: Reduces file size significantly but may lower quality slightly (e.g., JPEG).
- Lossless: Retains original quality but achieves smaller reductions in file size (e.g., PNG).

## Use a Content Delivery Network (CDN)
- Host images on a CDN to ensure fast delivery from a server closest to the user. This reduces latency and improves load times, especially for global audiences.

 ## Set Correct Dimensions
Explicitly set width and height attributes on ```<img>``` tags to prevent layout shifts (cumulative layout shift or CLS). This lets browsers reserve space for images as they load.

## Implement Image Caching
Use caching headers to ensure images are stored in the browser cache. Set long expiration times for images that don’t change often to avoid re-downloading on repeat visits.

## Optimize Background Images in CSS
Use CSS media queries to load background images only at certain breakpoints. Lazy-load background images by dynamically setting the background-image property through JavaScript or CSS classes.

## Use Progressive Loading for JPEGs
Use progressive JPEGs, which load a low-quality version of the entire image initially, then gradually improve quality. This can give users a preview while the image fully loads.

## Consider Using Image Sprites
For small icons or UI elements, combine multiple images into a single “sprite” image and use CSS to display specific parts. This reduces the number of HTTP requests.
By implementing these strategies, you can enhance image performance, reduce page load times, and provide a smoother experience for users across all devices.





