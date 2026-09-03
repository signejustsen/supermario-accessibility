# Horiseon

# Web Accessibility, Web Performance og Responsive Webdesign

**Semester:** 3. semester

> Opgaven kan løses med Visual Studio Code, Google Chrome, Chrome DevTools, Lighthouse, tastatur og eventuelt HeadingsMap.

---

## Opgavebeskrivelse

I denne øvelse skal du arbejde med et eksisterende website for det digitale bureau **Horiseon**.

Horiseon arbejder blandt andet med:

- Search Engine Optimization
- Online Reputation Management
- Social Media Marketing
- Lead Generation
- Brand Awareness
- Cost Management

Du skal **ikke bygge websitet om fra bunden**.

Formålet er, at du lærer at analysere og forbedre eksisterende HTML og CSS trin for trin.

Opgaven består af tre dele:

```text
DEL 1
Web Accessibility
        ↓
DEL 2
Web Performance
        ↓
DEL 3
Responsive Webdesign med CSS Flexbox
```

Du skal bruge **Chrome DevTools** og **Lighthouse** til at dokumentere effekten af dine ændringer.

> **Vigtigt:** Foretag ikke alle ændringer på én gang. Test løbende, så du kan se, hvilken betydning de enkelte ændringer har.

---

## Projektmappe

Starterprojektet består af:

```text
project/
│
├── README.md
├── index.html
│
├── css/
│   └── style.css
│
├── images/
│   ├── brand-awareness.png
│   ├── cost-management.png
│   ├── digital-marketing-meeting.jpg
│   ├── lead-generation.png
│   ├── online-reputation-management.jpg
│   ├── search-engine-optimization.jpg
│   └── social-media-marketing.jpg
│
└── README-assets/
    └── horiseon-responsive-reference.png
```

> **Vigtigt:** I `index.html` skal stylesheetet refereres som `./css/style.css`, og HTML-billederne skal refereres fra `./images/`. Fra `css/style.css` refereres hero-billedet som `../images/digital-marketing-meeting.jpg`.

---

## GitHub og løbende commits

Du skal arbejde med projektet i dit eget GitHub-repository.

Under hele opgaven skal du lave **løbende og beskrivende commits**, så din arbejdsproces og udviklingen af projektet kan følges.

Du skal som minimum:

- lave **ét commit for hver opgave**
- committe løbende, efterhånden som du løser og tester opgaverne
- skrive en beskrivende commit-besked, der fortæller, hvad du har ændret

Da opgavesættet består af 29 opgaver, skal dit repository derfor indeholde **mindst 29 relevante commits**.

---

# DEL 1 – WEB ACCESSIBILITY

I første del skal du forbedre websitets HTML og CSS med fokus på webtilgængelighed.

Målet er:

```text
Lighthouse Accessibility: 100
```

En Lighthouse-score på 100 betyder dog ikke, at websitet automatisk er fuldt tilgængeligt.

Du skal derfor kombinere Lighthouse med:

- manuel tastaturtest
- kontrol af headingstruktur
- vurdering af `alt`-tekster
- kontrol af farvekontrast
- zoom og reflow
- HTML-validering

---

# Opgave 1 – Lav en Lighthouse Accessibility-baseline

Inden du ændrer noget i koden, skal du måle sidens nuværende Accessibility-score.

## Sådan gør du

1. Åbn `index.html` i Google Chrome.
2. Åbn **Chrome DevTools**.
3. Vælg **Lighthouse**.
4. Vælg kategorien **Accessibility**.
5. Kør analysen.
6. Notér den nuværende score.
7. Gem gerne et screenshot.

```text
Accessibility før forbedringer: ______
```

> Din præcise Lighthouse-score kan variere lidt afhængigt af Chrome/Lighthouse-version og testmiljø. Det vigtige er, at du registrerer **din egen baseline**, før du ændrer koden, og bruger samme testopsætning ved eftermålingen.

## Forkert princip

```text
Ret først problemerne og kør derefter Lighthouse.
```

### Hvorfor er det et problem?

Hvis du ændrer siden først, har du ingen baseline at sammenligne med.

## Korrekt princip

```text
1. Mål
2. Notér
3. Forbedr
4. Mål igen
5. Sammenlign
```

---

# Opgave 2 – Giv siden en beskrivende `<title>`

Undersøg dokumentets nuværende `<title>`.

Starterprojektet indeholder:

```html
<title>website</title>
```

### Hvorfor kan det forbedres?

Titlen hjælper brugeren med at identificere siden i blandt andet:

- browserfaner
- bogmærker
- browserhistorik

## Korrekt princip

En titel bør kort beskrive både websitet og sidens vigtigste indhold.

```html
<title>Virksomhedsnavn | Sidens vigtigste indhold</title>
```

Formulér selv en passende titel til Horiseon.

---

# Opgave 3 – Kontrollér dokumentets `<head>`

