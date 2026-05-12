# Ruska Media — Astro Build Brief
## Part 4: Keyword Map & Sisältöohjeet

> Käytä tätä ohjaamaan sisältökirjoitusta.
> Jokainen sivu tavoittelee yhtä pääkeywordia + joukon tukisanoja.
> Kirjoita sisältö luonnollisesti — älä tunge keywordeja väkisin.

---

## Keyword-kartta per sivu

| Sivu | Pääkeyword | Volyymi/kk | Tukisanat (sisällytä luonnollisesti) |
|------|-----------|-----------|--------------------------------------|
| / | ruska media | branded | videotuotanto jyväskylä, valokuvaus, hääkuvaus, kiinteistökuvaus |
| /lyhytvideo/ | lyhytvideo yritys | ~200 | lyhytvideot yrityksille, tiktok yritys, instagram reels, youtube shorts, some-video |
| /valokuvaus/ | valokuvaus yritys jyväskylä | ~200 | yrityskuvaus jyväskylä, henkilökuvaus jyväskylä, markkinointikuvaus |
| /videomarkkinointi-yrityksille/ | videomarkkinointi yrityksille | ~130 | yritysvideo, brändivideo, rekrytointivideo, videotuotanto jyväskylä |
| /asunto-ja-kiinteistokuvaus/ | kiinteistökuvaus | ~400 | asuntokuvaus, kiinteistövalokuvaus, drone kuvaus kiinteistö, digistailaus |
| /haakuvaus/ | hääkuvaus | ~320 | hääkuvaaja, hääkuvaus hinta, häävideo, wedding photographer finland |
| /haakuvaus/jyvaskyla/ | hääkuvaus jyväskylä | ~70 | hääkuvaaja jyväskylä, hääkuvaus keski-suomi |
| /haakuvaus/tampere/ | hääkuvaus tampere | ~130 | hääkuvaaja tampere, häät tampere |
| /haakuvaus/helsinki/ | hääkuvaus helsinki | ~200 | hääkuvaaja helsinki |
| /haakuvaus/turku/ | hääkuvaus turku | ~140 | hääkuvaaja turku |
| /kiinteistokuvaus/jyvaskyla/ | kiinteistökuvaus jyväskylä | ~100 | asuntokuvaus jyväskylä, kiinteistövalokuvaaja jyväskylä |
| /kiinteistokuvaus/tampere/ | kiinteistökuvaus tampere | ~100 | asuntokuvaus tampere |
| /kiinteistokuvaus/helsinki/ | kiinteistökuvaus helsinki | ~150 | asuntokuvaus helsinki |
| /blogi/parhaat-haapaikat-jyvaskylassa/ | parhaat hääpaikat jyväskylä | ~100 | häätilat jyväskylä, hääpaikat keski-suomi |
| /blogi/parhaat-haapaikat-tampereella/ | hääpaikat tampere | ~210 | häätilat tampere, hääpaikat pirkanmaa |

---

## Sisältöohjeet — tärkeimmät säännöt

### 1. Keyword etusijalla H1:ssä
H1 sisältää aina pääkeywordin tai lähisynonyymin:
- ✅ "Hääkuvaus koko Suomessa" (sisältää "hääkuvaus")
- ✅ "Kiinteistökuvaus Jyväskylässä" (sisältää "kiinteistökuvaus jyväskylä")
- ❌ "Ikuista muistosi" (ei keywordeja)

### 2. Kaupunkimaininta ensimmäisessä kappaleessa
Jokainen paikallinen sivu (palvelusivu + kaupunkisivu) mainitsee kaupungin nimeltä ensimmäisessä 100 sanassa:
- ✅ "...tarjoamme kiinteistökuvausta Jyväskylässä ja Keski-Suomessa..."
- ❌ kaupunki mainitaan vasta sivun lopussa

### 3. Hinnat näkyvillä
Hääkuvaus: täysi hinnoittelu sivulla (jo olemassa).
Kiinteistökuvaus: "alkaen X€" tai selkeä pakettilista.
Lyhytvideo ja valokuvaus: vähintään "Pyydä tarjous" mutta mieluiten hintaluokka.
**Perustelu:** "kiinteistökuvauksen hinta" ja "hääkuvauksen hinta" ovat hakuja joihin valokuvaajat.fi vastaa — Ruska voi vastata omalla sivullaan.

### 4. FAQ jokaisella palvelusivulla
Vähintään 4 kysymystä per palvelusivu. Merkitään HTML:ssä selkeästi:
```html
<section class="faq">
  <h2>Usein kysyttyä</h2>
  <details>
    <summary>Paljonko kiinteistökuvaus maksaa?</summary>
    <p>Kiinteistökuvauksen hinta riippuu...</p>
  </details>
  ...
</section>
```
Schema lisätään erikseen (ks. Part 3).

