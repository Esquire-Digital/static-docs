## SEO With Decoupled Sites

Because the front end is completely custom, implementing the features [Yoast SEO](https://yoast.com/wordpress/plugins/seo/) normally automatically provides has to be done manually by developers. For content editors, this does not change much. Meta descriptions, meta titles, and other SEO information on a page is edited in the exact same way.

However, there is some warranted concern that decoupled sites may not be implementing certain SEO features correctly. This section explains how the generator implements the features that Yoast provides.

If you are only interested in editing content, there are no important differences in editing SEO settings on pages, and this documentation can be skipped. You can continue to edit SEO information the same way you do on normal WordPress sites. The below sections are for those who dive deep into SEO and want to know how static sites implement Yoast's features.

## Yoast Integration

The generator gets information from the Yoast plugin. It does so by using a plugin called [WPGraphQL Yoast SEO Addon](https://wordpress.org/plugins/add-wpgraphql-seo/). This plugin exposes important SEO information entered in the WordPress editor for pages, and allows us to implement Yoast's features manually on the front end.

So, saying that decoupled sites do not use Yoast is technically incorrect. Decoupled sites use Yoast for a convenient and familiar user interface, while implementing its features manually and slightly differently. Yoast performs important SEO functions, such as generating schema for each page automatically, which the generator still takes advantage of.