Kontrollér dokumentets metadata.

Starterprojektet indeholder allerede:

```html
<meta charset="UTF-8" />
```

Undersøg, hvad der mangler for at gøre siden bedre forberedt til forskellige viewport-størrelser.

## Korrekt princip

Et responsive website bør blandt andet indeholde en viewport-deklaration:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

### Hvorfor er dette vigtigt?

Viewport-indstillingen har betydning for:

- mobile enheder
- responsive layouts
- zoom
- reflow

---

# Opgave 4 – Forbedr den semantiske HTML

Starterprojektet anvender flere generiske `<div>`-elementer.

Eksempel:

```html
<div class="header"></div>
```

Undersøg, om nogle områder i stedet bør anvende semantiske HTML-elementer.

Overvej blandt andet:

```html
<header>
  <nav>
    <main>
      <section>
        <aside>
          <footer></footer>
        </aside>
      </section>
    </main>
  </nav>
</header>
```

## Forkert princip

```html
<div class="footer">...</div>
```

hvis området reelt fungerer som sidens footer.

## Korrekt princip

Brug det HTML-element, der bedst beskriver indholdets funktion.

### En `<div>` kan også være det korrekte valg

Semantisk HTML betyder ikke, at alle `<div>`-elementer skal erstattes med `<section>`.

Hvis et element kun bruges til at gruppere indhold af hensyn til layout og ikke repræsenterer et selvstændigt indholdsafsnit, kan `<div>` være det korrekte valg.

Eksempel:

```html
<div class="layout-wrapper">...</div>
```

Her bruges `<div>` kun som en neutral wrapper til layout.

## Undersøg navigationen særligt

Starterprojektet har et synligt problem i headeren: navigationen står lodret og vises med bullets.

Undersøg både HTML'en og de eksisterende CSS-selectors. Starter-CSS'en indeholder blandt andet:

```css
.header nav {
    ...
}

.header nav ul {
    list-style-type: none;
}

.header nav ul li {
    display: inline-block;
    ...
}
```

Sammenlign disse selectors med den HTML, der faktisk omgiver menuens `<ul>`.

### Krav til navigationen på større skærme

Efter din semantiske rettelse skal navigationen:

- være markeret med et passende semantisk HTML-element
- vises uden bullets
- have menupunkterne placeret horisontalt
- bevare de tre eksisterende links

> Pointen er både at vælge korrekt HTML-semantik og at forstå, hvorfor en CSS-selector kun virker, når den matcher den faktiske HTML-struktur.

---

# Opgave 5 – Skab en logisk dokumentstruktur

HTML-strukturen skal give mening, også hvis CSS ikke indlæses.

Prøv midlertidigt at deaktivere:

```html
<link rel="stylesheet" href="./css/style.css" />
```

Undersøg:

- Kommer navigationen før hovedindholdet?
- Er hovedindholdet samlet?
- Er supplerende indhold placeret logisk?
- Kommer footeren sidst?
- Kan siden forstås uden floats og visuel positionering?

> HTML-koden skal give mening uafhængigt af den visuelle styling.

---

# Opgave 6 – Undersøg headingstrukturen

Starterprojektet anvender website-navnet som `<h1>`.

Du skal overveje:

- Hvad er branding?
- Hvad er sidens egentlige hovedemne?
- Hvilke overskrifter er underemner?
- Mangler nogle sektioner en overordnet heading?
- Er headingniveauerne logiske?

Et muligt hierarki kan være:

```text
h1 Sidens hovedemne

├── h2 Search Engine Optimization
├── h2 Online Reputation Management
├── h2 Social Media Marketing
└── h2 Benefits
    ├── h3 Lead Generation
    ├── h3 Brand Awareness
    └── h3 Cost Management
```

### Vigtigt

Vælg ikke headingniveau ud fra tekstens størrelse.

Vælg headingniveau ud fra indholdets hierarki.

---

## Tilpas CSS efter ændringer i HTML-strukturen

Når du ændrer HTML-elementer, skal du kontrollere, om de eksisterende CSS-selectors stadig matcher.

Starter-CSS'en er flere steder knyttet direkte til bestemte HTML-elementer, blandt andet:

```css
.header h1 {
    ...
}

.header h1 .seo {
    ...
}

.header nav {
    ...
}

.footer h2 {
    ...
}
```

Hvis du ændrer et af disse HTML-elementer, kan stylingen derfor holde op med at virke.

### Korrekt princip

Du skal enten:

1. tilpasse CSS-selectoren til den nye semantiske HTML, eller
2. tilføje en relevant class, hvis stylingen med fordel skal være uafhængig af elementtypen.

Eksempel på princippet:

```html
<p class="logo">...</p>
```

```css
.logo {
    ...
}
```

Det samme princip kan anvendes andre steder, hvis du ændrer et heading-element, men stadig ønsker at bevare den eksisterende visuelle styling.

