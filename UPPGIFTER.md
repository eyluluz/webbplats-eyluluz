# UPPGIFTER — Bygg en webbplats steg för steg

## Syfte
- Förstå HTML-struktur: `<header>`, `<nav>`, `<main>`, `<section>`, `<footer>` och `<div>` som boxar.
- Lära dig om CSS-boxmodellen: margin, border, padding.
- Göra sidan mer visuell: hover, transition, box-shadow och enkla animationer.
- Visa återanvändning: flera sidor med samma header/nav/footer.
- Bygga en webbplats stegvis så att du förstår HTML-struktur, boxmodellen och enkla visuella effekter.
- Lära dig git-flödet (add, commit, push) och hur du publicerar med Netlify via GitHub ("New site from Git").
- Få din första riktiga utvecklarupplevelse: från kod till publik webbplats som du kan visa för andra.

## Struktur och tidsuppskattning (total: 3–4 timmar)
- STEG 0: Förberedelser (10 min)
- STEG 1: Grundskal och git (30 min)
- STEG 2: Header och footer (25 min)
- STEG 3: Navigation med hover och fokus (25 min)
- STEG 4: Huvudinnehåll och projektboxar (50 min)
- STEG 5: Fler sidor och återanvändning (20 min)
- STEG 6: Visuella förbättringar (20 min)
- STEG 7: Responsivitet (20 min)
- STEG 8: Publicera på GitHub och Netlify (20 min)

## Checklist (vad du lämnar in)
- `index.html` (färdig sida enligt STEG 7)
- `kontakt.html` (en andra sida med kontaktinfo)
- `style.css` (alla stilar)
- `reflektion.md` (svar på frågorna i varje steg)
- Ett GitHub-repo (publikt) med publicerad version på Netlify

---

## STEG 0 — Förberedelser (10 min)
1) Klona Classroom-repot till din `DEV`-katalog:
   ```powershell
   cd C:\Users\<ditt-användarnamn>\DEV
   git clone <Classroom-länk>
   cd <repo-namn>
   ```
   (Byt ut `<Classroom-länk>` mot den länk du får i uppgiften, och `<repo-namn>` mot namnet på mappen som skapas - det är vanligtvis `te4-exercise-html-layout-stepwise-<ditt-användarnamn>`.)
2) Öppna mappen i VS Code.
3) Bekanta dig med filerna som redan finns: `index.html`, `style.css`, `kontakt.html`, `reflektion.md`, `UPPGIFTER.md`.

> **Varför klona?** Genom att klona repot startar du med rätt filstruktur och koppling till GitHub Classroom. Det är precis så riktiga utvecklare börjar jobba på nya projekt - klona, koda, pusha tillbaka!

## STEG 1 — Grundskal och git (30 min)
1) Kontrollera att din `index.html` innehåller rätt grundskal. Den ska se ut så här:
```html
<!DOCTYPE html>
<html lang="sv">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Stegvis Övning — Start</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div id="root">
    <!-- Här bygger du stegvis enligt UPPGIFTER.md -->
  </div>
</body>
</html>
```

2) Gör din första commit (Commandprompten/terminalen i VS Code, kör i projektmappen):
```powershell
git status
git add .
git commit -m "STEG 1: Grundskal för övning"
git status
git log --oneline
```

> **Protip:** Tänk på commit-meddelandet som en kort förklaring till framtida-dig själv (eller teamet) om vad du gjorde. I riktiga projekt läser utvecklare dessa meddelanden dagligen!

3) När du har gjort din första commit, pusha ändringarna till GitHub:
```powershell
git push
```

> **Varför pusha nu?** I den här övningen pushar vi efter varje steg för att du ska lära dig git-flödet och så att GitHub Classroom kan följa dina framsteg. I riktiga projekt skulle du normalt testa mer lokalt först, men här fokuserar vi på att lära oss verktygen!

## STEG 2 — Header och footer (25 min)
1) I `index.html`, direkt under `<div id="root">`, klistra in (kopiera exakt):
```html
<header>
  <div class="container header-inner">
    <h1>Mitt Namn / Min Webbplats</h1>
    <p class="subtitle">En enkel portfolio — byggs stegvis</p>
  </div>
</header>

<footer>
  <div class="container footer-inner">
    <p>© 2025 — Ditt Namn — <a href="mailto:kontakt@example.com">kontakt@example.com</a></p>
  </div>
</footer>
```

