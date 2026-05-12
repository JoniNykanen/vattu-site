# Ruska Media — Astro Build Brief
## Part 3: Schema Markup & Tekninen SEO

> Lisää nämä JSON-LD -blokit Base.astro-layoutin <head>-osioon.
> Sivukohtaiset schemat: lisää suoraan kyseisen sivun .astro-tiedostoon.

---

## 1. LocalBusiness Schema — ETUSIVU (/)

Lisää Base.astro:hon kun `Astro.url.pathname === '/'`:

```json
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "Ruska Media",
  "legalName": "Ruska Tuotanto Oy",
  "url": "https://ruskamedia.com",
  "logo": "https://ruskamedia.com/wp-content/uploads/2019/05/RUSKA-MEDIA-MUSTA.png",
  "image": "https://ruskamedia.com/wp-content/uploads/2022/11/Ruska-Media-Videomarkkinointi.jpg",
  "telephone": "+358405369809",
  "email": "joel@ruskamedia.com",
  "address": {
    "@type": "PostalAddress",
    "addressLocality": "Jyväskylä",
    "addressCountry": "FI"
  },
  "areaServed": {
    "@type": "Country",
    "name": "Finland"
  },
  "priceRange": "€€",
  "sameAs": [
    "https://www.facebook.com/ruskamedia/"
  ],
  "hasOfferCatalog": {
    "@type": "OfferCatalog",
    "name": "Ruska Media palvelut",
    "itemListElement": [
      { "@type": "Offer", "itemOffered": { "@type": "Service", "name": "Lyhytvideo yrityksille" }},
      { "@type": "Offer", "itemOffered": { "@type": "Service", "name": "Valokuvaus yrityksille" }},
      { "@type": "Offer", "itemOffered": { "@type": "Service", "name": "Videomarkkinointi yrityksille" }},
      { "@type": "Offer", "itemOffered": { "@type": "Service", "name": "Kiinteistökuvaus" }},
      { "@type": "Offer", "itemOffered": { "@type": "Service", "name": "Hääkuvaus" }}
    ]
  }
}
```

---

## 2. Service Schema — PALVELUSIVUT

### /lyhytvideo/
```json
{
  "@context": "https://schema.org",
  "@type": "Service",
  "name": "Lyhytvideo yrityksille",
  "serviceType": "Lyhytvideotuotanto",
  "description": "Lyhytvideoita yrityksille TikTokiin, Instagram Reelsiin ja YouTube Shortsiin.",
  "provider": {
    "@type": "LocalBusiness",
    "name": "Ruska Media",
    "url": "https://ruskamedia.com"
  },
  "areaServed": { "@type": "Country", "name": "Finland" },
  "url": "https://ruskamedia.com/lyhytvideo/"
}
```

### /valokuvaus/
```json
{
  "@context": "https://schema.org",
  "@type": "Service",
  "name": "Valokuvaus yrityksille",
  "serviceType": "Yrityskuvaus",
  "description": "Yrityskuvaus, henkilökuvaus ja markkinointikuvaus Jyväskylässä ja koko Suomessa.",
  "provider": {
    "@type": "LocalBusiness",
    "name": "Ruska Media",
    "url": "https://ruskamedia.com"
  },
  "areaServed": { "@type": "Country", "name": "Finland" },
  "url": "https://ruskamedia.com/valokuvaus/"
}
```

### /videomarkkinointi-yrityksille/
```json
{
  "@context": "https://schema.org",
  "@type": "Service",
  "name": "Videomarkkinointi yrityksille",
  "serviceType": "Videotuotanto",
  "description": "Yritysvideot, brändivideot ja rekrytointivideot markkinointiin ja myyntiin.",
  "provider": {
    "@type": "LocalBusiness",
    "name": "Ruska Media",
    "url": "https://ruskamedia.com"
  },
  "areaServed": { "@type": "Country", "name": "Finland" },
  "url": "https://ruskamedia.com/videomarkkinointi-yrityksille/"
}
```

### /asunto-ja-kiinteistokuvaus/
```json
{
  "@context": "https://schema.org",
  "@type": "Service",
  "name": "Kiinteistökuvaus",
  "alternateName": "Ruska Estate",
  "serviceType": "Kiinteistövalokuvaus",
  "description": "Ammattimaiset kiinteistökuvaukset — valokuva, drone, digistailaus ja kiinteistövideo. Yli 1000 asuntoa kuvattuna vuodessa.",
  "provider": {
    "@type": "LocalBusiness",
    "name": "Ruska Media",
    "url": "https://ruskamedia.com"
  },
  "areaServed": { "@type": "Country", "name": "Finland" },
  "url": "https://ruskamedia.com/asunto-ja-kiinteistokuvaus/"
}
```

