<aside>
    <!-- Table of contents -->
    {{ .TableOfContents }}
    <!-- Related content -->
    {{ $related := .Site.RegularPages.Related . | first 5 }}
    {{ with $related }}
    <h3>See Also</h3>
    <ul>
        {{ range . }}
        <li><a href="{{ .RelPermalink }}">{{ .Title }}</a></li>
        {{ end }}
    </ul>
    {{ end }}
</aside>