2) I `style.css` klistra in följande (kopiera exakt):
```css
/* HEADER + FOOTER */
header { background:#4a90e2; color:#fff; padding:20px 0; }
.header-inner { max-width:900px; margin:0 auto; padding:0 15px; }
header h1 { margin:0; }
header .subtitle { margin:4px 0 0; font-size:0.95rem; opacity:0.9; }

footer { background:#222; color:#fff; padding:10px 0; }
.footer-inner { max-width:900px; margin:0 auto; padding:0 15px; text-align:center; }
```

3) Spara och commit:
```powershell
git add index.html style.css
git commit -m "STEG 2: Lagt till header och footer med grundstilar"
```

STEG 3 — Navigation med hover och fokus (25 min)
1) I `index.html`, efter `</header>` (men före `<footer>`), klistra in:
```html
<nav>
  <div class="container nav-inner">
    <a href="index.html" class="nav-link">Hem</a>
    <a href="om.html" class="nav-link">Om mig</a>
    <a href="projekt.html" class="nav-link">Projekt</a>
    <a href="kontakt.html" class="nav-link">Kontakt</a>
  </div>
</nav>
```
> **Obs:** De andra sidorna (`om.html`, `projekt.html`) skapar vi i STEG 5. För nu får länkarna vara "trasiga" - det är normalt under utveckling!

2) I `style.css` lägg till:
```css
/* NAV */
nav { background:#333; }
.nav-inner { max-width:900px; margin:0 auto; padding:8px 15px; }
.nav-link { color:#fff; margin-right:18px; text-decoration:none; padding:6px 8px; border-radius:4px; display:inline-block; }
.nav-link:hover, .nav-link:focus { background:rgba(255,255,255,0.08); transform:translateY(-2px); transition:all 150ms ease; }
.nav-link:focus { outline:2px solid #fff; outline-offset:3px; }
```

3) Spara och commit:
```powershell
git add index.html style.css
git commit -m "STEG 3: Lagt till nav med hover och fokus-stilar"
```

STEG 4 — Huvudinnehåll och projektboxar (50 min)
1) I `index.html`, mellan nav och footer, klistra in:
```html
<main>
  <div class="container">
    <section id="about">
      <h2>Om mig</h2>
      <div class="info-box">
        <p>Skriv en kort presentation.</p>
      </div>
    </section>

    <section id="projects">
      <h2>Projekt</h2>
      <div class="projects-grid">
        <div class="project-box">
          <h3>Projekt 1</h3>
          <p>Kort beskrivning.</p>
        </div>
        <div class="project-box">
          <h3>Projekt 2</h3>
          <p>Kort beskrivning.</p>
        </div>
      </div>
    </section>
  </div>
</main>
```

2) I `style.css` lägg till:
```css
/* MAIN + BOXES */
main { background:#fff; margin:20px auto; max-width:900px; padding:20px; box-shadow:0 4px 10px rgba(0,0,0,0.06); }
.info-box { border:2px solid #4a90e2; padding:12px; background:#eaf6ff; }
.projects-grid { display:flex; gap:18px; flex-wrap:wrap; }
.project-box { flex:1 1 240px; border:2px solid #333; padding:12px; background:#fafafa; transition:box-shadow 200ms ease, transform 200ms ease; }
.project-box:hover { box-shadow:0 8px 20px rgba(0,0,0,0.12); transform:translateY(-6px); }
```

3) Spara och commit:
```powershell
git add index.html style.css
git commit -m "STEG 4: Lagt till main och projektboxar med hover-effekt"
```

STEG 5 — Fler sidor och återanvändning (20 min)
1) Skapa tre nya HTML-filer genom att kopiera `index.html`:
   - `kontakt.html` - ersätt `<main>` med kontaktinformation
   - `om.html` - ersätt `<main>` med information om dig själv
   - `projekt.html` - ersätt `<main>` med en lista över dina projekt
   
2) **Viktigt:** Säkerställ att `<header>`, `<nav>` och `<footer>` är **exakt identiska** i alla fyra filer. Endast `<main>`-innehållet ska skilja sig åt.

> **Varför samma header/nav/footer?** Det här är hur riktiga webbplatser fungerar - konsistent navigation och layout skapar bra användarupplevelse. Användare känner igen sig på alla sidor!

