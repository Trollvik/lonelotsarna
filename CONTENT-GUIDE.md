# Förvaltningsguide – lonelotsarna.se

Den här guiden beskriver hur sajten fungerar och hur olika personer kan göra ändringar.
Du behöver **inte** kunna HTML eller programmering för att redigera texter.

---

## Översikt

| Vad | Var |
|-----|-----|
| Sajten (live) | https://trollvik.github.io/lonelotsarna/ |
| Engelska sidan | https://trollvik.github.io/lonelotsarna/en/ |
| Repot (kod) | https://github.com/Trollvik/lonelotsarna |
| Analytics | https://lonelotsarna.goatcounter.com |
| Nedladdningar (releases) | https://github.com/Trollvik/lonelotsarna/releases |

**Sajten deployas automatiskt** varje gång någon sparar en ändring i repot. Det tar ca 30 sekunder.

---

## Roller

### Marie & Johanna (redaktörer)
- Kan redigera texter direkt i webbläsaren via GitHub
- Kan ladda upp nya PDF-dokument
- Kan byta bilder

### Jonas (utvecklare, Analys Lönelots)
- Laddar upp nya versioner av programmet via GitHub Releases
- Nedladdningslänkarna på sajten pekar alltid på senaste versionen

### Emil (teknisk förvaltare)
- Större strukturella ändringar (nya sidor, layout, design)
- DNS-hantering när domänen ska pekas om

---

## Redigera text på sajten

### Steg för steg

1. Gå till https://github.com/Trollvik/lonelotsarna
2. Navigera till filen du vill ändra (se "Var finns vad?" nedan)
3. Klicka på **pennikonen** (✏️) uppe till höger i filen
4. Gör dina ändringar i texten
5. Klicka den gröna knappen **"Commit changes"**
6. Sajten uppdateras automatiskt inom ca 30 sekunder

### Var finns vad?

| Innehåll | Fil |
|----------|-----|
| **Startsidan** — hero-text | `src/components/Hero.astro` |
| **Om oss** — föreningstext, länkar | `src/components/About.astro` |
| **Analys Lönelots** — brödtexter | `src/pages/analys-lonelots.astro` |
| **Engelska startsidan** | `src/pages/en/index.astro` |
| **Engelska Analys Lönelots** | `src/pages/en/analys-lonelots.astro` |

### Vad du kan redigera själv

| Fil | Vad du kan ändra |
|-----|------------------|
| `src/components/Hero.astro` | Rubriken och texten på startsidan |
| `src/components/About.astro` | Texterna under "Om oss" |
| `src/data/reports.json` | Svenska rapportlistan (titel, år, sammanfattning, filnamn) |
| `src/data/reports-en.json` | Engelska rapportlistan (samma format) |
| `src/pages/analys-lonelots.astro` | Brödtext i accordion-stegen (Arbetsvärdering, Lönekartläggning, FAQ) |
| `src/pages/en/index.astro` | Engelska texter (Om oss, Kontakt) |
| `src/pages/en/analys-lonelots.astro` | Engelska brödtexter i accordion-stegen |

### Filer du INTE ska redigera

| Fil | Varför |
|-----|--------|
| `src/layouts/BaseLayout.astro` | Styr navigation, footer och SEO för hela sajten. Fel här kraschar alla sidor. |
| `src/components/Reports.astro` | Styr hur rapporterna visas. Datan redigeras i `src/data/reports.json`. |
| `src/pages/index.astro` | Innehåller bara import-rader — texterna redigeras i komponentfilerna ovan. |
| Nedladdningslänkar i analys-sidorna | URL:erna måste matcha filnamnen i GitHub Releases exakt. |

**Vill du ändra något i dessa filer?** Kontakta Emil.

### Tips för redigering

- Redigera bara **texten** — rör inte koden runt om (saker som `class="..."` eller `<div>`)
- Om du bara vill ändra ett ord eller en mening, använd webbläsarens sökfunktion (Ctrl+F) för att hitta rätt ställe
- Varje ändring du sparar syns live inom 30 sekunder
- Om något går fel kan vi alltid gå tillbaka — Git sparar all historik

---

## Lägga till en ny rapport

Rapportlistan styrs av filen `src/data/reports.json`. Varje rapport har fyra fält:

```json
{
  "title": "Rapportens titel",
  "year": "2025",
  "summary": "En kort sammanfattning av rapporten.",
  "file": "/documents/rapportens-titel.pdf"
}
```

### Steg för steg

1. Ladda först upp PDF-filen till `public/documents/` (se nästa avsnitt)
2. Öppna `src/data/reports.json` på GitHub
3. Klicka pennikonen (✏️)
4. Kopiera blocket ovan och klistra in det **överst** i listan (efter första `[`)
5. Ändra titel, år, sammanfattning och filnamn
6. **Viktigt:** Filnamnet i `file` ska vara med bindestreck och små bokstäver, t.ex. `rapportens-titel.pdf`
7. Klicka **Commit changes**