### Vigtig pointe

```text
HTML-element
→ beskriver betydning og struktur

CSS-selector / class
→ styrer styling og layout
```

---

# Opgave 7 – Gennemgå billedernes `alt`-attributter

Starterprojektet indeholder flere billeder uden `alt`.

Du skal vurdere hvert billede.

## Informativt billede

Hvis billedet tilfører relevant information:

```html
<img src="images/example.jpg" alt="Meningsfuld beskrivelse" />
```

## Dekorativt billede

Hvis billedet kun er dekorativt:

```html
<img src="images/example.png" alt="" />
```

### Vigtig pointe

```text
Informativt billede
→ alt="Meningsfuld beskrivelse"

Dekorativt billede
→ alt=""
```

Brug ikke `aria-label` eller `aria-labelledby` for at fortælle, at et billede er dekorativt.

`aria-label` og `aria-labelledby` bruges, når et element har behov for et tilgængeligt navn.

Til et dekorativt `<img>` er:

```html
alt=""
```

normalt den enkleste og korrekte løsning.

---

# Opgave 8 – Reparér de interne anchor-links

Navigationen anvender interne links som:

```html
<a href="#search-engine-optimization"> Search Engine Optimization </a>
```

Destinationen skal have et tilsvarende `id`.

Eksempel:

```html
<section id="search-engine-optimization"></section>
```

### Din opgave

Test alle tre navigationslinks.

Kontrollér, at de fører til den korrekte sektion.

## Gør også logoet til et link til forsiden

På mange websites fungerer logoet som et link tilbage til forsiden.

Gør derfor hele Horiseon-logoet klikbart og lad det føre til `index.html`.

Eksempel:

```html
<p class="logo">
  <a href="index.html"> Hori<span class="seo">seo</span>n </a>
</p>
```

### Accessibility-pointe

Der er ikke behov for at tilføje `aria-label` til dette link, når den synlige linktekst allerede giver linket et meningsfuldt navn.

---

# Opgave 9 – Undersøg om links kan identificeres visuelt

Starter-CSS'en indeholder:

```css
a {
  color: #ffffff;
  text-decoration: none;
}
```

Undersøg navigationen og vurder:

- Er det tydeligt, at teksterne er links?
- Er links tydelige ved hover?
- Er links tydelige ved keyboard-fokus?
- Er designet afhængigt af farve alene?

> Det er ikke automatisk en accessibility-fejl at fjerne understregningen fra links i en tydelig navigation. Du skal vurdere linkets kontekst.

---

# Opgave 10 – Test og forbedr farvekontrast

Brug Lighthouse eller browserens accessibility-værktøjer til at undersøge kontrast.

Vær især opmærksom på:

```css
color: #ffffff;
```

kombineret med blå baggrunde.

## Din opgave

Hvis kontrasten er utilstrækkelig, skal du ændre eksempelvis:

```css
color
background-color
```

Forsøg at bevare Horiseons visuelle identitet.

---

# Opgave 11 – Test siden med tastatur

Læg musen væk.

Brug:

```text
Tab
Shift + Tab
Enter
```

Kontrollér:

- Kan du nå alle links?
- Kan navigationen bruges?
- Følger fokus en logisk rækkefølge?
- Kan du se, hvilket element der har fokus?

## Korrekt princip

Hvis den eksisterende fokusmarkering ikke er tydelig nok, kan du implementere en tydelig `:focus-visible`-stil.

Eksempel:

```css
a:focus-visible {
  outline: 3px solid currentColor;
  outline-offset: 4px;
}
```

Tilpas løsningen til designet.

---

# Opgave 12 – Test zoom, reflow og faste højder

Starterprojektet anvender blandt andet:

```css
height: 300px;
```

på serviceområderne.

Zoom browseren til:

```text
200 %
```

Undersøg:

- Er al tekst stadig synlig?
- Løber tekst uden for bokse?
- Overlapper elementer?
- Kan bokse vokse med indholdet?
- Opstår der unødvendig vandret scrolling?

## Korrekt princip

Brug ikke en fast højde, hvis indholdet har behov for at kunne vokse.

Overvej:

```css
min-height
```

eller at lade indholdet bestemme højden.

---

# Opgave 13 – Ryd op i CSS

Starter-CSS'en indeholder med vilje gentagelser.

Undersøg:

- Findes den samme styling flere steder?
- Kan selectors samles?
- Findes gamle eller overflødige properties?
- Findes layoutregler, der ikke længere er nødvendige?
- Findes CSS, der ikke længere matcher HTML'en?

### Afgrænsning i denne del

Du må gerne reducere gentagelser ved at gruppere eksisterende selectors. Du behøver ikke allerede her at indføre den `.marketing`-wrapper eller fælles `.services`-class, som introduceres i DEL 3.

## Eksempel

```css
.element-a {
  margin-bottom: 32px;
  color: #ffffff;
}

.element-b {
  margin-bottom: 32px;
  color: #ffffff;
}
```

