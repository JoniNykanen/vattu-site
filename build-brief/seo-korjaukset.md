# SEO-KORJAUKSET — Ruska Media
## Perustuu GSC-dataan + DataForSEO-analyysiin (2026-05-10)

Nämä muutokset EIVÄT koske designia tai layoutia.
Muutat vain: URL-slugit, title-tagit, H1-otsikot, meta descriptionit.

---

## KRIITTISET MUUTOKSET (tee ensin)

---

### 1. Nimeä sivu uudelleen: videomarkkinointi-yrityksille → videotuotanto

**Tiedosto:** `src/pages/videomarkkinointi-yrityksille.astro`
**Uusi tiedosto:** `src/pages/videotuotanto.astro`

**Miksi:** "videomarkkinointi yrityksille" = 0 hakua/kk. "videotuotanto" = 390 hakua/kk.

Muuta nämä:

```
URL:          /videomarkkinointi-yrityksille/  →  /videotuotanto/
title:        "Videomarkkinointi yrityksille — Yritysvideot & brändivideot | Ruska Media"
          →   "Videotuotanto yrityksille — Yritysvideot ja brändivideot | Ruska Media"
H1:           "Herätä huomio videolla"
          →   "Videotuotanto yrityksille"
canonical:    https://ruskamedia.com/videotuotanto/
```

Lisää myös redirect vanhoilta urlilta (jos Astro tukee):
`/videomarkkinointi-yrityksille/` → `/videotuotanto/`

---

### 2. Vaihda /valokuvaus/ pääavainsana

**Tiedosto:** `src/pages/valokuvaus/` (kansio tai .astro-tiedosto)

**Miksi:** "valokuvaus yrityksille" = 10 hakua/kk, MEDIUM kilpailu.
"henkilökuvaus" = 210 hakua/kk, LOW kilpailu.
"yrityskuvaus" = 110 hakua/kk, LOW kilpailu.
Sivun sisältö on jo oikea (henkilö- ja yrityskuvaus) — vain kohdistus muuttuu.

Muuta nämä:

```
title:        "Valokuvaus yrityksille — Yrityskuvaus & markkinointikuvaus | Ruska Media Jyväskylä"
          →   "Henkilökuvaus ja yrityskuvaus — Jyväskylä ja koko Suomi | Ruska Media"
H1:           "Valokuvaus yrityksille"
          →   "Henkilökuvaus ja yrityskuvaus"
meta desc:    "Ammattitaitoinen yrityskuvaus, henkilökuvaus ja markkinointikuvaus..."
          →   "Ammattitaitoinen henkilökuvaus ja yrityskuvaus Jyväskylässä ja koko Suomessa. Tiimikuvat, LinkedIn-kuvat, markkinointikuvat — Ruska Media."
canonical:    https://ruskamedia.com/valokuvaus/   ← pidä ennallaan, älä muuta URL:ia
```

URL pysyy `/valokuvaus/` — muutat vain title, H1 ja meta description.

---

### 3. Korjaa H1 kiinteistökuvaussivulla

**Tiedosto:** `src/pages/asunto-ja-kiinteistokuvaus.astro`

**Miksi:** H1 alkaa tällä hetkellä "Ruska Estate — Kiinteistökuvaus".
Google painottaa H1:n alkua. Brändinimi ei ole hakutermi.

Muuta vain H1:

```
H1 nyt:     "Ruska Estate — Kiinteistökuvaus"
H1 uusi:    "Kiinteistökuvaus ja asuntokuvaus — Ruska Estate"
```

Muuta ei tarvita tällä sivulla.

---

## NORMAALIMUUTOKSET

---

### 4. Korjaa hääkuvaustitle

**Tiedosto:** `src/pages/haakuvaus/index.astro` (tai vastaava)

**Miksi:** "Ruska Wedding Frames" titlessa vie tilaa — ei hakutermi.

```
title nyt:    "Hääkuvaus koko Suomessa — Ruska Wedding Frames by Joel Nykänen"
title uusi:   "Hääkuvaus koko Suomessa — hinnat ja paketit | Ruska Media"
meta desc:    lisää "hääkuvauksen hinta" tai "häävideo" tekstiin
```

H1 on OK — älä koske siihen.

---

### 5. Lisää Oulu hääkuvauksen kaupunkisivuihin

**Miksi:** "hääkuvaus oulu" = 110 hakua/kk, LOW kilpailu. Puuttuu kokonaan.

Luo: `src/pages/haakuvaus/oulu.astro`

Malli: kopioi `src/pages/haakuvaus/tampere.astro` ja muuta:
- URL → `/haakuvaus/oulu/`
- title → `Hääkuvaus Oulu — hinnat ja matkakulut | Ruska Media`
- H1 → `Hääkuvaus Oulu`
- canonical → `https://ruskamedia.com/haakuvaus/oulu/`
- Vaihda kaupunki-spesifi teksti: Oulu on ~370 km Jyväskylästä, matkakulut lasketaan lomakkeessa

Lisää myös linkki Oulu-sivulle `/haakuvaus/`-pääsivun kaupunkilistaan.

---

## EI MUUTOKSIA (nämä ovat kunnossa)

- `/lyhytvideo/` — title, H1 ja meta desc OK
- `/haakuvaus/` kaupunkisivut Jyväskylä, Tampere, Helsinki, Turku — olemassa ✓
- `/asunto-ja-kiinteistokuvaus/` kaupunkisivut Jyväskylä, Tampere, Helsinki — olemassa ✓
- FAQ-osiot jokaisella sivulla — OK ✓

---

## TARKISTUSLISTA ennen commitia

```bash
npm run build

# Tarkista että nämä löytyvät buildista:
grep -r "Videotuotanto yrityksille" dist/
grep -r "Henkilökuvaus ja yrityskuvaus" dist/
grep -r "Kiinteistökuvaus ja asuntokuvaus" dist/
grep -r "haakuvaus/oulu" dist/
```

---

## YHTEENVETO muutoksista

| Sivu | Muutos | Prioriteetti |
|------|--------|--------------|
| /videomarkkinointi-yrityksille/ | Nimeä uudelleen → /videotuotanto/, vaihda H1 | KRIITTINEN |
| /valokuvaus/ | Vaihda title + H1 → henkilökuvaus/yrityskuvaus | KRIITTINEN |
| /asunto-ja-kiinteistokuvaus/ | Korjaa H1 alkamaan avainsanalla | TÄRKEÄ |
| /haakuvaus/ | Korjaa title | NORMAALI |
| /haakuvaus/oulu/ | Luo uusi sivu | NORMAALI |
