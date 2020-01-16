![Amperage theme](https://raw.githubusercontent.com/asurbernardo/amperage/master/images/banner.png)

Amperage is a theme for static site generator [GoHugo](https://gohugo.io/). This theme provides the following features:

 - Generates AMP pages.
 - Valid PWA out of the box.
 - Automatic structured data.
 - Service worker for asset caching, link prefetching and offline navigation.
 - SEO optimized.
 - Multilanguage and i18n support.
 - Code highlighting on build time.
 - Super fast and lightweight.
 - Minimal and easily overridable styles.
 - Basic AMP shortcodes for ease of use.
 - Header menu, table of contents and related posts.
 - Uses web safe fonts by default.
 - Social share buttons and OGP/Twitter card tags.
 - Google analytics with gtag.
 - Configurable Adsense shortcode.
 - Comment system agnostic.

Lighthouse v5 theme results:

![Lighthouse results](https://raw.githubusercontent.com/asurbernardo/amperage/master/images/lighthouse-results.png)

## Installation

You can use the `exampleSite` provided to bootstrap your new project:

```sh
git clone https://github.com/asurbernardo/amperage.git

mkdir -p new-site/themes/amperage

mv amperage/exampleSite/* new-site
mv amperage/* new-site/themes/amperage

cd new-site

hugo serve
```

## Kitchen sink

You can check out all the components of this theme [here](https://asur.dev/en/amperage/theme-kitchen-sink) and a fully functional website using this theme [here](https://github.com/asurbernardo/blog).

## Configuration

```toml
# Default language if you have a multi-language setup
DefaultContentLanguage = "en"

baseURL = "https://example.com"
theme = "amperage"
pygmentsUseClasses = true

# Number of posts shown per page
paginate = 2

# Language sections
[languages]
    [languages.en]
        contentDir = "content"
        languageName = "English"
        languageCode = "en"
        title = "Amperage theme ⚡"
        description = "This is an example page for the Amperage theme!"
        weight = 1
    [languages.es]
        contentDir = "content/spanish"
        languageName = "Español"
        languageCode = "es"
        title = "Tema Amperage ⚡"
        description = "Esta es una página de ejemplo para el tema Amperage!"
        weight = 2

# Menu elements
[[menu.main]]
    identifier = "hugo"
    name = "Hugo"
    url = "https://gohugo.io"
    weight = 10
[[menu.main]]
    identifier = "github"
    name = "GitHub"
    url = "https://github.com/asurbernardo/amperage"
    weight = 10

# Enable only tags taxonomy
[taxonomies]
    tag = "tags"

[params]
    copyright = "Amperage" # Name shown on footer copyright
    themeColor = "#333" # Theme color displayed on mobile browsers

    # Default AMP components for the whole site
    ampElements = ["amp-analytics", "amp-social-share", "amp-install-serviceworker", "amp-iframe"]

    # Google Analytics code
    googleAnalytics = "UA-128498798-1"

    # Adsense publisher code
    adsensePublisher = "ca-pub-123456789"

    # Comments Iframe URL
    commentsEmbedUrl = "https://comments.example.com"

    # Social sites for metatags
    facebookSite = "example"
    twitterSite = "@example"

    # Structured data elements
    socialProfiles = ["https://twitter.com/example","https://www.linkedin.com/in/example/","https://github.com/example"]

    alternatePageName = "Amperage example"
    organizationLogo = "/logo.png"
    organizationName = "Asur"

    publisherName = "amperage"
    publisherLogo = "/logo-amp-article.png"
    publisherLogoWidth = 600
    publisherLogoHeight = 60
```

## Customize logo

To override the default logo add the svg markup on the partial `layouts/partials/header/logo.html`.

## Customize styles

To override default styles just add the file `assets/custom.scss` to your project and it will be transpiled, minified and appended automatically. Default styles only weight 5KB (including code highlighting), that leaves you with 45KB to further customize the theme.

## Enable cross-domain service worker installation

To enable cross-domain service worker you need to override the file `static/install-sw.html`:

```
<amp-install-serviceworker
  src="https://your-site.com/sw.js"
  data-iframe-src="https://your-site.com/install-sw.html"
  layout="nodisplay">
</amp-install-serviceworker>
```

## Menu links

On the menu you can set internal and external links. To set external links you can use the `config.toml` file:

```
[[menu.main]]
    identifier = "hugo"
    name = "Hugo"
    url = "https://gohugo.io"
    weight = 10
[[menu.main]]
    identifier = "github"
    name = "GitHub"
    url = "https://github.com/asurbernardo/amperage"
    weight = 10
```

If you want to display a page from your own site on the menu you need to add to the frontmatter of that page:
```
menu = "main"
```

This distinction is important because the service worker needs to identify the internal URLs so it can eager load them.

## Display ads

To enable ads you need to have an approved Adsense publisher code. Once you get one set it in the `config.toml`:

```
adsensePublisher = "ca-pub-123456789"
```

Now you can use the `amp-ad` shortcode:

```
{{< amp-adsense
    width="320"
    height="320"
    layout="fixed"
    slot="123456789" >}}
```

## Comments

Due to AMP requirements the comments need to be hosted in a domain different from the original. Amperage is ready to receive a URL to embed comments at the end of every post. This is to achieve a degree of agnosticy for the comment system.

Remember that to resize the iframe containing the comment box you need to send a message to the amp sentinel with the new height:

```
window.requestAnimationFrame(() => {
    window.parent.postMessage({
    sentinel: 'amp',
    type: 'embed-size',
    height: msg.data.height
    }, '*');
});
```

If you want to integrate your own comment service Amperage will add the parameters `id` and `url` to the request so you can use them on the iframe, in case you need a unique id. An example for Disqus:

```
var urlParams = new URLSearchParams(window.location.search);

var disqus_config = function () {
    this.page.url = urlParams.get('url');
    this.page.identifier = urlParams.get('id');
};
```

What I personally recommend is to use a new Github Pages project and refer it from your main site. Here you can see a [fully functional example using Disqus](https://github.com/asurbernardo/blog-comments).

## Contributing to Amperage

If you have a feature request or have found a bug feel free to open a new issue.