kan eventuelt samles:

```css
.element-a,
.element-b {
  margin-bottom: 32px;
  color: #ffffff;
}
```

### Vigtigt

Fjern ikke CSS alene, fordi du ikke forstår reglen.

Undersøg først, hvilken funktion den har.

---

# DEL 2 – WEB PERFORMANCE

I anden del skal du optimere websitets ressourcer med fokus på indlæsningstid og billedoptimering.

Målet er:

```text
Lighthouse Performance: 90 eller højere
```

Du skal især arbejde med:

- billeddimensioner
- filstørrelser
- WebP
- hero-billedet i CSS
- billedkvalitet
- Lighthouse og Chrome DevTools

> Bevar de accessibility-forbedringer, du gennemførte i DEL 1, mens du arbejder med performance.

---

# Opgave 14 – Lav en Performance-baseline

Åbn Lighthouse igen.

Vælg:

```text
Performance
```

Brug samme indstillinger ved før- og eftermålingen.

Notér:

```text
Performance før optimering: ______
```

> Performance-scoren kan variere lidt mellem målinger. Brug derfor samme browser, samme Lighthouse-indstillinger og så vidt muligt samme testforhold ved før- og eftermålingen.

Gem gerne et screenshot.

---

# Opgave 15 – Undersøg billedernes dimensioner og filstørrelser

Gennemgå billederne i:

```text
images/
```

Undersøg for hvert billede:

- filformat
- bredde og højde i pixels
- filstørrelse
- hvor stort billedet faktisk vises på websitet

### Refleksion

Et billede på eksempelvis:

```text
3000 × 2000 px
```

er ikke nødvendigvis hensigtsmæssigt, hvis det kun vises omkring:

```text
500 × 300 px
```

## Hjælp

Du kan bruge:

- filinformation i operativsystemet
- Chrome DevTools
- Network-panelet
- et billedredigeringsprogram

Notér gerne resultaterne i en lille tabel.

| Billede                            | Format | Dimensioner | Filstørrelse | Relevant at optimere? |
| ---------------------------------- | ------ | ----------: | -----------: | --------------------- |
| `search-engine-optimization.jpg`   |        |             |              |                       |
| `online-reputation-management.jpg` |        |             |              |                       |
| `social-media-marketing.jpg`       |        |             |              |                       |

---

# Opgave 16 – Konvertér relevante billeder til WebP

Konvertér relevante JPG- og PNG-billeder til **WebP**.

## Forkert

Det er ikke nok blot at ændre:

```html
<img src="images/photo.jpg" alt="..." />
```

til:

```html
<img src="images/photo.webp" alt="..." />
```

hvis filen `photo.webp` ikke eksisterer.

## Korrekt princip

```text
1. Konvertér den fysiske billedfil
2. Kontrollér billedkvaliteten
3. Opdatér filreferencen
4. Test i browseren
```

## Hjælp

Du kan eksempelvis bruge:

- Adobe Photoshop
- GIMP
- XnConvert
- et andet billedværktøj, der kan eksportere WebP

Du behøver ikke bruge terminalen.

---

# Opgave 17 – Husk hero-billedet i CSS

Ikke alle billeder ligger i HTML.

Starter-CSS'en indeholder:

```css
.hero {
  background-image: url("../images/digital-marketing-meeting.jpg");
}
```

Hvis du optimerer hero-billedet, skal denne reference også opdateres.

### Kontrol

Brug browserens **Network-panel** til at kontrollere, at den nye fil faktisk indlæses.

---

# Opgave 18 – Kontrollér billedkvaliteten

En mindre fil er ikke automatisk bedre.

Sammenlign originalen og den optimerede version.

Kontrollér:

- skarphed
- komprimeringsfejl
- teksturer
- farver
- samlet visuel kvalitet

Find en balance mellem:

```text
lav filstørrelse
+
acceptabel billedkvalitet
```

---

# Opgave 19 – Kør Lighthouse Performance igen

Kør Lighthouse med samme indstillinger som ved baseline.

Notér:

```text
Performance før: ______
Performance efter: _____
```

### Mål

```text
Performance: 90 eller højere
```

Hvis scoren fortsat er lav, skal du læse Lighthouse-anbefalingerne og undersøge, hvilke ressourcer der stadig påvirker siden.

---

# DEL 3 – RESPONSIVE WEBDESIGN MED CSS FLEXBOX

Nu skal du gøre websitet responsive.

Du skal arbejde videre med den tilgængelige og optimerede version fra DEL 1 og DEL 2.

Målet er, at siden fungerer på både store og små skærme uden unødvendig vandret scrolling eller overlappende indhold.

---

## Visuelt mål

![Reference til det responsive Horiseon-layout](README-assets/horiseon-responsive-reference.png)

