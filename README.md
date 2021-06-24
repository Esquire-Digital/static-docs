# Overview

Esquire Digital Static is a static site generator that generates secure, cheap and most of all performant static sites from a headless content management system (CMS). By default, the generator is set up to fetch data from a headless WordPress install, but can be easily modified to query data from any headless CMS that Gatsby.js supports natively. In fact, given enough modification, potentially *any* CMS or data source could be queried by this generator.

## Motivation

Given the rapid evolution of the web, WordPress sites can no longer meet the requirements to remain in the top percentiles of performance. Users now expect a much faster web browsing experience, and are quick to click off sites that have noticeable loading times, increasing bounce rate and impacting conversions. While it is certainly possible to force a WordPress site to be performant enough to score high on current metrics, maintaining this across many client sites quickly becomes a full time job. If the metrics change or being stricter, as they always have, it may become impossible to build an adequately performant site. Instead, a performance focused framework should be used to develop websites, using WordPress only for content management.

Further, Google announced in mid-year 2020 that they would officially be considering the [core web vitals](https://support.google.com/webmasters/answer/9205520?hl=en) (CWV) of a website when ranking them in search results. Because SEO efficacy is paramount to our business and our clients, it is clear that WordPress alone no longer fits the bill. To remain competitive, we need more control over the performance and CWV values of our sites.

![Pagespeed Comparison](/_media/pagespeed.png)

Finally, our continued interest in creating award winning and complex designs necessitates the use of modern web technologies. By using [Gatsby.js](https://www.gatsbyjs.com), this generator can harness the power of React and thereby a living DOM to design truly stunning user experiences. The first client site to use this static generator, [Marrone Law](https://www.marronelaw.com), went on to be nominated for a [Webby Award](https://www.webbyawards.com/) and win a [Web Excellence Award](https://we-awards.com/).

## How It Works

### Headless WordPress

The generator works by reading content from a normal WordPress install, hosted by some provider remotely. This WordPress install is **headless**, which means it is not responsible for displaying content to the user. Typically, WordPress will dynamically render a page based on the content that is written in the backend. In this set up, WordPress is only used to manage content, which is then extracted and built into a static site. 

![CMS comparison](/_media/CMS.png)

### Problems With Dynamic Rendering

Traditionally, WordPress **dynamically renders** pages at the time of request. Every time a user visits a page, WordPress retrieves the content, styling, and other aspects of that page, combines it, and returns it as a web page. This results in a lot of time wasted; it takes time to patch together a page, and is done for every request. This can be mitigated by using clever caching techniques, and there are plugins that can help **pre-render** these pages so they are not produced each time they are requested. However, WordPress was simply designed to dynamically render pages, and these solutions have serious shortcomings, and become a hassle to maintain across many sites.

Making matters worse, if a single portion of a WordPress site breaks, *all* of the website will break. These incidents are commonly referred to as the white screen of death, and can be very difficult to debug. If WordPress is made headless, then a small bug will only affect content editing, and the front facing website will remain functional.

WordPress is also vulnerable to many security threats. Because the website's database and display lives in the same place, hackers or other bad actors can exploit many aspects of the website to gain unauthorized access or otherwise damage the integrity of the site. Attacks like [SQL injection](https://kinsta.com/blog/sql-injection/) should be a thing of the past, yet consistently affect many WordPress sites. While primitive attacks like these can be avoided, hackers are always ahead of the curve, and the only way to completely prevent security vulnerabilities is to do away with WordPress's dynamic rendering.

### Static Rendering

The opposite approach to dynamic rendering is **static rendering**. This means that all pages are only rendered once. Every time a user requests a page they are delivered an already built page. Every time a change is made in WordPress, pages that reflect those changes are rebuilt. If someone edits the page **Personal Injury** to become **Accidents and Injuries**, that page will be rebuilt to have the new content.

This effectively shifts the rendering step from each request to each time content is changed. This means that when changes are made to content, especially changes that affect a large portion of the site's pages, the site will not immediately reflect the changes. Instead, it will take a couple minutes (even up to 10 for large sites!) to build, optimize and publish new pages.

The benefits are well worth the wait. With static pages comes enhanced security; there is no database to manipulate and no backend to hack. Static pages remove the need for a web server, and can be served on ultra-fast [Content Delivery Networks](https://www.cloudflare.com/learning/cdn/what-is-a-cdn/) (CDNs). To make WordPress sites faster, assets are often moved to CDNs to speed up delivery times; with static sites, the whole site is delivered with a CDN!

Lastly, static sites are generated using state of the art web technologies, empowering developers to create the best user experiences possible. The static site generator used by Esquire Digital Static is [Gatsby.js](https://www.gatsbyjs.com), which prioritizes performance, SEO, and developer sanity. With it, we can generate blazing fast sites delivered at the edge, all while still managing content in a familiar WordPress dashboard.

### Putting It All Together

This type of web development can be a headache to understand. Here's the key takeaways:

  - **WordPress is no longer used to *display* content.** WordPress plugins, themes, and other front-facing components will no longer work. All of the front end is managed by the developers.
  - **WordPress works the same way to *manage* content.** Pages, custom fields, menus, and blog posts all function the same way to content editors. Esquire Digital Static builds the website from the content entered in WordPress.
  - **Changes are not immediate.** If a change is made to a page, it will take time to rebuild and publish the new version of the website.
  - **The result is fast and secure.** By removing WordPress as the middleman in displaying content, we can create extremely fast sites with features that are unachievable with a traditional WordPress install.