# Innehållsguide – Lönelots hemsida

Den här guiden beskriver hur du uppdaterar hemsidans innehåll via GitHub.
Du behöver **inte** kunna HTML eller programmering.

---

## Lägga till en nyhet

1. Gå till repots GitHub-sida
2. Navigera till mappen `src/content/news/`
3. Klicka **Add file** → **Create new file**
4. Namnge filen, t.ex. `2026-05-nyhet.md` (använd datum och kort beskrivning)
5. Klistra in följande mall och fyll i dina uppgifter:

```markdown
---
title: "Rubrik på nyheten"
date: 2026-05-01
summary: "En kort sammanfattning som visas på startsidan."
---

Här skriver du nyhetstext. Du kan använda:

- Punktlistor
- **Fetstil**
- *Kursiv stil*

## Underrubriker

Skriv fritt. Varje stycke separeras med en tom rad.
```

6. Klicka **Commit changes** (grön knapp)
7. Hemsidan uppdateras automatiskt inom ca 1 minut

### Tips
- `title` och `date` är obligatoriska
- `summary` är valfritt men rekommenderas (visas som förhandsgranskning)
- Datumet måste skrivas som `ÅÅÅÅ-MM-DD`

---

## Ladda upp ett dokument (PDF)

1. Gå till mappen `public/documents/` i repot
2. Klicka **Add file** → **Upload files**
3. Dra in PDF-filen
4. Klicka **Commit changes**
5. Dokumentet blir tillgängligt på `lonelotsarna.se/documents/filnamn.pdf`

### Visa dokumentet i dokumentlistan

För att dokumentet ska synas i listan på hemsidan behöver du (eller Emil) lägga till det i filen `src/components/Documents.astro`. Lägg till en ny rad i listan:

```
{ name: 'Dokumentnamn', file: 'filnamn.pdf' },
```

---

## Byta en bild

1. Gå till mappen `public/images/` i repot
2. Klicka **Add file** → **Upload files**
3. Ladda upp den nya bilden med **samma filnamn** som den gamla
4. Klicka **Commit changes**
5. Bilden uppdateras automatiskt

---

## Ta bort en nyhet

1. Gå till `src/content/news/`
2. Klicka på filen du vill ta bort
3. Klicka på papperskorgsikonen (🗑️) uppe till höger
4. Klicka **Commit changes**

---

## Vanliga frågor

**Hur lång tid tar det innan ändringen syns?**
Ca 1 minut. Cloudflare Pages bygger om sajten automatiskt vid varje commit.

**Kan jag förstöra något?**
Nej, inte på riktigt. Git sparar all historik — om något går fel kan vi alltid gå tillbaka till en tidigare version.

**Vad är frontmatter?**
Det är texten mellan `---` i toppen av Markdown-filen. Där anger du titel, datum och andra metadata.