> Referencebilledet viser det ønskede overordnede layout. Du behøver ikke ramme hver pixel præcist. Fokus er på struktur, fleksibilitet, læsbarhed og et robust responsive layout.

---

## Læringsmål

Du skal kunne:

- analysere et eksisterende float-baseret layout
- anvende CSS Flexbox
- forstå flex-container og flex-items
- anvende `gap`
- arbejde med `flex-direction`
- anvende `justify-content` og `align-items`
- bruge `flex-wrap` efter behov
- gøre billeder fleksible
- anvende media queries
- teste flere viewport-størrelser
- fjerne overflødige floats

---

# Opgave 20 – Analysér det eksisterende layout og det gamle layoutsystem

Åbn **Device Toolbar** i Chrome DevTools.

Test eksempelvis:

```text
320 px
480 px
768 px
1024 px
1440 px
```

Undersøg:

- Bliver navigationen for bred?
- Overlapper indhold?
- Bliver serviceområderne for smalle?
- Bliver Benefits-kolonnen for smal?
- Skalerer billederne?
- Opstår vandret scrolling?

Dokumentér mindst tre problemer.

---

## Find det gamle layoutsystem

Starter-CSS'en bruger blandt andet:

```css
float: left;
float: right;
display: inline-block;
```

Undersøg, hvilke elementer disse regler forsøger at placere.

### Refleksion

```text
Hvilke elementer skal stå ved siden af hinanden?
Hvilke elementer skal stå under hinanden?
```

Før du skriver Flexbox, skal du forstå den ønskede struktur.

---

# Opgave 21 – Brug Flexbox i headeren

Headeren indeholder branding og navigation.

I DEL 1 har du arbejdet med navigationens semantik og fået menuen til at fungere vandret uden bullets på større skærme. Starter-CSS'en bruger oprindeligt blandt andet:

```css
.header nav {
  float: right;
}
```

I denne del skal du erstatte den gamle layoutmetode med Flexbox.

## Hjælp – start her

Du kan gøre `.header` til en flex-container:

```css
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
```

Når et element får:

```css
display: flex;
```

bliver dets **direkte children** til flex-items.

Efter dine semantiske forbedringer kan du tænke headerens struktur sådan:

```text
.header
│
├── branding / logo
└── nav
```

### Vigtig pointe

Flexbox påvirker først og fremmest de direkte children i flex-containeren.

Når Flexbox overtager placeringen af branding og navigation, skal du undersøge, om den gamle regel:

```css
float: right;
```

stadig er nødvendig.

Du skal ikke beholde gamle layoutregler, hvis Flexbox allerede løser deres funktion.

### Kontrollér navigationen igen

Efter ændringen skal navigationen på større skærme fortsat:

- være uden bullets
- have links placeret horisontalt
- have passende afstand mellem links
- kunne bruges med tastatur

---

# Opgave 22 – Organisér hovedindholdet før du bruger Flexbox

Før du skriver mere CSS, skal du forstå strukturen i hovedindholdet.

Den vejledende løsning organiserer indholdet efter dette princip:

```text
main.content
│
├── h1
│   └── Digital Marketing Services
│
├── .marketing
│   ├── section.services
│   │   └── Search Engine Optimization
│   │
│   ├── section.services
│   │   └── Online Reputation Management
│   │
│   └── section.services
│       └── Social Media Marketing
│
└── aside.benefits
    ├── Lead Generation
    ├── Brand Awareness
    └── Cost Management
```

## Hvad viser skitsen?

Skitsen viser:

- at `main.content` er den overordnede container
- at sidens `<h1>` ligger øverst
- at `.marketing` samler de tre serviceområder
- at `aside.benefits` er et separat område
- at de tre serviceområder har samme rolle i layoutet

`.marketing` fungerer her som en wrapper omkring de tre service-sektioner.

De enkelte serviceområder kan derfor få en fælles class:

```html
<section class="search-engine-optimization services">...</section>
```

```html
<section class="online-reputation-management services">...</section>
```

```html
<section class="social-media-marketing services">...</section>
```

### Hvorfor en fælles `.services`-class?

De tre områder har samme rolle i layoutet.

Det giver mulighed for at style dem samlet i stedet for at skrive den samme layoutregel tre gange.

### Tænk over strukturen før CSS

Før du bruger Flexbox, skal du kunne svare på:

```text
Hvad hører sammen?

Hvilke elementer skal ligge ved siden af hinanden?

Hvilke elementer skal ligge under hinanden?

Hvilke elementer skal være direkte children i en flex-container?
```

> Du må gerne tilføje classes eller en simpel wrapper i HTML'en, når det gør layoutet mere logisk og CSS'en lettere at vedligeholde.

---

# Opgave 23 – Brug Flexbox på `main.content`

I den vejledende løsning bruges `main.content` som flex-container.

Du må gerne tage udgangspunkt i:

```css
main.content {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-items: stretch;
  gap: 1.2rem;
}
```

