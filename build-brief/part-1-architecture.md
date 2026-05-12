# Ruska Media — Astro Build Brief
## Part 1: Site Architecture & URL Structure

> Syötä tämä Claude-sessiolle ennen rakentamista.
> Pohja: C:/Users/jonin/Projects/ruska-media (Astro 5 + Tailwind)

---

## Yritys

**Nimi:** Ruska Media (Ruska Tuotanto Oy)
**URL:** https://ruskamedia.com
**Sijainti:** Jyväskylä (toimii koko Suomessa)
**Tiimi:** Joel Nykänen (visuaalisen sisällön johtaja), Oskari Vattu (luova tuottaja)
**Sisaryhtiö:** Ruska Event (https://ruskaevent.com)

---

## Palvelut (5 kpl)

1. **Lyhytvideo** — some-videot yrityksille (TikTok, Reels, Shorts)
2. **Valokuvaus** — yrityskuvaus, markkinointikuvaus, henkilökuvaus
3. **Filmi & Video** — yritysvideot, brändivideot, rekrytointivideot
4. **Ruska Estate** — kiinteistökuvaus, asuntokuvaus, drone, digistailaus
5. **Wedding Frames by Joel Nykänen** — hääkuvaus ja häävideo

---

## URL-rakenne (KAIKKI sivut rakennettava)

```
/ ...................... Etusivu
/lyhytvideo/ .......... Lyhytvideo yrityksille (PUUTTUU — luo uusi)
/valokuvaus/ .......... Valokuvaus yrityksille (PUUTTUU — luo uusi)
/videomarkkinointi-yrityksille/ ... Filmi & Video (olemassa, uudelleenkirjoita)
/asunto-ja-kiinteistokuvaus/ ...... Ruska Estate (olemassa, paranna)
/haakuvaus/ ........... Wedding Frames (olemassa, paranna)

── Hääkuvaus-kaupunkisivut (KAIKKI PUUTTUVAT — luo uudet):
/haakuvaus/jyvaskyla/
/haakuvaus/tampere/
/haakuvaus/helsinki/
/haakuvaus/turku/

── Kiinteistökuvaus-kaupunkisivut (KAIKKI PUUTTUVAT — luo uudet):
/kiinteistokuvaus/jyvaskyla/
/kiinteistokuvaus/tampere/
/kiinteistokuvaus/helsinki/

── Blogi (olemassa, lisää artikkelit):
/blogi/
/blogi/haakuvaaja-miksi-palkata-ammattikuvaaja-haihin/ (päivitä)
/blogi/yritysvideo/ (päivitä)
/blogi/kiinteistokuvaus-milloin-kaantya-ammattilaisen-puoleen/ (päivitä)
/blogi/parhaat-haapaikat-jyvaskylassa/ (PUUTTUU — luo uusi)
/blogi/parhaat-haapaikat-tampereella/ (PUUTTUU — luo uusi)

── Muut:
/tiimi-yhteystiedot/
/en/ (englanninkieliset sivut — säilytä rakenne)
/en/wedding-photography/
/en/real-estate-photography/
/en/video-marketing-for-businesses/
/en/team-contact/
```

---

## Navigaatiorakenne

```
Header nav:
├── Palvelut (dropdown)
│   ├── Lyhytvideo → /lyhytvideo/
│   ├── Valokuvaus → /valokuvaus/
│   ├── Filmi & Video → /videomarkkinointi-yrityksille/
│   ├── Ruska Estate → /asunto-ja-kiinteistokuvaus/
│   └── Wedding Frames → /haakuvaus/
├── Blogi → /blogi/
├── Tiimi → /tiimi-yhteystiedot/
└── In English → /en/

Footer:
├── Kolumni 1: Logo + lyhyt kuvaus + some-linkit
├── Kolumni 2: Palvelut-linkit
├── Kolumni 3: Yhteystiedot (joel@ruskamedia.com, 040 536 9809)
└── Copyright: 2026 © Ruska Tuotanto Oy
```

---

## Design system (säilytä olemassa olevasta suunnitelmasta)

```css
--green: #3a4a35
--green-dark: #2a3727
--cream: #f7f5f0
--gray-light: #f0eeea
--text: #1a1a18
--text-muted: #5a5a5a
--white: #ffffff

Font heading: Cormorant Garamond, 400/600
Font body: Inter, 400/500
Max width: 1280px
```

---

## Kriittiset tekniset vaatimukset

1. **Canonical tag** — jokainen sivu: `<link rel="canonical" href="https://ruskamedia.com/[slug]/" />`
2. **lang="fi"** — kaikilla suomenkielisillä sivuilla, lang="en" englanninkielisillä
3. **Viewport** — `<meta name="viewport" content="width=device-width, initial-scale=1.0" />`
4. **Robots** — kaikki sivut: index, follow (ei noindex missään palvelusivulla)
5. **Sitemap** — generoi automaattisesti Astron sitemap-integraatiolla
6. **Redirect** — `www.ruskamedia.com` → `ruskamedia.com` (1-hop, ei ketjua)
7. **HTTPS** — kaikki linkit https://, ei mixed content
8. **Kuvat** — WebP-formaatti, lazy load, alt-teksti jokaiseen kuvaan
9. **Trailing slash** — konsistentisti jokaisessa URL:ssa (joko aina tai ei koskaan — valitse yksi)
