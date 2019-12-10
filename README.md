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
DefaultContentLanguage = "en" # Default language if you have a multi-language setup

baseURL = "https://example.com"
theme = "amperage"
pygmentsUseClasses = true

paginate = 2 # Number of posts shown per page

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
    copyright = "amperage" # Name shown on footer copyright
    themeColor = "#333" # Theme color displayed on mobile browsers

    # Default AMP components for the whole site
    ampElements = ["amp-analytics", "amp-social-share", "amp-install-serviceworker"]

    # Google Analytics code
    googleAnalytics = "UA-128498798-1"

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

To override default styles just create a file in `assets/custom.scss` on your project and it will be transpiled, minified and appended automatically. The default styles are only 5KB, that leaves you with 45KB of room to still be a valid AMP page.

## Enable cross-domain service worker installation

To enable cross-domain service worker you need to override the file `static/install-sw.html`:

```
<amp-install-serviceworker
  src="https://your-site.com/sw.js"
  data-iframe-src="https://your-site.com/install-sw.html"
  layout="nodisplay">
</amp-install-serviceworker>
```

## Contributing to Amperage

If you have a feature request or have found a bug feel free to open an issue on this repository.
