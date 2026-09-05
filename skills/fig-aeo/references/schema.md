# JSON-LD patterns for Fig AEO

Paste-ready shapes. Replace host, name, and URLs with the brand's real values. Visible FAQ HTML must match FAQPage entries.

## Article

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "How hosted MCP authentication works",
  "description": "A short, literal summary of the article.",
  "dateModified": "2026-09-05",
  "author": { "@type": "Organization", "name": "Acme Auth" },
  "publisher": { "@type": "Organization", "name": "Acme Auth", "url": "https://acmeauth.example" },
  "mainEntityOfPage": "https://acmeauth.example/docs/mcp-auth"
}
```

## FAQPage

Use only when the page shows the same Q&A in HTML.

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Does Fig edit the brand's site?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "No. Fig returns live SEO and AEO research. The agent or brand owner decides what to change."
      }
    }
  ]
}
```

## Organization

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Acme Auth",
  "url": "https://acmeauth.example",
  "sameAs": ["https://github.com/acmeauth", "https://x.com/acmeauth"]
}
```

## BreadcrumbList

Only if the UI has a real breadcrumb.

Do not add HowTo or sitelinks SearchAction rich-result types for new pages. Do not mint Review markup for self-serving reviews.