### 5. Internal linking — pakollinen rakenne
Jokainen kaupunkisivu linkittää takaisin pääsivulle:
```
/haakuvaus/tampere/ → linkki: "Katso kaikki hääkuvauspaketit" → /haakuvaus/
/haakuvaus/tampere/ → linkki naapurikaupunkiin: "Hääkuvaus Helsinki" → /haakuvaus/helsinki/
```

Pääpalvelusivu linkittää kaupunkisivuihin:
```
/haakuvaus/ → "Kuvaan häitä ympäri Suomea — katso kaupunkikohtaiset sivut:"
→ [Jyväskylä] [Tampere] [Helsinki] [Turku]
```

Blogisivut linkittävät palvelusivuille:
```
/blogi/parhaat-haapaikat-jyvaskylassa/ → "Etsitkö hääkuvaajaa Jyväskylään?" → /haakuvaus/jyvaskyla/
```

### 6. Alt-tekstit kaikille kuville
Muoto: "[Kuvan sisältö] — [brändi tai kaupunki]"
- ✅ "Hääkuvaus Tampereella, Joel Nykänen — Ruska Media"
- ✅ "Kiinteistökuvaus Jyväskylässä, kerrostaloasunto — Ruska Estate"
- ❌ "image001.jpg" tai tyhjä alt

### 7. Sivun sanamäärät (minimi)
| Sivutyyppi | Minimi |
|-----------|--------|
| Pääpalvelusivu (lyhytvideo, valokuvaus, video, estate, häät) | 500 sanaa |
| Kaupunkisivu | 250 sanaa |
| Blogiartikkeli | 600 sanaa |
| Etusivu | 300 sanaa (ilman navigaatiota) |

---

## Sisäisen linkityksen kartta

```
Etusivu (/)
├── → /lyhytvideo/
├── → /valokuvaus/
├── → /videomarkkinointi-yrityksille/
├── → /asunto-ja-kiinteistokuvaus/
└── → /haakuvaus/

/haakuvaus/ (pillar)
├── → /haakuvaus/jyvaskyla/
├── → /haakuvaus/tampere/
├── → /haakuvaus/helsinki/
└── → /haakuvaus/turku/

/haakuvaus/[kaupunki]/ (spoke)
├── → /haakuvaus/ (takaisin pillariin)
└── → /haakuvaus/[naapurikaupunki]/ (ristilinkit)

/asunto-ja-kiinteistokuvaus/ (pillar)
├── → /kiinteistokuvaus/jyvaskyla/
├── → /kiinteistokuvaus/tampere/
└── → /kiinteistokuvaus/helsinki/

/blogi/parhaat-haapaikat-jyvaskylassa/
└── → /haakuvaus/jyvaskyla/ (CTA-linkki)

/blogi/parhaat-haapaikat-tampereella/
└── → /haakuvaus/tampere/ (CTA-linkki)
```

---

## Englanninkieliset sivut — SEO-ohjeet

Säilytä olemassa oleva rakenne. Päivitä meta-tagit:

| Sivu | Title | Meta |
|------|-------|------|
| /en/ | `Ruska Media — Video Production & Photography Finland` | `Professional video production, photography and wedding photography in Finland. Ruska Media, based in Jyväskylä.` |
| /en/wedding-photography/ | `Wedding Photographer Finland — Ruska Wedding Frames by Joel Nykänen` | `Wedding photography across Finland. Clear packages, no deposit required. Book your wedding photographer.` |
| /en/real-estate-photography/ | `Real Estate Photography Finland — Ruska Estate` | `Professional real estate photography in Finland — photos, drone, virtual staging. Over 1000 properties per year.` |
| /en/video-marketing-for-businesses/ | `Video Marketing for Businesses — Ruska Media Finland` | `Corporate videos, brand videos and recruitment videos. Ruska Media, Jyväskylä, Finland.` |

---

## Poistu-URL:t (ei rakenneta)

Nämä URLit olivat WordPressissä mutta EI rakenneta uuteen Astro-sivustoon:
- `/portfolio/` — integroitu palvelusivuihin gallerioina
- `/team-contact/` (ilman /en/ prefixiä) — redirect → /tiimi-yhteystiedot/
- `/en/team-contact/` — säilytetään, redirectataan tarvittaessa

**Redirect-lista (lisää vercel.json tai .htaccess):**
```
/portfolio/ → /asunto-ja-kiinteistokuvaus/  (301)
/team-contact/ → /tiimi-yhteystiedot/       (301)
```
