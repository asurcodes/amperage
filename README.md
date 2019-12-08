@TODO

Amperage is a theme for static site generator [GoHugo](https://gohugo.io/). This theme provides the following features:

 - Generates AMP pages.
 - Valid PWA out of the box.
 - Automatic structured data.
 - Service worker for asset caching, link prefetching and offline navigation.
 - SEO optimized.
 - Multilanguage and i18n support.
 - Super fast and lightweight.
 - Minimal and easily overridable styles.
 - Basic AMP shortcodes for ease of use.
 - Seamless code highlighting (block and inline)
 - Header menu, table of contents and related posts.
 - Social share
 - Default table styles

## Installation

You can use the `exampleSite` provided as example to bootstrap your new project:

```
git clone https://github.com/asurbernardo/amperage.git
mkdir your-site
git cp amperage/exampleSite your-site
mkdir your-site/themes/amperage
mv amperage your-site/themes/amperage
hugo serve
```

Lighthouse v6 example site results:

@TODO

## Kitchen sink

You can check out all the components of this theme [here](https://asur.dev/en/amperage/theme-kitchen-sink) and a fully functional website using this theme [here](https://github.com/asurbernardo/blog).

## Configuration

```
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

# Enable only tag toxonomy
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

## Contribute

@TODO