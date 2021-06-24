## Introduction

Esquire Digital Static is a static site generator that generates secure, cheap and most of all performant static sites from a headless content management system (CMS). By default, the generator is set up to fetch data from a headless WordPress install, but can be easily modified to query data from any headless CMS that Gatsby.js supports natively. In fact, given enough modification, potentially _any_ CMS or data source could be queried by this generator.

## Motivation

Given the rapid evolution of the web, WordPress sites can no longer meet the requirements to remain in the top percentiles of performance. Users now expect a much faster web browsing experience, and are quick to click off sites that have noticeable loading times, increasing bounce rate and impacting conversions. While it is certainly possible to force a WordPress site to be performant enough to score high on current metrics, maintaining this across many client sites quickly becomes a full time job. If the metrics change or being stricter, as they always have, it may become impossible to build an adequately performant site. Instead, a performance focused framework should be used to develop websites, using WordPress only for content management.

Further, Google announced in mid-year 2020 that they would officially be considering the [core web vitals](https://support.google.com/webmasters/answer/9205520?hl=en) (CWV) of a website when ranking them in search results. Because SEO efficacy is paramount to our business and our clients, it is clear that WordPress alone no longer fits the bill. To remain competitive, we need more control over the performance and CWV values of our sites.

![Pagespeed Comparison](/_media/pagespeed.png)

Finally, our continued interest in creating award winning and complex designs necessitates the use of modern web technologies. By using [Gatsby.js](https://www.gatsbyjs.com), this generator can harness the power of React and thereby a living DOM to design truly stunning user experiences. The first client site to use this static generator, [Marrone Law](https://www.marronelaw.com), went on to be nominated for a [Webby Award](https://www.webbyawards.com/) and win a [Web Excellence Award](https://we-awards.com/).
