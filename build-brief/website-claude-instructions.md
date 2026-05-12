# Ruska Media — Website Claude ohjeet
# Päivämäärä: 2026-05-10
# Tee kaikki muutokset kerralla. Älä kysy lupaa yksittäisiin kohtiin.

---

## 1. NOINDEX — EI KOSKETA VIELÄ

Sivusto on demo-ympäristössä (vercel.app). Noindex jätetään toistaiseksi
paikalleen — poistetaan vasta ennen DNS-siirtoa tuotantoon.

---

## 2. SCHEMA — kaupunkisivujen template

Kaupunkisivuilla (/haakuvaus/[kaupunki]/, /kiinteistokuvaus/[kaupunki]/,
/videotuotanto/[kaupunki]/) on vain BreadcrumbList. Puuttuu Service + FAQPage.

Löydä kaupunkisivujen Astro-template (esim. src/pages/haakuvaus/[kaupunki].astro)
ja lisää sinne:

### Service schema (hääkuvaus kaupunkisivuille):
```json
{
  "@context": "https://schema.org",
  "@type": "Service",
  "name": "Hääkuvaus [KAUPUNKI]",
  "serviceType": "Hääkuvaus",
  "description": "Hääkuvaus [KAUPUNGISSA] — Joel Nykänen kuvaa häät dokumentaarisesti.",
  "provider": {
    "@type": "LocalBusiness",
    "name": "Ruska Media",
    "url": "https://ruskamedia.com"
  },
  "areaServed": {
    "@type": "City",
    "name": "[KAUPUNKI]"
  },
  "url": "https://ruskamedia.com/haakuvaus/[kaupunki-slug]/",
  "offers": {
    "@type": "AggregateOffer",
    "lowPrice": "500",
    "highPrice": "2500",
    "priceCurrency": "EUR"
  }
}
```

### Service schema (kiinteistökuvaus kaupunkisivuille):
```json
{
  "@context": "https://schema.org",
  "@type": "Service",
  "name": "Kiinteistökuvaus [KAUPUNKI]",
  "serviceType": "Kiinteistövalokuvaus",
  "provider": {
    "@type": "LocalBusiness",
    "name": "Ruska Media",
    "url": "https://ruskamedia.com"
  },
  "areaServed": {
    "@type": "City",
    "name": "[KAUPUNKI]"
  },
  "url": "https://ruskamedia.com/kiinteistokuvaus/[kaupunki-slug]/"
}
```

### Service schema (videotuotanto kaupunkisivuille):
```json
{
  "@context": "https://schema.org",
  "@type": "Service",
  "name": "Videotuotanto [KAUPUNKI]",
  "serviceType": "Videotuotanto",
  "provider": {
    "@type": "LocalBusiness",
    "name": "Ruska Media",
    "url": "https://ruskamedia.com"
  },
  "areaServed": {
    "@type": "City",
    "name": "[KAUPUNKI]"
  },
  "url": "https://ruskamedia.com/videotuotanto/[kaupunki-slug]/"
}
```

### FAQPage schema (kaupunkisivuille):
Käytä sivulla jo olevien FAQ-kysymysten sisältöä. Älä keksi uusia — lue
ne suoraan sivun FAQ-osiosta ja rakenna schema niiden pohjalta.