## Skitse af Flexbox-layoutet

Målet er et desktop-layout, der overordnet kan se sådan ud:

```text
main.content
┌──────────────────────────────────────────────────────────────┐
│ h1: Digital Marketing Services                              │
├───────────────────────────────────────┬──────────────────────┤
│ .marketing                            │ aside.benefits       │
│                                       │                      │
│ ┌───────────────────────────────────┐ │ ┌──────────────────┐ │
│ │ .services                         │ │ │ Lead Generation  │ │
│ │ Search Engine Optimization        │ │ ├──────────────────┤ │
│ └───────────────────────────────────┘ │ │ Brand Awareness  │ │
│                                       │ ├──────────────────┤ │
│ ┌───────────────────────────────────┐ │ │ Cost Management  │ │
│ │ .services                         │ │ └──────────────────┘ │
│ │ Online Reputation Management      │ │                      │
│ └───────────────────────────────────┘ │                      │
│                                       │                      │
│ ┌───────────────────────────────────┐ │                      │
│ │ .services                         │ │                      │
│ │ Social Media Marketing            │ │                      │
│ └───────────────────────────────────┘ │                      │
└───────────────────────────────────────┴──────────────────────┘
```

## Hvad betyder reglerne?

```text
display: flex
→ main bliver en flex-container

flex-direction: row
→ flex-items placeres som udgangspunkt vandret

flex-wrap: wrap
→ flex-items må flytte til en ny række

align-items: stretch
→ elementerne kan strækkes i den tværgående retning

gap: 1.2rem
→ der skabes afstand mellem flex-items
```

## Hvilke elementer bliver flex-items?

Hvis HTML-strukturen er:

```text
main.content
│
├── h1
├── .marketing
└── aside.benefits
```

så bliver disse tre elementer flex-items:

```text
h1
.marketing
aside.benefits
```

### Vigtig pointe

`display: flex` påvirker først og fremmest de **direkte children** i flex-containeren.

Det betyder, at de tre `.services` ikke direkte styres af Flexbox-reglerne på `main.content`.

De ligger inde i `.marketing`.

---

## Få `<h1>` til at ligge på sin egen række

Hvis `<h1>` skal ligge over `.marketing` og `aside.benefits`, kan du bruge:

```css
main.content > h1 {
  flex-basis: 100%;
}
```

Så kan du tænke layoutet sådan:

```text
Række 1

[h1......................................................]

Række 2

[.marketing........................][aside.benefits.....]
```

### Hvad gør `flex-basis: 100%`?

I denne sammenhæng betyder det, at `<h1>` som udgangspunkt optager en hel række i flex-containeren.

Det giver plads til, at `.marketing` og `aside.benefits` kan ligge ved siden af hinanden på næste række.

---

## Det overordnede Flexbox-princip

Du kan tænke strukturen sådan:

```text
main.content
→ styrer det overordnede layout

.marketing
→ styrer de tre servicebokse

aside.benefits
→ styrer benefit-indholdet
```

Du skal altså ikke forsøge at løse hele siden med én enkelt flex-container.

I de næste opgaver arbejder du videre med `.marketing` og `aside.benefits`.

---

# Opgave 24 – Organisér `.marketing` med Flexbox

De tre servicebokse skal stå under hinanden.

Her kan `.marketing` fungere som endnu en flex-container:

```css
.marketing {
  display: flex;
  flex-direction: column;
  gap: 1.2rem;
}
```

Strukturen bliver:

```text
.marketing
│
├── .services
├── .services
└── .services
```

Her betyder:

```text
flex-direction: column
→ serviceboksene placeres lodret
```

## Lad serviceboksene dele pladsen

I stedet for at give hver serviceboks en fast procenthøjde kan du lade Flexbox fordele den tilgængelige plads:

```css
.services {
  flex: 1;
}
```

Det er mere fleksibelt end eksempelvis:

```css
.services {
  height: 32.2%;
}
```

### Hvorfor?

`flex: 1` betyder i denne sammenhæng, at de tre serviceområder får mulighed for at dele den ledige plads i `.marketing`.

Det gør det lettere at få servicekolonnen til visuelt at flugte med Benefits-kolonnen uden at bruge en "magisk" procentværdi.

---

# Opgave 25 – Brug Flexbox i `aside.benefits`

Benefits-området indeholder flere elementer, der skal organiseres lodret.

Du må gerne tage udgangspunkt i:

```css
aside.benefits {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.4rem;
}
```

Her får du et andet eksempel på Flexbox:

```text
main.content
→ row

.marketing
→ column

aside.benefits
→ column
```

### Det vigtige er ikke at bruge Flexbox overalt

Brug Flexbox, når det løser et konkret layoutproblem.

Du skal kunne forklare:

- hvorfor `main.content` bruger Flexbox
- hvorfor `.marketing` bruger `column`
- hvorfor `.services` bruger `flex: 1`
- hvorfor `aside.benefits` bruger `column`

