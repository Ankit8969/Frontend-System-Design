# Web Vitals 
- Optimizing for quality of user experience is key to the long-term success of any site on the web. Whether you're a business owner, marketer, or developer, Web Vitals can help you quantify the experience of your site and identify opportunities to improve.

## Core Web Vitals

- Core Web Vitals are the subset of Web Vitals that apply to all web pages, should be measured by all site owners, and will be surfaced across all Google tools. Each of the Core Web Vitals represents a distinct facet of the user experience, is measurable in the field, and reflects the real-world experience of a critical user-centric outcome.

- The current set focuses on three aspects of the user experience—loading, interactivity, and visual stability—and includes the following metrics (and their respective thresholds):
![largest-contentful-paint-ea2e6ec5569b6](https://github.com/user-attachments/assets/223978b8-b0f7-4d94-9a8c-d67e7b50ae7b)
![inp-thresholds](https://github.com/user-attachments/assets/b57af3e9-35dc-4ed3-8168-5520f8a3d330)
![cumulative-layout-shift-t-5d49b9b883de4](https://github.com/user-attachments/assets/65edd441-b5a4-495b-b61a-e6899a6149ae)

- ***Largest Contentful Paint (LCP)***: measures loading performance. To provide a good user experience, LCP should occur within 2.5 seconds of when the page first starts loading.
- ***Interaction to Next Paint (INP)***: measures interactivity. To provide a good user experience, pages should have a INP of 200 milliseconds or less.
- ***Cumulative Layout Shift (CLS)***: measures visual stability. To provide a good user experience, pages should maintain a CLS of 0.1. or less.


- To ensure you're hitting the recommended target for these metrics for most of your users, a good threshold to measure is the 75th percentile of page loads, segmented across mobile and desktop devices.

## User-centric performance metrics
We've all heard how important performance is. But when we talk about performance, and about making websites "fast", what specifically do we mean?

## The truth is that performance is relative:
- A site might be fast for one user (on a fast network with a powerful device) but slow for another user (on a slow network with a low-end device).
- Two sites may finish loading in the exact same amount of time, yet one may seem to load faster (if it loads content progressively rather than waiting until the end to display anything).
- A site might appear to load quickly but then respond slowly (or not at all) to user interaction.

# What is LCP?
LCP reports the render time of the largest image, text block, or video visible in the viewport, relative to when the user first navigated to the page.

## What is a good LCP score?

![good-lcp-values](https://github.com/user-attachments/assets/f6704466-b209-48a6-ab18-2980f5b9be5c)

## What elements are considered?
As currently specified in the Largest Contentful Paint API, the types of elements considered for Largest Contentful Paint are:

- "img" elements (the first frame presentation time is used for animated content such as GIFs or animated PNGs)
- "image" elements inside an "SVG" element
- "video" elements (the poster image load time or first frame presentation time for videos is used—whichever is earlier)
- An element with a background image loaded using the url() function, (as opposed to a CSS gradient)
- Block-level elements containing text nodes or other inline-level text element children



# Cumulative Layout Shift (CLS)
Unexpected layout shifts can disrupt the user experience in many ways, from causing them to lose their place while reading if the text moves suddenly, to making them click the wrong link or button. In some cases, this can do serious damage.

[layout-instability2.webm](https://github.com/user-attachments/assets/cd48176d-a68f-4f33-aeb3-f9d42fd88f2c)

## What is CLS?
CLS is a measure of the largest burst of layout shift scores for every unexpected layout shift that occurs during the entire lifecycle of a page.
A layout shift occurs any time a visible element changes its position from one rendered frame to the next

![good-cls-values](https://github.com/user-attachments/assets/511a0073-c5fa-437a-b6ab-2134aca765bf)

# Interaction to Next Paint (INP)

- Good responsiveness means that a page responds quickly to interactions. When a page responds to an interaction, the browser presents visual feedback in the next frame that it paints. Visual feedback tells you if, for example, an item you add to an online shopping cart is indeed being added, whether a mobile navigation menu has opened, if a login form's contents are being authenticated by the server, and so forth.
- Some interactions naturally take longer than others, but for especially complex interactions, it's important to quickly present some initial visual feedback to tell the user that something is happening. The next frame that the browser will paint is the earliest opportunity to do this.
- Therefore, the intent of INP is not to measure all the eventual effects of an interaction—such as network fetches and UI updates from other asynchronous operations)—but the time that the next paint is being blocked. By delaying visual feedback, users may get the impression that the page is not responding quickly enough, and INP was developed to help developers measure this part of the user experience.

![videoframe_6165](https://github.com/user-attachments/assets/a54f2ca0-5141-4ea8-8789-82fb9bd0c461)


## What is INP?
- INP is a metric that assesses a page's overall responsiveness to user interactions by observing the latency of all click, tap, and keyboard interactions that occur throughout the lifespan of a user's visit to a page. The final INP value is the longest interaction observed, ignoring outliers.

![inp-desktop-v2](https://github.com/user-attachments/assets/d047931e-61fe-4289-bbaf-00df40e4befd)