**Tips:** Om sidan kraschar efter din ändring har du troligen glömt ett komma eller en `"`. Kontakta Emil så fixar han det snabbt.

### Svenska vs engelska

| Språk | Fil |
|-------|-----|
| Svenska | `src/data/reports.json` |
| Engelska | `src/data/reports-en.json` |

Stegen är identiska för båda. Redigera rätt fil beroende på språk.

---

## Ladda upp ett nytt dokument (PDF)

1. Gå till mappen `public/documents/` i repot
2. Klicka **Add file** → **Upload files**
3. Dra in PDF-filen
4. Klicka **Commit changes**
5. Dokumentet finns nu på `[sajt-url]/documents/filnamn.pdf`

**OBS:** Dokumentet blir tillgängligt via URL men syns inte automatiskt i rapportlistan. För att lägga till det i listan, följ instruktionerna under "Lägga till en ny rapport" ovan.

---

## Byta en bild

1. Gå till mappen `public/images/` i repot
2. Klicka **Add file** → **Upload files**
3. Ladda upp den nya bilden med **samma filnamn** som den gamla
4. Klicka **Commit changes**
5. Bilden uppdateras automatiskt

---

## Ladda upp ny version av Analys Lönelots (Jonas)

Installationsfilerna hostas via GitHub Releases (inte i repot — de är för stora).

### Steg för steg

1. Gå till https://github.com/Trollvik/lonelotsarna/releases
2. Klicka **"Draft a new release"**
3. Ange en ny tag, t.ex. `v7.2`
4. Skriv en kort titel, t.ex. "Analys Lönelots v7.2"
5. Dra in de fyra installationsfilerna:
   - `LoneLots-X.X.X.exe` (PC, svenska)
   - `LoneLots-X.X-EN.exe` (PC, engelska)
   - `lonelots-mac-X.X-arm64.dmg` (Mac, svenska)
   - `lonelots-mac-X.X-arm64-EN.dmg` (Mac, engelska)
6. Klicka **"Publish release"**

### Viktigt om filnamn

Nedladdningslänkarna på sajten pekar på specifika filnamn. **Om filnamnen ändras vid en ny version måste Emil uppdatera länkarna i koden.** Meddela Emil när nya filer laddas upp med andra filnamn. Nuvarande filnamn:

| Språk | PC | Mac |
|-------|-----|-----|
| Svenska | `LoneLots-7.1.1.exe` | `lonelots-mac-7.1-arm64.dmg` |
| Engelska | `LoneLots-7.1-EN.exe` | `lonelots-mac-7.1-arm64-EN.dmg` |

Länkarna finns i:
- `src/pages/analys-lonelots.astro` (svenska)
- `src/pages/en/analys-lonelots.astro` (engelska)

Sök efter `releases/latest/download/` för att hitta dem.

---

## Analytics

Sajten använder GoatCounter (cookie-fritt, GDPR-vänligt).

- **Dashboard:** https://lonelotsarna.goatcounter.com
- Visar: sidvisningar, besökare, referrers, länder, enheter
- **Nedladdningsstatistik** för programmet: https://github.com/Trollvik/lonelotsarna/releases

---

## Teknisk information

| Teknologi | Användning |
|-----------|-----------|
| Astro 6 | Statisk sajt-generator (bygger HTML, ingen JavaScript till besökare) |
| Tailwind CSS 4 | Styling |
| GitHub Pages | Hosting (gratis) |
| GitHub Actions | Automatisk deploy vid varje commit |
| GitHub Releases | Hosting av installationsfiler för Analys Lönelots |
| GoatCounter | Webbanalys (cookie-fritt) |

### Filstruktur

```
src/
├── components/        # Återanvändbara delar (hero, om oss, rapporter)
├── data/              # Rapportlista (reports.json)
├── layouts/           # Sidlayout (navigation, footer)
├── pages/             # Varje fil = en sida
│   ├── index.astro          # Startsidan (svenska)
│   ├── analys-lonelots.astro # Analys Lönelots (svenska)
│   └── en/
│       ├── index.astro          # English homepage
│       └── analys-lonelots.astro # Lonelots Tool (English)
└── styles/            # CSS

public/
├── documents/         # PDF-filer (rapporter, handbok)
└── images/            # Bilder (logga, hero, etc.)
```

---

## Vanliga frågor

**Hur lång tid tar det innan en ändring syns?**
Ca 30 sekunder. GitHub Actions bygger om sajten automatiskt.

**Kan jag förstöra något?**
Nej. Git sparar all historik — vi kan alltid gå tillbaka till en tidigare version.

**Vad händer om jag råkar ändra fel?**
Kontakta Emil. Han kan återställa filen till en tidigare version med ett kommando.

**Behöver jag installera något?**
Nej. All redigering sker via webbläsaren på github.com.