---

# Opgave 26 – Tilføj ét CSS breakpoint med media query

Desktop-layoutet skal nu tilpasses mindre skærme.

Du behøver kun **ét breakpoint**, hvis det giver et velfungerende layout.

> Du skal ikke tilføje flere breakpoints bare for at have flere.

## Hvad er et breakpoint?

Et breakpoint er det punkt, hvor layoutet har behov for at ændre sig.

Tænk derfor:

```text
Hvornår begynder mit layout at få problemer?
```

og ikke:

```text
Hvor mange breakpoints skal jeg have?
```

---

## Brug `max-width` i denne opgave

Starterprojektet er bygget som et desktop-layout. Derfor bruger vi i denne opgave `max-width` til at tilpasse layoutet til mindre skærme.

### `max-width`

```css
@media (max-width: 768px) {
    ...
}
```

betyder:

```text
Når viewporten er 768 px eller smallere
→ brug reglerne inde i media query'en
```

Du kan tænke det sådan:

```text
Standard CSS
→ desktop / større skærme

max-width
→ tilpasning til mindre skærme
```

Horiseon-starterprojektet er allerede bygget som et desktop-layout, så `max-width` passer naturligt til denne opgave.

---

## Hjælp – sådan kan du starte dit breakpoint

Du må gerne tage udgangspunkt i:

```css
@media (max-width: 768px) {
  main.content {
    flex-direction: column;
  }

  .benefits {
    width: 100%;
  }
}
```

Det betyder, at hovedlayoutet på mindre skærme går fra:

```text
DESKTOP

.marketing | .benefits
```

til:

```text
MINDRE SKÆRM

.marketing
.benefits
```

Du skal herefter undersøge, om du også skal tilpasse:

- headeren
- navigationen
- floats på billeder
- margins
- paddings
- billedstørrelser

### Eksempel på yderligere muligheder

```css
@media (max-width: 768px) {
  .header {
    flex-direction: column;
  }

  .header nav {
    float: none;
    margin-right: 0;
  }

  main.content {
    flex-direction: column;
  }

  .benefits {
    width: 100%;
  }
}
```

> Eksemplet er stilladsering og ikke nødvendigvis hele løsningen. Test din egen side og tilføj kun de regler, der er nødvendige.

---

## Test breakpointet

Brug Chrome DevTools og ændr langsomt viewportens bredde.

Undersøg:

```text
Over breakpointet
→ desktop-layout

Ved breakpointet
→ layoutet skifter

Under breakpointet
→ layoutet skal stadig være læsbart og brugbart
```

Hvis ét breakpoint løser problemerne tilfredsstillende, er det nok.

---

# Opgave 27 – Test navigationen på små skærme

På større skærme har du allerede gjort navigationen vandret og fjernet bullets. Nu skal du undersøge, om den samme løsning fungerer på mindre skærme.

Test navigationen ved blandt andet:

```text
320 px
480 px
```

Kontrollér:

- Kan alle links læses?
- Bliver links klippet?
- Overlapper de logoet?
- Er der passende afstand mellem links?
- Kan de fortsat bruges med tastatur?

Overvej om:

```css
flex-wrap
```

eller ændring af `flex-direction` kan være relevant.

---

# Opgave 28 – Sammenlign med referencebilledet og gennemfør afsluttende responsive test

## Sammenlign med referencebilledet

Sammenlign dit resultat med referencebilledet.

Vurder:

- overordnet placering
- indbyrdes afstand
- størrelsesforhold
- læsbarhed
- desktop-layout
- mobile-layout

Du skal **ikke** nødvendigvis lave en pixel-perfekt kopi.

Du skal kunne forklare dine layoutvalg.

---

## Test flere viewport-størrelser

Test mindst:

```text
320 px
480 px
768 px
1024 px
1440 px
```

Kontrollér:

- ingen unødvendig vandret scrolling
- ingen overlappende indhold
- navigationen fungerer
- teksten er læsbar
- billederne passer til containeren
- Benefits fungerer både desktop og mobil
- keyboard focus er stadig synligt

Test også ved:

```text
200 % zoom
```

---

# Opgave 29 – Afsluttende Lighthouse-test

Kør til sidst Lighthouse igen.

Registrér:

| Måling        | Før | Efter |
| ------------- | --: | ----: |
| Accessibility |     |       |
| Performance   |     |       |

### Målsætning

```text
Accessibility: 100
Performance: 90 eller højere
```

Responsive webdesign vurderes manuelt med Device Toolbar og zoom-test.

---

# Dokumentér dine resultater

Besvar kort:

