## Sitemaps

On regular WordPress sites, Yoast will generate XML sitemaps automatically. By decoupling, Yoast no longer has control over generating sitemaps, and they instead have to be generated each build along with the pages.

By default, **all published pages and posts** are included in the sitemap. Even if a page is restricted from indexing, it will still appear in the sitemap. To restrict the page from indexing, the page includes an appropriate meta tag (see [meta data section](seo/meta.md)).

### Location

By default, the sitemap will be split up into a **sitemap index** and individual **sitemaps**. The locations of these are:

- Sitemap Index `/sitemap-index.xml`
- Sitemap 0 (always included) `/sitemap-0.xml`
- Sitemap N `/sitemap-n.xml`

The sitemap index lists the location of each individual sitemap. By default, there will only be one sitemap, `sitemap-0.xml`. On sufficiently large sites, the sitemap may be split up into multiple to decrease the file size of any single sitemap.

This is very similar to how Yoast operates, which uses a sitemap index and splits up pages and posts into their respective sitemaps.

### Elements

In the sitemap index, each individual sitemap's location is simply listed in its own `sitemap` and `loc` element:

```xml
<sitemapindex>
  <sitemap>
    <loc>https://www.esquiredigital.com/sitemap-0.xml</loc>
  </sitemap>
  <sitemap>
    <loc>https://www.esquiredigital.com/sitemap-1.xml</loc>
  </sitemap>
</sitemapindex>
```

In actual sitemap files, the pages are listed in a `urlset` element:

```xml
<urlset>
  <url>
    <loc>https://www.esquiredigital.com/law-firm-marketing/</loc>
    <lastmod>2021-06-24T21:21:01.000Z</lastmod>
  </url>
  <url>
    <loc>https://www.esquiredigital.com/ask-a-question/</loc>
    <lastmod>2021-06-17T17:53:00.000Z</lastmod>
  </url>
  <url>
    <loc>https://www.esquiredigital.com/text-us/</loc>
    <lastmod>2021-06-21T18:51:06.000Z</lastmod>
  </url>
  <url>
    <loc>https://www.esquiredigital.com/free-audit-report/</loc>
    <lastmod>2021-06-17T18:18:35.000Z</lastmod>
  </url>
  <!-- And so on for each page -->
</urlset>
```

Each page gets its own `url` element. Inside, the URL of the page is listed as its location in the `loc` element. The only other element included by default is the `lastmod`, or the date the page was last modified. This is generated by looking at the page/post's last published date in WordPress.

There are many other elements that can be included in a sitemap. However, because companies have exploited their purposes to get pages indexed more frequently, Google has started ignoring all but the `lastmod` element. If this date is misrepresented, they will begin to ignore this element in the sitemap as well. For more information, see Google's official [documentation](https://developers.google.com/search/docs/advanced/sitemaps/build-sitemap?hl=en&visit_id=637604969287724171-3447187709&rd=1) on this issue.

### Automatic Submission

Sites use the plugin [netlify-plugin-submit-sitemap](https://github.com/cdeleeuwe/netlify-plugin-submit-sitemap#readme) to submit the sitemap to search engines on succesful builds. If a build fails, the sitemap will not be submitted to search engines. Currently, the sitemap will be submitted to:

- Google
- Bing
- Yandex

This ensures that Google and other search engines know about the freshest sitemap. DuckDuckGo, another very popular search engine, unforutnately does not have an API for submitting sitemaps for review.

## Robots.txt

The robots file communicates important information to web crawlers, and is usually one of the first stops for crawlers. Our robots files are fairly simple, and contain these fields by default:

```txt
User-agent: *
Allow: /
Disallow: /wp-admin
Sitemap: https://www.esquiredigital.com/sitemap-index.xml
Host: https://www.esquiredigital.com
```

Most importantly, it directs crawlers to the sitemap using the `sitemap` field, and blocks crawlers from accidentally navigating to the WordPress dashboard.
