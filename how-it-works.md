## Headless WordPress

The generator works by reading content from a normal WordPress install, hosted by some provider remotely. This WordPress install is **headless**, which means it is not responsible for displaying content to the user. Typically, WordPress will dynamically render a page based on the content that is written in the backend. In this set up, WordPress is only used to manage content, which is then extracted and built into a static site.

![CMS comparison](/_media/CMS.png)

## Dynamic Rendering

Traditionally, WordPress **dynamically renders** pages at the time of request. Every time a user visits a page, WordPress retrieves the content, styling, and other aspects of that page, combines it, and returns it as a web page. This results in a lot of time wasted; it takes time to patch together a page, and is done for every request. This can be mitigated by using clever caching techniques, and there are plugins that can help **pre-render** these pages so they are not produced each time they are requested. However, WordPress was simply designed to dynamically render pages. As such, these solutions have serious shortcomings and become a hassle to maintain across many sites.

Making matters worse, if a single portion of a WordPress site breaks, _all_ of the website will break. These incidents are commonly referred to as the white screen of death, and can be very difficult to debug. If WordPress is made headless, then a small bug will only affect content editing, and the front facing website will remain functional.

WordPress is also vulnerable to many security threats. Because the website's database and display logic lives in the same place, hackers or other bad actors can exploit many aspects of the website to gain unauthorized access or otherwise damage the integrity of the site. Attacks like [SQL injection](https://kinsta.com/blog/sql-injection/) should be a thing of the past, yet consistently affect many WordPress sites. While primitive attacks like these can be avoided, hackers are always ahead of the curve, and the only way to completely prevent security vulnerabilities is to do away with WordPress's dynamic rendering.

## Static Rendering

The opposite approach to dynamic rendering is **static rendering**. This means that all pages are only rendered once. Every time a user requests a page they are delivered an already built page. Every time a change is made in WordPress, pages that reflect those changes are rebuilt. If someone edits the page **Personal Injury** to become **Accidents and Injuries**, that page will be rebuilt to have the new content.

This effectively shifts the rendering step from each request to each time content is changed. This means that when changes are made to content, especially changes that affect a large portion of the site's pages, the site will not immediately reflect the changes. Instead, it will take a couple minutes (even up to 10 for large sites!) to build, optimize and publish new pages.

The benefits are well worth the wait. With static pages comes enhanced security; there is no database to manipulate and no backend to hack. Static pages remove the need for a web server, and can be served on ultra-fast [Content Delivery Networks](https://www.cloudflare.com/learning/cdn/what-is-a-cdn/) (CDNs). To make WordPress sites faster, assets are often moved to CDNs to speed up delivery times; with static sites, the whole site is delivered with a CDN!

Lastly, static sites are generated using state of the art web technologies, empowering developers to create the best user experiences possible. The static site generator used by Esquire Digital Static is [Gatsby.js](https://www.gatsbyjs.com), which prioritizes performance, SEO, and developer sanity. With it, we can develop blazing fast sites delivered at the edge, all while still managing content in a familiar WordPress dashboard.

## Putting It All Together

This type of web development can be a headache to understand. Here's the key takeaways:

- **WordPress is no longer used to _display_ content.** WordPress plugins, themes, and other front-facing components will no longer work. All of the front end is managed by the developers.
- **WordPress works the same way to _manage_ content.** Pages, custom fields, menus, and blog posts all function the same way to content editors. Esquire Digital Static builds the website from the content entered in WordPress.
- **Changes are not immediate.** If a change is made to a page, it will take time to rebuild and publish the new version of the website.
- **The result is fast and secure.** By removing WordPress as the middleman in displaying content, we can create extremely fast sites with features that are unachievable with a traditional WordPress install.