Rakenne:
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "[Sivulla oleva kysymys]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[Sivulla oleva vastaus]"
      }
    }
  ]
}
```

### Muut sivut joilta schema puuttuu:

/tiimi-yhteystiedot → lisää Person-schema:
```json
{
  "@context": "https://schema.org",
  "@type": "Person",
  "name": "Joel Nykänen",
  "jobTitle": "Visuaalisen sisällön johtaja",
  "worksFor": { "@type": "Organization", "name": "Ruska Media" },
  "email": "joel@ruskamedia.com",
  "telephone": "+358405369809",
  "url": "https://ruskamedia.com/tiimi-yhteystiedot/",
  "knowsAbout": ["Videotuotanto", "Hääkuvaus", "Kiinteistökuvaus", "Valokuvaus"]
}
```

/blogi → lisää Blog-schema:
```json
{
  "@context": "https://schema.org",
  "@type": "Blog",
  "name": "Ruska Media — Blogi",
  "url": "https://ruskamedia.com/blogi/",
  "publisher": { "@type": "Organization", "name": "Ruska Media" }
}
```

Blogiartikkeleihin lisää Article-schema (datePublished, author, headline).

/en → lisää sama LocalBusiness-schema kuin etusivulla.

---

## 3. FAQ-SISÄLTÖ — hintavastaukset

Muuta seuraavien sivujen FAQ-vastaukset. Älä muuta muita FAQja.

### /lyhytvideo/
Kysymys: "Paljonko lyhytvideo maksaa?"
Nykyinen: "Pyydä tarjous niin laaditaan juuri teidän tarpeisiin sopiva paketti."
UUSI: "Yksittäinen lyhytvideo alkaen 500 €. Kuukausipaketti (4–8 videota/kk) räätälöidään tarpeen mukaan — pyydä tarjous."

### /valokuvaus/
Kysymys: "Paljonko yrityskuvaus maksaa?"
Nykyinen: "Hinta riippuu kuvauksen laajuudesta, sijainnista ja kuvamäärästä. Pyydä tarjous niin lasketaan juuri teidän tarpeisiin sopiva paketti."
UUSI: "Henkilökuvaus alkaen 300 €. Laajempi yrityskuvaus (tiimikuvat, tilat) alkaen 600 €. Lopullinen hinta riippuu kuvausajasta ja kuvamäärästä — pyydä tarjous."

### /videotuotanto/
Kysymys: "Paljonko yritysvideo maksaa?"
Nykyinen: "Yritysvideo hinta vaihtelee laajuuden, kuvausajan ja jälkituotannon mukaan. Pyydä tarjous niin laaditaan juuri teidän tarpeisiin sopiva paketti."
UUSI: "Yksinkertainen yritysvideo alkaen 1 500 €. Laajempi kampanja tai brändivideo 3 000–8 000 €. Hinta riippuu kuvausajasta, käsikirjoituksesta ja jälkituotannosta — pyydä tarjous."

Lisäksi: muuta kysymys "Kuvaatteko myös Helsingin seudulla?" → "Mihin kaupunkeihin videotuotanto onnistuu?"
Vastaus: "Toimimme koko Suomessa — Jyväskylä, Tampere, Helsinki, Turku, Oulu ja muut. Matkakulut lasketaan etäisyyden mukaan."

### /asunto-ja-kiinteistokuvaus/
Kysymys: "Paljonko kiinteistökuvaus maksaa?"
Nykyinen: "Kiinteistökuvauksen hinta riippuu kohteen koosta ja tilatuista palveluista. Pyydä tarjous niin lasketaan kohteen mukaan."
UUSI: "Perusasuntokuvaus alkaen 150 €. Lopullinen hinta riippuu kohteen koosta ja tilatuista palveluista (drone, digistailaus, video). Pyydä tarjous niin lasketaan tarkka hinta."

### /kiinteistokuvaus/helsinki/
Kysymys: "Paljonko kiinteistökuvaus maksaa Helsingissä?"
Nykyinen: "Sama hinnoittelu kuin muualla — matkakulut Helsinkiin lisätään tarjoukseen. Pyydä tarjous niin lasketaan kohteen mukaan."
UUSI: "Perusasuntokuvaus alkaen 150 €, matkakulut Helsinkiin lisätään tarjoukseen. Arvokohteet ja luksusasunnot hinnoitellaan kohteen mukaan — pyydä tarjous."

### /kiinteistokuvaus/jyvaskyla/
Kysymys: "Paljonko kiinteistökuvaus maksaa Jyväskylässä?"
Nykyinen: "Sama hinnoittelu kuin muualla — ei matkakuluja Jyväskylän sisällä. Pyydä tarjous niin lasketaan kohteen mukaan."
UUSI: "Perusasuntokuvaus alkaen 150 €. Jyväskylässä ei matkakuluja. Pyydä tarjous niin lasketaan kohteen mukaan."

### /kiinteistokuvaus/tampere/
Kysymys: "Paljonko kiinteistökuvaus maksaa Tampereella?"
Nykyinen: "Sama hinnoittelu kuin muualla — matkakulut Tampereelle lisätään tarjoukseen. Pyydä tarjous niin lasketaan kohteen mukaan."
UUSI: "Perusasuntokuvaus alkaen 150 €, matkakulut Tampereelle lisätään tarjoukseen. Pyydä tarjous niin lasketaan kohteen mukaan."

### /haakuvaus/
LISÄÄ uusi kysymys FAQ-listan ensimmäiseksi:
Kysymys: "Paljonko hääkuvaus maksaa?"
Vastaus: "Hääkuvauspaketit alkaen 500 € (potrettikuvaus). Koko päivän dokumentaarinen kuvaus (12h) 2 000 €. Häävideo 2 500 €. Matkakulut lisätään kaupungin mukaan."

---

## 4. SITEMAP — poista turhat sivut

Poista public/sitemap.xml:stä tai sitemap-generaattorista nämä URLit:
- /varaa/haakuvaus/
- /varaa/kiinteistokuvaus/
- /varaa/lyhytvideo/
- /varaa/valokuvaus/
- /varaa/videomarkkinointi/
- /kiitos/

Lisäksi: lisää näille sivuille noindex-metatagi:
- /varaa/* (kaikki varaus-sivut)
- /kiitos/
- /tietosuoja/

---

## 5. TARKISTUSLISTA KUN VALMIS

Aja check-head.js ja varmista:

```
/haakuvaus/helsinki/  → schemas: BreadcrumbList, Service, FAQPage
/kiinteistokuvaus/jyvaskyla/  → schemas: BreadcrumbList, Service, FAQPage
/videotuotanto/tampere/  → schemas: BreadcrumbList, Service, FAQPage
/tiimi-yhteystiedot  → schemas: Person
/blogi  → schemas: Blog
/  → schemas: LocalBusiness (noindex jätetään — poistetaan ennen julkaisua)
```

FAQ-tarkistus — näiden pitää löytyä sivulta (grep tai selaimessa):
- /haakuvaus/ FAQ sisältää "500 €" ja "2 000 €"
- /videotuotanto/ FAQ sisältää "1 500 €"
- /asunto-ja-kiinteistokuvaus/ FAQ sisältää "150 €"
- /lyhytvideo/ FAQ sisältää "500 €"
- /valokuvaus/ FAQ sisältää "300 €"

Sitemap ei saa sisältää /varaa/* eikä /kiitos/ URLeja.
