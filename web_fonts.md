# Optimize web fonts
- Web fonts can impact page performance at both load time and rendering time. Large font files can take a while to download and negatively affect First Contentful Paint (FCP), while the incorrect font-display value could cause undesirable layout shifts that contribute to a page's Cumulative Layout Shift (CLS).
- Before optimizing web fonts can be discussed, knowing how they're discovered by the browser can be helpful, so that you can understand how CSS prevents the retrieval of unnecessary web fonts in certain situations.

```
@font-face {
  font-family: "Open Sans";
  src: url("/fonts/OpenSans-Regular-webfont.woff2") format("woff2");
}
```

```
h1 {
  font-family: "Open Sans";
}
```

### Optimizing web fonts is crucial for improving website performance, especially in terms of loading speed and rendering time. Here are effective strategies to optimize web fonts:
- Choose Modern Formats
  - Use modern font formats like WOFF2 (Web Open Font Format 2) for better compression and faster loading.
  - Fallback to WOFF or other formats for older browser support.
- Subset Fonts
  - Include only the characters you need by creating subsets of the font (e.g., Latin, Cyrillic).
  - Tools like Font Squirrel or Google Fonts Subsetter can help.
- Use System Fonts When Possible
  - For non-branded text like body content, consider using system fonts to avoid loading external resources.
  - Examples: Arial, Helvetica, Times New Roman.

- Implement Font Display
  - Use the font-display property in CSS to control how fonts are loaded and displayed:
```
@font-face {
  font-family: 'MyFont';
  src: url('myfont.woff2') format('woff2');
  font-display: swap;
}
```
```
swap: Displays fallback text while the font loads, preventing blank text.
```

- Lazy-Load Fonts
  - Load fonts only when needed, such as when the user scrolls to a specific section.
  - Tools like Typekit or dynamic import in JavaScript can help.

- Host Fonts Locally
  - Download and serve fonts from your server instead of relying on third-party CDNs to reduce DNS lookups.

- Enable Compression
  - Use Gzip or Brotli compression on font files to reduce size before transferring them to the browser.

- Preload Fonts
  - Use the <link rel="preload"> tag to prioritize font loading in the browser:
```
<link rel="preload" href="myfont.woff2" as="font" type="font/woff2" crossorigin="anonymous">
```

- Cache Fonts
  - Use long-term caching by setting appropriate HTTP cache headers so fonts are downloaded only once.
```
Cache-Control: public, max-age=31536000
```

- Avoid Excessive Font Variants
  - Limit the number of weights, styles, and sizes to only what is necessary (e.g., Regular, Bold).

- Reduce Unused CSS
  - Remove unused @font-face rules and styles that load unnecessary fonts.

- Monitor and Optimize
  - Use tools like Google Lighthouse, WebPageTest, or FontForge to analyze and improve font performance.
  - By applying these techniques, you can significantly reduce font loading times, improve rendering performance, and enhance the user experience.