### /haakuvaus/
```json
{
  "@context": "https://schema.org",
  "@type": "Service",
  "name": "Hääkuvaus",
  "alternateName": "Ruska Wedding Frames",
  "serviceType": "Hääkuvaus",
  "description": "Hääkuvaus ja häävideo koko Suomessa. Joel Nykänen — selkeät paketit, ei ennakkomaksuja.",
  "provider": {
    "@type": "LocalBusiness",
    "name": "Ruska Media",
    "url": "https://ruskamedia.com"
  },
  "areaServed": { "@type": "Country", "name": "Finland" },
  "url": "https://ruskamedia.com/haakuvaus/",
  "offers": [
    {
      "@type": "Offer",
      "name": "Hääpotretit",
      "price": "500",
      "priceCurrency": "EUR",
      "description": "1–2 tuntia, noin 30 kuvaa, toimitus 2–3 viikkoa."
    },
    {
      "@type": "Offer",
      "name": "Potretit + vihkitilaisuus",
      "price": "700",
      "priceCurrency": "EUR"
    },
    {
      "@type": "Offer",
      "name": "Potretit + vihki + juhla (8h)",
      "price": "1600",
      "priceCurrency": "EUR"
    },
    {
      "@type": "Offer",
      "name": "Koko päivä (12h)",
      "price": "2000",
      "priceCurrency": "EUR"
    },
    {
      "@type": "Offer",
      "name": "Häävideo",
      "price": "2500",
      "priceCurrency": "EUR"
    }
  ]
}
```

---

## 3. FAQPage Schema — palvelusivuille

Lisää jokaisen palvelusivun FAQ-osion yhteyteen.

### Esimerkki /haakuvaus/:
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Milloin hääkuvaaja kannattaa varata?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Suosittelemme varaamaan 12–18 kuukautta ennen häitä. Suosituimmat viikonloput täyttyvät nopeasti."
      }
    },
    {
      "@type": "Question",
      "name": "Matkustatko Jyväskylän ulkopuolelle?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Kyllä — kuvaan häitä ympäri Suomea. Matkakulut lasketaan lomakkeessa automaattisesti kaupungin mukaan."
      }
    },
    {
      "@type": "Question",
      "name": "Mitä jos peruutan hääkuvauksen?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Peruutus on maksuton yli 30 päivää ennen häitä. Ei ennakkovarausmaksua."
      }
    },
    {
      "@type": "Question",
      "name": "Onko teillä kirjallinen sopimus?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Aina — kirjallinen sopimus jokaiseen kuvaukseen. Ei yllätyksiä."
      }
    }
  ]
}
```

### Esimerkki /asunto-ja-kiinteistokuvaus/:
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Paljonko kiinteistökuvaus maksaa?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Kiinteistökuvauksen hinta riippuu kohteen koosta ja tilatuista palveluista. Perusasuntokuvaus alkaen [X]€. Pyydä tarjous niin lasketaan kohteen mukaan."
      }
    },
    {
      "@type": "Question",
      "name": "Kuinka nopeasti kuvat toimitetaan?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Valokuvat toimitetaan 1–3 arkipäivässä kuvauksesta. Kiiretoimitukset sovittavissa lisämaksusta."
      }
    },
    {
      "@type": "Question",
      "name": "Kuvaatteko koko Suomessa?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Kyllä — palvelemme Jyväskylässä ja koko Suomessa. Matkakulut lisätään tarjoukseen."
      }
    }
  ]
}
```

---

## 4. Person Schema — tiimisivulle

```json
{
  "@context": "https://schema.org",
  "@type": "Person",
  "name": "Joel Nykänen",
  "jobTitle": "Visuaalisen sisällön johtaja",
  "worksFor": {
    "@type": "Organization",
    "name": "Ruska Media"
  },
  "email": "joel@ruskamedia.com",
  "telephone": "+358405369809",
  "url": "https://ruskamedia.com/tiimi-yhteystiedot/",
  "image": "https://ruskamedia.com/wp-content/uploads/2025/04/Joel-Nykanen-Ruska-Media-Event-yhteystiedot-675x900.jpg",
  "knowsAbout": ["Videotuotanto", "Hääkuvaus", "Kiinteistökuvaus", "Valokuvaus"]
}
```

---

