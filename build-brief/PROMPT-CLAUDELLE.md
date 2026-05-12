# RUSKA MEDIA — CLAUDE BUILD PROMPT
## Syötä tämä Claude-sessiolle kun aloitat rakentamisen

---

## Konteksti

Jatkat Ruska Median Astro 5 -sivuston rakentamista.
Projekti löytyy: `C:/Users/jonin/Projects/ruska-media`

**Mikä on jo valmis — ÄLÄ KOSKE:**
- Base layout (Base.astro)
- Header + navigaatio
- Footer
- Kaikki alkuperäiset palvelusivut:
  - /videomarkkinointi-yrityksille/
  - /asunto-ja-kiinteistokuvaus/
  - /haakuvaus/
  - /tiimi-yhteystiedot/
  - /blogi/ + olemassa olevat artikkelit
  - /en/* (englanninkieliset sivut)

Lue nämä tiedostot ENNEN kuin teet mitään:
1. `build-brief/part-1-architecture.md`
2. `build-brief/part-2-page-briefs.md`
3. `build-brief/part-3-schema-technical.md`
4. `build-brief/part-4-keyword-map.md`
5. `build-brief/part-5-city-content.md` ← kaupunkisivujen sisältöstrategia

---

## Mitä lisäät

Ruska Media on Jyväskyläläinen mediatuotantoyritys (Ruska Tuotanto Oy).
Tiimi: Joel Nykänen + Oskari Vattu.

**5 palvelua (kaikki navigaatiossa):**
1. Lyhytvideo yrityksille
2. Valokuvaus yrityksille
3. Filmi & Video (videomarkkinointi)
4. Ruska Estate (kiinteistökuvaus)
5. Wedding Frames by Joel Nykänen (hääkuvaus)

---

## Tärkeysjärjestys

**Vaihe 1 — SEO-korjaukset olemassa oleviin sivuihin**
Älä muuta layoutia tai designia — muuta VAIN metatagit ja lisää puuttuvat elementit:

- Kaikki sivut: lisää `<title>`, `<meta description>`, `<link rel="canonical">` (ks. Part 2 per sivu)
- /asunto-ja-kiinteistokuvaus/ → muuta title: poista "- Jyväskylä" → "Kiinteistökuvaus koko Suomessa | Ruska Media"
- /videomarkkinointi-yrityksille/ → lisää FAQ-osio sivun loppuun (ks. Part 2 FAQ-sisältö)
- /haakuvaus/ → lisää FAQ-osio (ks. Part 2)
- /asunto-ja-kiinteistokuvaus/ → lisää FAQ-osio (ks. Part 2)
- Kaikki palvelusivut → lisää JSON-LD schema (ks. Part 3)

**Vaihe 2 — Uudet palvelusivut (luo tyhjästä)**
- `/lyhytvideo/` — ks. Part 2 täysi sisältöbrief
- `/valokuvaus/` — ks. Part 2 täysi sisältöbrief

Navigaatio-dropdown pitää päivittää sisältämään nämä 2 uutta linkkiä.

**Vaihe 3 — Kaupunkisivut (luo tyhjästä)**
Hääkuvaus:
- `/haakuvaus/jyvaskyla/`
- `/haakuvaus/tampere/`
- `/haakuvaus/helsinki/`
- `/haakuvaus/turku/`

Kiinteistökuvaus:
- `/kiinteistokuvaus/jyvaskyla/`
- `/kiinteistokuvaus/tampere/`
- `/kiinteistokuvaus/helsinki/`

Rakenne ks. Part 2 (kaupunkisivut-osio). JOKAINEN sivu on uniikki — ei copy-paste.

**Vaihe 4 — Uudet blogiartikkelit**
- `/blogi/parhaat-haapaikat-jyvaskylassa/`
- `/blogi/parhaat-haapaikat-tampereella/`

Rakenne ks. Part 2 (blogi-artikkelit-osio).

**Vaihe 5 — Sitemap & robots.txt**
Päivitä sitemap sisältämään kaikki uudet sivut (ks. Part 3).
Korvaa robots.txt (ks. Part 3).

---

## Ei-neuvoteltavat SEO-vaatimukset

Nämä PITÄÄ olla jokaisella sivulla:
- [ ] <title> täytetty (ei "Ruska Media | Ruska Media")
- [ ] <meta name="description"> täytetty
- [ ] <link rel="canonical"> osoittaa oikeaan URL:iin
- [ ] <html lang="fi"> (tai "en" englanninkielisillä)
- [ ] H1 sisältää pääkeywordin
- [ ] FAQ-osio palvelusivuilla (min 4 kysymystä)
- [ ] JSON-LD schema (Service + FAQ)
- [ ] Alt-teksti kaikissa kuvissa
- [ ] Internal links: kaupunkisivut ↔ pääsivut

---

## Kiellettyä

- ÄLÄ laita noindex-tageja palvelusivuille
- ÄLÄ käytä samaa title-tagia kahdella sivulla
- ÄLÄ jätä meta descriptionia tyhjäksi
- ÄLÄ käytä "Klikkaa tästä" linkkiteksteinä — käytä kuvaavia tekstejä
- ÄLÄ laita kaupunkisivuille identtistä tekstiä — kirjoita ainutlaatuinen johdanto jokaiselle

---

## Tarkistuslista ennen commitia

Aja nämä tarkistukset ennen jokaista git commitia:

```bash
# Build tarkistus
npm run build

# Tarkista title-tagit (ei duplikaatteja, ei tyhjiä)
grep -r "<title>" dist/ | sort

# Tarkista canonical-tagit
grep -r "canonical" dist/ | grep -v "node_modules"
```

---

## Kuvat

Käytä olemassa olevia kuvia WordPressin upload-kansiosta:
```
Hero:      https://ruskamedia.com/wp-content/uploads/2022/11/Ruska-Media-Videomarkkinointi.jpg
Kiinteistö: https://ruskamedia.com/wp-content/uploads/2022/11/Kiinteistöjen-valokuvaus-Ruska-Media.jpg
Häät (Turku): https://ruskamedia.com/wp-content/uploads/2022/11/Hääkuvaus-Turku-1.jpg
Häät (Tampere): https://ruskamedia.com/wp-content/uploads/2023/07/[hakee]
Joel:       https://ruskamedia.com/wp-content/uploads/2025/04/Joel-Nykanen-Ruska-Media-Event-yhteystiedot-675x900.jpg
Oskari:     https://ruskamedia.com/wp-content/uploads/2025/04/Oskari-Vattu-Ruska-Media-Event-yhteystiedot-675x900.jpg
```

Muista: alt-teksti jokaiseen kuvaan (ks. Part 4 ohje).

---

## Kysymykset ennen aloitusta

Jos jokin on epäselvää, kysy VAIN nämä asiat ennen aloitusta:
1. Mikä on kiinteistökuvauksen aloitushinta? (placeholder [X]€ brifeissä)
2. Mikä on lyhytvideon aloitushinta?
3. Onko "valokuvaus"-palvelu oma erillinen palvelu vai integroitu muihin?

Kaikki muu löytyy brief-tiedostoista.
