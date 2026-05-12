# Sivuston päivitysohje — Ruska Media

> Tämä ohje on tarkoitettu tilanteeseen, jossa haluat päivittää sivustoa itse ilman erillistä kehittäjää.

---

## Mitä tarvitset

### 1. GitHub-tili — ilmainen
Sivuston koodi on jo GitHubissa. Tarvitset tilin jotta pääset siihen käsiksi.
👉 [github.com](https://github.com) → Create account

### 2. Vercel-tili — ilmainen
Vercel deployaa sivuston automaattisesti aina kun koodi päivittyy GitHubissa. Ei tarvetta manuaalisiin julkaisuihin.
👉 [vercel.com](https://vercel.com) → Sign up with GitHub

### 3. Anthropic API-avain — pay-as-you-go
Claude Code tarvitsee tämän toimiakseen. Se ei kuulu Claude.ai Pro -tilaukseen — se on erillinen.
👉 [console.anthropic.com](https://console.anthropic.com) → API Keys → Create key

**Hinta:** Maksat vain käytöstä. Tyypillinen päivitysistunto (esim. tekstejä, kuvia, pieniä muutoksia) maksaa **2–8 €**. Ei kuukausimaksua jos et käytä.

### 4. Claude Code — ilmainen työkalu
Asennetaan terminaaliin kerran:
```
npm install -g @anthropic-ai/claude-code
```
Vaatii Node.js:n (ilmainen): [nodejs.org](https://nodejs.org)

---

## Miten päivitys tapahtuu käytännössä

1. Avaat terminaalin ja navigoit sivuston kansioon
2. Kirjoitat `claude` — Claude Code käynnistyy
3. Kerrot mitä haluat muuttaa suomen kielellä, esimerkiksi:
   - *"Vaihda hääkuvauksen hinta 2 500 eurosta 2 800 euroon"*
   - *"Lisää uusi arvostelu: nimi Matti Virtanen, teksti: ..."*
   - *"Vaihda etusivun hero-teksti"*
4. Claude tekee muutokset tiedostoihin
5. Kirjoitat `git push` — Vercel deployaa automaattisesti ~1 minuutissa

---

## Kustannusarvio

| Tilanne | Arvioitu hinta |
|--------|---------------|
| Pieni tekstimuutos (hinta, teksti) | ~1–2 € |
| Useampi muutos samassa istunnossa | ~3–6 € |
| Isompi kokonaisuus (uusi sivu, FAQ-päivitys) | ~8–15 € |

Anthropic laskuttaa luettujen + kirjoitettujen "tokenien" mukaan. Yksi token ≈ yksi sana. Tyypillinen istunto ei ylitä 5 €.

---

## Mitä EI tarvita

- ❌ Erillistä hosting-maksua (Vercel ilmainen pienille sivustoille)
- ❌ Claude.ai Pro -tilausta (API-avain riittää)
- ❌ Ohjelmointitaitoja
- ❌ Manuaalista FTP-siirtoa tai WordPress-kirjautumista

---

## Mitä kannattaa tietää ennen kuin aloitat

**Hyvä:** tekstimuutokset, hinnat, FAQ:t, arvostelut, kuvien vaihdot URL-osoitteella, uudet sivut samalla rakenteella.

**Pyydä apua:** isommat rakennemuutokset, uudet toiminnallisuudet, lomakkeiden muokkaus, SEO-strategia.

**Tärkeää:** Tee aina muutokset `git push` kautta — älä muokkaa tiedostoja suoraan GitHubissa käsin, jotta koodin historia pysyy siistinä.

---

## Yhteenveto kustannuksista vuodessa

Jos päivität sivustoa kerran kuussa (esim. hinnat, tekstit, arvostelut):

| Kuluerä | Hinta |
|--------|-------|
| GitHub | 0 € / vuosi |
| Vercel | 0 € / vuosi |
| Anthropic API (~5 € × 12 kk) | ~60 € / vuosi |
| **Yhteensä** | **~60 € / vuosi** |

Vertailu: WordPress-ylläpito + kehittäjä tyypillisesti 500–2 000 € / vuosi.

---

*Päivitetty: toukokuu 2026*
