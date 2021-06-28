### Information Tags

Yoast exposes _a lot_ of meta information that we include on pages. For more information on Open Graph, the protocol observed by social media like Twitter and Facebook, visit their official [documentation](https://ogp.me/). These include:

- Meta title `title`
- Meta description `description`
- Title for Facebook `og:title`
- URL of page for Facebook `og:url`
- Description for Facebook `og:description`
- Page type for Facebook `og:type`
- Thumbnail for Facebook embeds `og:image`
- Thumbnail for Twitter embeds `twitter:image`
- Summary for Twitter embeds `twitter:card`
- Title for Twitter embeds (just the meta title) `twitter:title`
- Description for Twitter embeds (just the meta description) `twitter:description`
- Domain for Twitter `twitter:domain`

### Robots Tag

When restricting a page from indexing, Yoast sends a `noindex, nofollow` value for use in the robots meta tag. On every page, a robots meta tag is included with the intended functionality by Yoast. For example:

```html
<!-- Indexed -->
<meta name="robots" value="index, follow" />
<!-- Not indexed -->
<meta name="robots" value="noindex, nofollow" />
```