3) Spara och commit:
```powershell
git add kontakt.html om.html projekt.html
git commit -m "STEG 5: Skapat alla sidor med återanvänd navigation och layout"
```

STEG 6 — Visuella förbättringar (20 min)
1) I `style.css` lägg till extra effekter (kopiera exakt):
```css
/* EXTRA EFFEKTER */
.project-box { transition: transform 200ms ease, box-shadow 200ms ease; }
.project-box:focus-within { box-shadow:0 10px 30px rgba(0,0,0,0.15); transform:translateY(-8px); }
```

2) Spara och commit:
```powershell
git add style.css
git commit -m "STEG 6: Lagt till extra visuella effekter"
```

STEG 7 — Responsivitet (20 min)
1) Lägg till media queries längst ner i `style.css`:
```css
/* RESPONSIV */
@media (max-width:600px) {
  .projects-grid { flex-direction:column; }
  .nav-inner { text-align:center; }
}
```

> **Vad gör detta?** Media queries låter oss ändra CSS baserat på skärmstorlek. På skärmar mindre än 600px (mobiler) staplar vi projekt-rutorna vertikalt istället för horisontellt, och centrerar navigationen.

2) **Testa responsiviteten:**
   - Öppna `index.html` i webbläsaren
   - Högerklicka → "Inspektera" (eller tryck F12)
   - Klicka på mobil-ikonen (📱) eller tryck Ctrl+Shift+M
   - Prova olika skärmstorlekar: iPhone, iPad, Desktop
   - Se hur layouten ändras vid 600px-gränsen

> **Varför är detta viktigt?** Över 50% av all webbtrafik kommer från mobiler! En sida som inte fungerar på mobil tappar hälften av sina besökare.

3) Spara och commit:
```powershell
git add style.css
git commit -m "STEG 7: Lagt till responsiva media queries"
```

STEG 8 — Publicera och verifiera i Netlify (20 min)
1) Pusha koden till GitHub (om inte redan gjort):
```powershell
git push
```

2) Publicera på Netlify via GitHub-anslutning (New site from Git):
   - Gå till https://app.netlify.com och logga in.
   - Klicka "New site from Git".
   - Välj GitHub som provider och välj **ditt eget Classroom-repo** (inte lärarens eller originalet). Repo-namnet är unikt för dig, t.ex. `TE4-Academy/te4-exercise-html-layout-stepwise-<ditt-användarnamn>`.
   - Välj branch `main`. Lämna Build command och Publish directory tomma för denna enkla statiska sida.
   - Klicka "Deploy site".

> **Magiskt ögonblick!** Nu kommer din kod att bli en riktig webbplats som vem som helst kan besöka. Det här är samma process som används av miljontals utvecklare världen över.

3) Testa deploy: gör en ändring, commit och push:
   - Lägg till en länk till din GitHub-profil i footern, bredvid copyright och mail.
   - Exempel (i `index.html` och `kontakt.html`):
     ```html
     <p>© 2025 — Ditt Namn — <a href="mailto:kontakt@example.com">kontakt@example.com</a> — <a href="https://github.com/ditt-github-användarnamn" target="_blank">GitHub</a></p>
     ```
   - Spara ändringen och kör:
     ```powershell
     git add .
     git commit -m "Test: trigger Netlify deploy + GitHub-länk i footer"
     git push
     ```

> **Utvecklarflöde live!** Nu ser du hela kedjan: kod → commit → push → automatisk deploy. Det här är hur modern webbutveckling fungerar!

4) Bekräfta i Netlify UI att en build körs och att site publicerats.

## AVSLUTNING & INLÄMNING — GitHub Classroom (viktig)
1) Arbeta i det tilldelade Classroom-repot och pusha alla ändringar till `main`.
2) Vänta på att Classroom kör autograding — se resultat på Classroom-uppgiftens sida.
3) Bekräfta att Netlify har byggt och publicerat din sida (kolla Site deploys i Netlify UI).
4) Dela den publika repo-länken till mig via Discord som dm.
5) När autograding visar "passed" och jag har godkänt (via Discord), är uppgiften inlämnad.

> **Grattis!** Du har nu gått genom hela utvecklarflödet från kloning till publik webbplats. Det här är exakt samma process som används i riktiga utvecklarjobb - du är på god väg!