## 5. Article Schema — blogiartikkelit

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "[Artikkelin otsikko]",
  "author": {
    "@type": "Person",
    "name": "Joel Nykänen"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Ruska Media",
    "logo": {
      "@type": "ImageObject",
      "url": "https://ruskamedia.com/wp-content/uploads/2019/05/RUSKA-MEDIA-MUSTA.png"
    }
  },
  "datePublished": "[ISO 8601 päivämäärä]",
  "dateModified": "[ISO 8601 päivämäärä]",
  "image": "[artikkelin pääkuva]",
  "url": "https://ruskamedia.com/blogi/[slug]/"
}
```

---

## 6. BreadcrumbList Schema — kaikille alasivuille

```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Etusivu",
      "item": "https://ruskamedia.com/"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "[Sivun nimi]",
      "item": "https://ruskamedia.com/[slug]/"
    }
  ]
}
```

Kaupunkisivuilla 3 tasoa:
```json
{
  "@type": "ListItem", "position": 1, "name": "Etusivu", "item": "https://ruskamedia.com/"
},
{
  "@type": "ListItem", "position": 2, "name": "Hääkuvaus", "item": "https://ruskamedia.com/haakuvaus/"
},
{
  "@type": "ListItem", "position": 3, "name": "Hääkuvaus Tampere", "item": "https://ruskamedia.com/haakuvaus/tampere/"
}
```

---

## 7. Astro-komponentti: SchemaOrg.astro

Luo tiedosto `src/components/SchemaOrg.astro`:

```astro
---
interface Props {
  schema: object | object[]
}
const { schema } = Astro.props
const schemas = Array.isArray(schema) ? schema : [schema]
---
{schemas.map(s => (
  <script type="application/ld+json" set:html={JSON.stringify(s)} />
))}
```

Käyttö Base.astro:ssa tai sivuilla:
```astro
---
import SchemaOrg from '../components/SchemaOrg.astro'
---
<SchemaOrg schema={[localBusinessSchema, faqSchema]} />
```

---

## 8. Meta-tagit — Base.astro

Lisää <head>-osioon:

```astro
---
interface Props {
  title: string
  description: string
  canonical?: string
  ogImage?: string
  noindex?: boolean
}
const {
  title,
  description,
  canonical = Astro.url.href,
  ogImage = 'https://ruskamedia.com/wp-content/uploads/2022/11/Ruska-Media-Videomarkkinointi.jpg',
  noindex = false
} = Astro.props
---

<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>{title}</title>
  <meta name="description" content={description} />
  <link rel="canonical" href={canonical} />
  {noindex && <meta name="robots" content="noindex, nofollow" />}
  {!noindex && <meta name="robots" content="index, follow, max-image-preview:large, max-snippet:-1, max-video-preview:-1" />}

  <!-- Open Graph -->
  <meta property="og:title" content={title} />
  <meta property="og:description" content={description} />
  <meta property="og:url" content={canonical} />
  <meta property="og:type" content="website" />
  <meta property="og:image" content={ogImage} />
  <meta property="og:locale" content="fi_FI" />
  <meta property="og:site_name" content="Ruska Media" />

  <!-- Twitter Card -->
  <meta name="twitter:card" content="summary_large_image" />
  <meta name="twitter:title" content={title} />
  <meta name="twitter:description" content={description} />
  <meta name="twitter:image" content={ogImage} />

  <link rel="icon" href="/favicon.ico" />
</head>
```

---

## 9. Sitemap — astro.config.mjs

```js
import { defineConfig } from 'astro/config'
import tailwind from '@astrojs/tailwind'
import sitemap from '@astrojs/sitemap'

export default defineConfig({
  site: 'https://ruskamedia.com',
  integrations: [
    tailwind(),
    sitemap({
      changefreq: 'monthly',
      priority: 0.7,
      lastmod: new Date(),
      customPages: [
        'https://ruskamedia.com/',
        'https://ruskamedia.com/lyhytvideo/',
        'https://ruskamedia.com/valokuvaus/',
        'https://ruskamedia.com/videomarkkinointi-yrityksille/',
        'https://ruskamedia.com/asunto-ja-kiinteistokuvaus/',
        'https://ruskamedia.com/haakuvaus/',
        'https://ruskamedia.com/haakuvaus/jyvaskyla/',
        'https://ruskamedia.com/haakuvaus/tampere/',
        'https://ruskamedia.com/haakuvaus/helsinki/',
        'https://ruskamedia.com/haakuvaus/turku/',
        'https://ruskamedia.com/kiinteistokuvaus/jyvaskyla/',
        'https://ruskamedia.com/kiinteistokuvaus/tampere/',
        'https://ruskamedia.com/kiinteistokuvaus/helsinki/',
        'https://ruskamedia.com/tiimi-yhteystiedot/',
        'https://ruskamedia.com/blogi/',
      ]
    })
  ]
})
```

---

## 10. robots.txt

```
User-agent: *
Disallow:

User-agent: GPTBot
Allow: /

User-agent: PerplexityBot
Allow: /

User-agent: ClaudeBot
Allow: /

User-agent: Google-Extended
Allow: /

Sitemap: https://ruskamedia.com/sitemap-index.xml
```

Tallenna: `public/robots.txt`