1. Hvad var Accessibility-score før og efter?
2. Hvilke accessibility-problemer fandt Lighthouse?
3. Hvilke accessibility-problemer krævede manuel kontrol?
4. Hvilke semantiske HTML-ændringer foretog du?
5. Hvilke CSS-regler blev overflødige efter HTML-ændringerne?
6. Hvad var Performance-score før og efter?
7. Hvilke billeder optimerede du?
8. Hvor meget blev filstørrelserne reduceret?
9. Hvilke elementer gjorde du til flex-containere?
10. Hvilke gamle floats kunne fjernes?
11. Hvilket breakpoint valgte du, og hvorfor valgte du netop dette?
12. Hvordan ændrer layoutet sig på en mobil skærm?
13. Hvad sker der ved 200 % zoom?

---

# Kontrol af din løsning

## DEL 1 – Web Accessibility

- [ ] Accessibility-baseline er dokumenteret.
- [ ] `<title>` er beskrivende.
- [ ] `<meta name="viewport">` er tilføjet.
- [ ] Semantisk HTML er anvendt.
- [ ] Rene layout-wrappers bruger et passende neutralt element, fx `<div>`.
- [ ] Eksisterende CSS-selectors er kontrolleret og tilpasset efter semantiske HTML-ændringer.
- [ ] Navigationen bruger et passende semantisk HTML-element.
- [ ] Navigationen vises uden bullets og med horisontale menupunkter på større skærme.
- [ ] Dokumentstrukturen er logisk.
- [ ] Headingstrukturen er logisk.
- [ ] Informative billeder har relevante `alt`-tekster.
- [ ] Dekorative billeder bruger `alt=""`.
- [ ] Anchor-links fungerer.
- [ ] Horiseon-logoet fungerer som link til `index.html`.
- [ ] Links kan identificeres.
- [ ] Farvekontrast er kontrolleret.
- [ ] Tastaturtest er gennemført.
- [ ] Keyboard-fokus er tydeligt.
- [ ] Siden er testet ved 200 % zoom.
- [ ] Faste højder er vurderet.
- [ ] CSS er ryddet op.
- [ ] HTML er valideret.
- [ ] Lighthouse Accessibility er kørt igen.
- [ ] Accessibility-score er 100.

## DEL 2 – Web Performance

- [ ] Performance-baseline er dokumenteret.
- [ ] Billeddimensioner er undersøgt.
- [ ] Filstørrelser er undersøgt.
- [ ] Relevante billeder er konverteret til WebP.
- [ ] HTML-referencer er opdateret.
- [ ] Hero-billedets CSS-reference er kontrolleret.
- [ ] Billedkvalitet er vurderet.
- [ ] Network-panelet er anvendt til kontrol.
- [ ] Lighthouse Performance er kørt igen.
- [ ] Performance-score er 90 eller højere.

## DEL 3 – Responsive Webdesign

- [ ] Layoutet er analyseret i Device Toolbar.
- [ ] Headeren anvender et passende Flexbox-layout.
- [ ] Hovedindholdet anvender et passende Flexbox-layout.
- [ ] Overflødige floats er fjernet.
- [ ] Billeder er responsive.
- [ ] Problematiske faste størrelser er vurderet.
- [ ] Der er tilføjet ét relevant CSS breakpoint med en media query (flere er tilladt, hvis de faktisk er nødvendige).
- [ ] Navigationen fungerer på små skærme.
- [ ] Siden er testet ved 320 px.
- [ ] Siden er testet ved 480 px.
- [ ] Siden er testet ved 768 px.
- [ ] Siden er testet ved 1024 px.
- [ ] Siden er testet ved 1440 px.
- [ ] Der er ingen unødvendig vandret scrolling.
- [ ] Siden fungerer ved 200 % zoom.
- [ ] Resultatet er sammenlignet med referencebilledet.

---

# Useful Links / Nyttige links

## Chrome DevTools

https://developer.chrome.com/docs/devtools/

## Lighthouse

https://developer.chrome.com/docs/lighthouse/

## HTML

https://developer.mozilla.org/en-US/docs/Web/HTML

## Web Accessibility

https://www.w3.org/WAI/

https://www.w3.org/WAI/tutorials/images/

https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html

https://www.w3.org/WAI/WCAG22/Understanding/reflow.html

## CSS Flexbox

https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_flexible_box_layout

## Responsive Webdesign

https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/CSS_layout/Responsive_Design

## WebP

https://developers.google.com/speed/webp/

## HTML Validation

https://validator.w3.org/

---

# Aflevering

Aflever hele projektmappen.

Dokumentér desuden:

```text
Accessibility før / efter
Performance før / efter
Responsive test ved flere viewport-bredder
```

Du skal kunne forklare mindst:

- tre accessibility-forbedringer
- to performance-forbedringer
- to responsive design-valg

---

# Afsluttende note

> Formålet er ikke kun at opnå høje Lighthouse-scores. Formålet er at lære at analysere eksisterende HTML og CSS, forbedre webtilgængelighed, optimere ressourcer og udvikle et robust responsive layout med begrundede tekniske valg.
