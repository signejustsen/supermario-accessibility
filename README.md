# Super Mario Fanclub
# Webtilgængelighed og web performance-optimering

**Semester:** 3. semester

> Udviklet til studerende på **3. semester**. Ingen AI-værktøjer er nødvendige — kun en browser, en teksteditor, et tastatur og et simpelt billedværktøj.

---

## Opgavebeskrivelse

I denne øvelse skal du arbejde med det eksisterende **Super Mario Fanclub-site** og undersøge, hvordan du kan forbedre både:

- web performance
- semantisk HTML
- webtilgængelighed
- formularer
- navigation
- billeder
- headingstruktur

Du skal bruge **Chrome DevTools** og **Lighthouse** til at analysere sitet før og efter dine ændringer.

Du skal ikke bygge sitet om fra bunden. Formålet er, at du lærer at identificere konkrete problemer i eksisterende kode og forbedre dem trin for trin.

Du skal arbejde med følgende sider:

```text
index.html
news.html
games.html
contact.html
```

> **Vigtigt:** Foretag ikke alle ændringer på én gang. Test løbende, så du kan se, hvilken effekt dine ændringer har.

---


# Fremgangsmåde – sådan kommer du i gang med projektet

I denne opgave skal du bruge **GitHub Template-metoden**.

Du skal derfor **ikke downloade projektet som ZIP og ikke bruge Fork**.

Følg rækkefølgen:

```text
GitHub Template
↓
Dit eget repository på GitHub.com
↓
GitHub Desktop
↓
Visual Studio Code
↓
Commit
↓
Push
```

Følg punkterne **ét ad gangen og i den viste rækkefølge**.

---

## 1. Opret dit eget repository på GitHub.com

Åbn det udleverede **Marioclub-template repository** på GitHub.com.

Du skal være logget ind på din egen GitHub-konto.

Klik på:

**Use this template**

Vælg derefter:

**Create a new repository**

Vælg din egen GitHub-konto som ejer, og brug det repository-navn, som din underviser har angivet.

Klik derefter:

**Create repository**

Vent et øjeblik, mens GitHub opretter dit nye repository.

### Kontrollér, at du er i dit eget repository

Når repositoryet er oprettet, skal du kontrollere navnet øverst på siden.

Det skal være **dit eget GitHub-brugernavn**, der står foran repositoryets navn.

Det kan fx se sådan ud:

```text
dit-brugernavn/marioclub-web-accessibility-performance
```

> **Stop her og kontrollér dette, før du går videre.**

---

## 2. Hent dit repository ned på din computer

Nu ligger projektet på **GitHub.com**, men du skal også have det ned på din egen computer.

Åbn **GitHub Desktop**.

Vælg:

**File → Clone repository...**

Vælg fanebladet **GitHub.com**, og find det Marioclub-repository, du netop har oprettet.

Hvis repositoryet ikke vises, kan du i stedet vælge fanebladet **URL** og indsætte adressen til dit repository fra GitHub.com.

### Vælg, hvor projektet skal gemmes

I feltet **Local path** vælger du, hvor projektet skal ligge på din computer.

> **Local path** betyder den mappe på din computer, hvor projektets filer bliver gemt.

Klik derefter:

**Clone**

Vent, mens GitHub Desktop henter projektet ned på din computer.

---

## 3. Åbn projektet i Visual Studio Code

Når projektet er klonet, vælg:

**Open in Visual Studio Code**

Du skal arbejde direkte i den lokale projektmappe, som GitHub Desktop har klonet.

Kontrollér, at du blandt andet kan se:

```text
index.html
news.html
games.html
contact.html
css/
img/
README.md
```

---

## 4. Arbejd progressivt med commits

Du skal ikke vente med at committe, til hele opgaven er færdig.

Lav commits løbende, når du har afsluttet en tydelig del af arbejdet.

Det kan eksempelvis være efter arbejde med:

- billeder og WebP
- alt-tekster
- headingstruktur
- navigation
- formularer
- dokumentets `<head>`
- WAVE-fejl og kontrast
- CSS-tilpasninger
- performance-optimering

Skriv selv korte og meningsfulde commit-beskeder, der beskriver, hvad du har ændret.

Push dine commits løbende til GitHub.com.

> Formålet er, at din Git-historik viser, hvordan projektet er blevet forbedret trin for trin.

---

# Opgave 1 – Lav en Lighthouse-baseline

Inden du ændrer noget i koden, skal du lave en måling af sitets nuværende performance.

## Sådan gør du

1. Åbn `index.html` i Google Chrome.
2. Åbn **Chrome DevTools**.
3. Vælg **Lighthouse**.
4. Vælg **Mobile**.
5. Kør en analyse af siden.
6. Notér den nuværende **Performance-score**.
7. Gem gerne et screenshot af resultatet.
8. Gentag målingen på de øvrige sider.

Du skal som minimum registrere performance-resultatet før optimering.

## Forkert

```text
Optimér først alle billeder og kør derefter Lighthouse.
```

### Hvorfor er det et problem?

Hvis du optimerer først, har du ingen baseline at sammenligne med. Du kan derfor ikke dokumentere effekten af dine ændringer.

## Korrekt princip

```text
1. Mål
2. Notér resultatet
3. Optimér
4. Mål igen
5. Sammenlign
```

### Hvorfor er dette bedre?

Du får en tydelig før/efter-måling og kan se, hvilke ændringer der faktisk forbedrer performance.

---

# Opgave 2 – Optimér billeder og konvertér til WebP

Sitet anvender flere billeder i JPG-format.

Eksempel:

```html
<img src="img/banner.jpg" alt="marioclub welcome banner">
```

Du skal undersøge billedernes:

- dimensioner
- filstørrelse
- visuelle kvalitet

Konvertér de relevante JPG-billeder til **WebP**. Hvis der også findes andre tunge rasterbilleder i `img`-mappen, skal du vurdere, om de ligeledes bør optimeres.

## Forkert

Det er ikke nok blot at ændre filendelsen i HTML:

```html
<img src="img/banner.webp" alt="marioclub welcome banner">
```

hvis filen stadig kun eksisterer som:

```text
banner.jpg
```

### Hvorfor er det et problem?

Browseren forsøger at hente en fil, som ikke findes.

## Korrekt princip

Først konverteres billedfilen:

```text
banner.jpg
→
banner.webp
```

Derefter ændres HTML:

```html
<img src="img/banner.webp" alt="...">
```

### Hvorfor er dette bedre?

HTML-koden peger nu på den faktiske optimerede billedfil.

---

## Programmer til WebP-konvertering

Du behøver ikke bruge terminalen til denne opgave.

Du kan eksempelvis bruge et af følgende programmer med grafisk brugerflade:

### Adobe Photoshop

Kan eksportere billeder til WebP og giver mulighed for at justere kvalitet og komprimering.

### GIMP

Gratis og open source.

GIMP findes til både macOS og Windows og kan eksportere direkte til WebP.

### XnConvert

Et grafisk værktøj til macOS, Windows og Linux.

XnConvert er særligt velegnet, hvis du skal konvertere flere billeder på én gang.

### WebP Converter / AnyWebP – macOS

Et simpelt grafisk program til konvertering mellem blandt andet JPG, PNG og WebP.

Hvis dit WebP-konverteringsprogram kan:

- konvertere JPG eller PNG til WebP
- bevare den ønskede billedkvalitet
- eventuelt justere komprimeringsniveauet

er det tilstrækkeligt til denne øvelse.

### ImageMagick – valgfrit

ImageMagick er et mere avanceret værktøj, som blandt andet kan konvertere, ændre størrelse på, beskære og optimere billeder.

Det er **ikke et krav** at bruge ImageMagick i denne opgave.

---

# Opgave 3 – Kontrollér billedkvaliteten

En mindre fil er ikke automatisk et bedre billede.

Efter konverteringen skal du kontrollere hvert WebP-billede visuelt.

## Forkert

```text
JPG: 800 KB
WebP: 35 KB
```

hvis WebP-versionen samtidig har tydelige komprimeringsfejl eller dårlig billedkvalitet.

### Hvorfor er det et problem?

En meget lille fil kan være så hårdt komprimeret, at billedkvaliteten bliver synligt dårlig.

## Korrekt princip

Find en balance mellem:

```text
lavere filstørrelse
+
acceptabel visuel kvalitet
```

### Hvorfor er dette bedre?

Du forbedrer performance uden at ødelægge brugeroplevelsen.

Sammenlign originalen og WebP-versionen i browseren.

Hvis kvaliteten ikke er tilfredsstillende, skal du eksportere billedet igen med en højere kvalitetsindstilling.

---

# Opgave 4 – Opdatér billedreferencer og brug lazy loading med omtanke

Når billederne er konverteret, skal HTML-filerne opdateres.

## Forkert

```html
<img src="img/thumb-1.jpg" alt="...">
```

hvis du ønsker at anvende den nye WebP-version.

### Hvorfor er det et problem?

Browseren fortsætter med at hente den gamle JPG-fil, selvom du har oprettet en WebP-version.

## Korrekt princip

```html
<img src="img/thumb-1.webp" alt="...">
```

### Hvorfor er dette bedre?

Browseren indlæser nu den nye optimerede billedfil.

Kontrollér alle fire HTML-filer.

Brug Chrome DevTools eller browserens **Network-panel** til at kontrollere, at de nye WebP-filer faktisk bliver hentet.

---

## Lazy loading

Billeder længere nede på siden kan være relevante at lazy-loade.

Eksempel:

```html
<img
    src="img/thumb-1.webp"
    alt="..."
    loading="lazy"
>
```

## Forkert princip

```html
<img
    src="img/banner.webp"
    alt="..."
    loading="lazy"
>
```

hvis banneret er et vigtigt billede, som vises med det samme øverst på siden.

### Hvorfor er det et problem?

Et vigtigt billede over folden bør normalt ikke forsinkes unødigt.

## Korrekt princip

```text
Banner / hero-billede øverst på siden
→ normalt ikke loading="lazy"

Thumbnail eller andet billede længere nede
→ loading="lazy" kan være relevant
```

### Hvorfor er dette bedre?

Browseren kan prioritere de vigtigste ressourcer først og udsætte billeder, som brugeren endnu ikke kan se.

---

# Opgave 5 – Gennemgå billedernes alt-tekster

Web performance handler om filstørrelse og loadingtid.

Webtilgængelighed handler også om, hvorvidt billedets betydning er tilgængelig for brugere, der ikke kan se billedet.

I starterkoden findes eksempelvis:

```html
<img src="img/thumb-1.jpg" alt="mario thumbnail 1">
```

## Forkert

```html
<img src="img/thumb-1.webp" alt="mario thumbnail 1">
```

### Hvorfor er det et problem?

Alt-teksten beskriver primært billedets fil- eller layoutrolle og ikke nødvendigvis billedets relevante indhold eller funktion.

## Korrekt princip

Hvis billedet har betydning for indholdet, skal `alt` kort beskrive billedets relevante indhold eller funktion.

Eksempel:

```html
<img
    src="img/example.webp"
    alt="Mario jumping over an obstacle"
>
```

Hvis billedet udelukkende er dekorativt, skal du overveje:

```html
alt=""
```

### Hvorfor er dette bedre?

En meningsfuld alt-tekst giver brugere af skærmlæsere adgang til billedets relevante information.

Et dekorativt billede med `alt=""` kan derimod ignoreres af skærmlæsere, så brugeren ikke præsenteres for unødvendig information.

Eksemplet ovenfor er kun et eksempel. Du skal selv skrive en alt-tekst, der passer til det konkrete billede.

Du skal selv kunne forklare, hvorfor du har valgt den enkelte alt-tekst.

---

# Opgave 6 – Undersøg sidernes headingstruktur med HeadingsMap

Brug Chrome Extension **HeadingsMap** til at undersøge headingstrukturen på alle fire sider.

Kør først HeadingsMap **inden du ændrer HTML-koden**.

På `index.html` vil starterkoden eksempelvis vise en struktur i denne retning:

```text
h1 Marioclub
├── h2 Welcome to Marioclub
├── h2 It's a me, Mario
└── h2 Join Today!
```

## Analysér strukturen

HeadingsMap viser sidens headinghierarki, men værktøjet fortæller ikke nødvendigvis, om strukturen er den mest meningsfulde.

Overvej derfor:

- Hvad er website-branding?
- Hvad er den aktuelle sides hovedemne?
- Hvilken tekst bør være sidens primære `h1`?
- Hvilke headings hører under sidens hovedemne?
- Er headingniveauerne valgt ud fra indholdets struktur eller ud fra tekstens visuelle størrelse?

Website-navnet `Marioclub` kan fungere som branding og link til forsiden uden nødvendigvis at være en heading.

Et muligt forbedret princip kan være:

```text
h1 Sidens hovedemne
├── h2 Underemne
└── h2 Underemne
```

Du skal selv beslutte den konkrete headingstruktur på hver side og kunne begrunde dit valg.

> Vælg headingniveau ud fra indholdets hierarki – ikke ud fra tekstens størrelse eller placering.

---

## Kontrollér CSS efter ændringer i HTML

Når du ændrer HTML-elementer, kan det påvirke eksisterende CSS.

Starterprojektets stylesheet indeholder eksempelvis selectors, som er knyttet til bestemte HTML-elementer.

Eksempel:

```css
header h1 {
    color: white;
    border: 8px solid white;
    display: inline-block;
    padding: 6px 12px;
    border-radius: 36px;
}
```

Hvis du ændrer HTML-strukturen, kan denne selector derfor holde op med at ramme det ønskede element.

Efter ændringer i headingstrukturen skal du:

1. gemme HTML-filen
2. genindlæse siden i browseren
3. kontrollere, om designet stadig ser korrekt ud
4. undersøge relevante CSS-selectors
5. tilpasse CSS, hvis dine HTML-ændringer har påvirket designet

### Vigtigt princip

```text
Ændr HTML-semantik
        ↓
kontrollér CSS
        ↓
tilpas selectors efter behov
        ↓
bevar både korrekt semantik og design
```

Du skal ikke beholde et uhensigtsmæssigt HTML-element alene for at bevare en bestemt styling.

---

## Test headingstrukturen igen

Når du har ændret headingstrukturen:

1. Gem HTML-filen.
2. Genindlæs siden i browseren.
3. Kør HeadingsMap igen.
4. Sammenlign strukturen før og efter.
5. Kontrollér samtidig, at ændringen ikke har ødelagt sidens visuelle design.

Kontrollér:

```text
index.html
news.html
games.html
contact.html
```

---

# Opgave 7 – Markér den aktuelle side i navigationen

Navigationen viser visuelt den aktive side med en CSS-klasse:

```html
<a href="news.html" class="join">Latest news</a>
```

## Forkert

```html
<a href="news.html" class="join">Latest news</a>
```

### Hvorfor er det et problem?

En CSS-klasse fortæller ikke i sig selv hjælpemidler, at dette link repræsenterer den aktuelle side.

## Korrekt princip

```html
<a
    href="news.html"
    class="join"
    aria-current="page"
>
    Latest news
</a>
```

### Hvorfor er dette bedre?

`aria-current="page"` gør det muligt for hjælpemidler at identificere den aktuelle side i navigationen.

Tilføj `aria-current="page"` til det aktive navigationslink på hver side.

Der må kun være én aktuel side i denne navigation ad gangen.

> Brug native semantisk HTML først. Tilføj ARIA, når der er et konkret behov.

---

# Opgave 8 – Gør formularerne tilgængelige

Sitet indeholder formularer på flere sider.

I starterkoden bruges blandt andet `placeholder` som eneste information om feltets formål.

Eksempel:

```html
<input
    type="email"
    name="email"
    placeholder="Type email & hit enter"
    required
>
```

Et `placeholder` er ikke en erstatning for et `<label>`.

## Forkert

```html
<input
    type="email"
    placeholder="Type your email"
>
```

### Hvorfor er det et problem?

Når brugeren begynder at skrive, forsvinder placeholder-teksten. Feltet har heller ikke nødvendigvis et tydeligt og entydigt tilgængeligt navn.

## Korrekt princip

```html
<label for="email">Email address</label>

<input
    type="email"
    id="email"
    name="email"
    autocomplete="email"
    placeholder="name@example.com"
    required
>
```

### Hvorfor er dette bedre?

Et synligt `<label>` gør feltets formål tydeligt og skaber en semantisk relation mellem label og input.

`for` på `<label>` skal matche feltets `id`.

---

## Labels gælder også textarea og datalist-input

Et `<textarea>` bør også have et label.

## Forkert

```html
<textarea
    name="question"
    placeholder="Ask a question..."
></textarea>
```

## Korrekt princip

```html
<label for="question">Your question</label>

<textarea
    id="question"
    name="question"
    placeholder="Ask a question..."
></textarea>
```

Et inputfelt med `list` og `<datalist>` skal også have et label.

## Forkert

```html
<input
    list="countries"
    name="country"
    id="country"
>

<datalist id="countries">
    <option value="Denmark">
    <option value="Sweden">
</datalist>
```

## Korrekt princip

```html
<label for="country">Country</label>

<input
    list="countries"
    name="country"
    id="country"
    autocomplete="country-name"
>

<datalist id="countries">
    <option value="Denmark">
    <option value="Sweden">
</datalist>
```

### Hvorfor er dette bedre?

`<datalist>` giver forslag til feltet, men den fortæller ikke brugeren, hvad feltets formål er. Det gør `<label>`.

---

## Brug `autocomplete` til kendte personoplysninger

`autocomplete` fortæller browseren, hvilken type information et felt forventer.

Eksempel:

```text
First name → autocomplete="given-name"
Last name  → autocomplete="family-name"
Email      → autocomplete="email"
Country    → autocomplete="country-name"
```

Eksempel i HTML:

```html
<label for="firstname">First name</label>
<input
    type="text"
    id="firstname"
    name="fname"
    autocomplete="given-name"
    required
>

<label for="lastname">Last name</label>
<input
    type="text"
    id="lastname"
    name="lname"
    autocomplete="family-name"
    required
>
```

### Vigtigt

`autocomplete` skal ikke nødvendigvis have samme værdi som `id` eller `name`.

De tre attributter har forskellige roller:

```text
id
→ identificerer HTML-elementet og bruges sammen med label

name
→ navnet på den værdi, som formularen sender

autocomplete
→ beskriver hvilken type information browseren forventer
```

### Hvorfor understøtter dette accessibility?

Autofill kan reducere behovet for at skrive de samme personlige oplysninger manuelt igen og igen.

Det kan blandt andet være en hjælp for brugere med motoriske, kognitive eller hukommelsesmæssige udfordringer.

---

## Giv formularen en tydelig submit-handling

På `index.html`, `news.html`, `games.html` og nederst på `contact.html` findes en emailformular, hvor brugeren forventes at forstå instruktionen:

```text
Type email & hit enter
```

Hovedformularen på `contact.html` har allerede en gyldig submit-kontrol:

```html
<input type="submit" value="Get in Touch">
```

Den behøver derfor ikke ændres alene af accessibility-hensyn. Opgaven er at vurdere hver formular og kun ændre de dele, der faktisk har et problem.

## Forkert princip

```html
<form>
    <label for="email">Email address</label>

    <input
        type="email"
        id="email"
        placeholder="Type email & hit enter"
    >
</form>
```

### Hvorfor er det et problem?

Brugeren skal selv vide, at Enter sender formularen, og instruktionen i placeholderen forsvinder, når der skrives i feltet.

## Korrekt princip

```html
<form>
    <label for="email">Email address</label>

    <input
        type="email"
        id="email"
        name="email"
        autocomplete="email"
        required
    >

    <button type="submit">Join the club</button>
</form>
```

### Hvorfor er dette bedre?

Formularfeltets formål og handlingen for at sende formularen er begge tydeligt angivet.

### `button` eller `input type="submit"`?

Begge dele er gyldige:

```html
<input type="submit" value="Get in Touch">
```

og:

```html
<button type="submit">Get in Touch</button>
```

`<button type="submit">` anvendes i eksemplerne, fordi det er et fleksibelt og tydeligt moderne valg.

Det betyder ikke, at `<input type="submit">` er en accessibility-fejl.

---

## Gennemgå alle formularer

Kontrollér formularerne i:

```text
index.html
news.html
games.html
contact.html
```

Vær især opmærksom på `contact.html`.

Kontrollér:

- Har hvert relevant felt et synligt og forståeligt label?
- Matcher `for` og `id`?
- Er alle `id`-værdier unikke?
- Har textarea et label?
- Har datalist-input et label?
- Er relevante `autocomplete`-værdier anvendt?
- Er formularens submit-handling tydelig?

---

# Opgave 9 – Kontrollér og optimér dokumentets `<head>`

Undersøg `<head>` i alle fire HTML-filer.

Formålet er ikke kun at finde fejl, men også at kunne genkende det, der allerede er korrekt, og vurdere, hvad der bør forbedres.

Kontrollér blandt andet:

- om dokumentets tegnsæt er angivet med `<meta charset="utf-8">`
- om `viewport` er angivet korrekt
- om hver side har en unik og beskrivende `<title>`
- om favicon og stylesheet er indlæst korrekt
- om elementerne i `<head>` er organiseret i en logisk og læsbar rækkefølge

## Stilladsering – tænk i denne rækkefølge

En vejledende struktur kan være:

```html
<head>
    <!-- tegnsæt -->

    <!-- viewport -->

    <!-- unik og beskrivende title -->

    <!-- favicon -->

    <!-- stylesheet -->
</head>
```

Du skal selv undersøge den eksisterende kode og afgøre, hvilke elementer der allerede er korrekte, hvilke der mangler, og hvilke der bør flyttes eller ændres.

En mulig færdig struktur kan eksempelvis ende sådan:

```html
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Marioclub - Contact</title>

    <link rel="shortcut icon" href="img/favicon.ico" type="image/x-icon">
    <link rel="stylesheet" href="css/style.css">
</head>
```

> Rækkefølgen af alle elementerne i `<head>` er ikke i sig selv et WCAG-krav. Det vigtigste er, at de nødvendige oplysninger er korrekte. `meta charset` bør dog placeres tidligt i `<head>`.

---

## Kontrollér dokumentets tegnsæt

Undersøg, om hver HTML-fil indeholder:

```html
<meta charset="utf-8">
```

Hvis den mangler, skal den tilføjes.

### Hvorfor er dette vigtigt?

`charset` fortæller browseren, hvilket tegnsæt dokumentet anvender.

Det hjælper browseren med at fortolke tekst og specialtegn korrekt.

---

## Kontrollér dokumentets sprog

Kontrollér også selve `<html>`-elementet.

Hvis starterfilen eksempelvis begynder sådan:

```html
<html>
```

skal du overveje, hvilket sprog siden er skrevet på.

Siderne i Marioclub-projektet er skrevet på engelsk.

### Korrekt princip

```html
<html lang="en">
```

### Hvorfor er dette bedre?

`lang`-attributten gør det muligt for browseren og hjælpemidler at identificere sidens primære sprog.

Det kan blandt andet have betydning for, hvordan skærmlæsere udtaler indholdet.

---

## Gør sidernes `<title>` unikke og beskrivende

Hvis flere sider bruger den samme generiske titel:

```html
<title>Marioclub</title>
```

bliver det vanskeligere at skelne siderne fra hinanden.

### Korrekt princip

Hver side skal have en kort, unik og beskrivende `<title>`, som både identificerer websitet og den aktuelle side.

Eksempel:

```html
<title>Marioclub - Home</title>
<title>Marioclub - News</title>
<title>Marioclub - Games</title>
<title>Marioclub - Contact</title>
```

### Hvorfor er dette bedre?

En beskrivende `<title>` hjælper brugeren med hurtigt at forstå, hvilken side der er åben, og gør det lettere at skelne mellem flere sider i blandt andet:

- browserfaner
- browserhistorik
- bogmærker
- hjælpemidler, som annoncerer sidens titel

Kontrollér og optimér `<title>` på alle fire HTML-sider.

---

# Opgave 10 – Test webtilgængelighed med WAVE og tastatur

Automatiske værktøjer kan finde mange accessibility-problemer, men ikke alle.

Du skal derfor kombinere **WAVE Evaluation Tool** med manuel tastaturtest.

---

## 10.1 – Test alle sider med WAVE

Installér **WAVE Evaluation Tool** som Chrome Extension.

Kør WAVE på:

```text
index.html
news.html
games.html
contact.html
```

Undersøg især kategorierne:

```text
Errors
Contrast Errors
Alerts
Features
Structure
ARIA
```

Du skal ikke blot forsøge at få alle markeringer til at forsvinde.

Undersøg først:

1. Hvad fortæller WAVE?
2. Hvilket HTML- eller CSS-element handler markeringen om?
3. Hvorfor er det et problem?
4. Kræver det faktisk en ændring?
5. Hvordan kan problemet løses uden at ødelægge sidens funktion eller design?

> WAVE er et analyseværktøj – ikke en automatisk facitliste.

---

## 10.2 – Undersøg Errors

Hvis WAVE finder fejl, skal du undersøge dem og rette relevante problemer.

Det kan eksempelvis være:

```text
Missing form label
Language missing or invalid
```

Brug WAVE til at lokalisere det konkrete element, og undersøg derefter HTML-koden i VS Code.

Når du har rettet problemet, skal du køre WAVE igen.

---

## 10.3 – Undersøg Contrast Errors

WAVE kan identificere tekst, hvor kontrasten mellem tekstfarve og baggrund er utilstrækkelig.

Hvis WAVE finder en kontrastfejl:

1. Find det relevante element.
2. Undersøg de anvendte farver i `css/style.css`.
3. Tilpas tekstfarve eller baggrundsfarve.
4. Bevar så vidt muligt sidens visuelle udtryk.
5. Kør WAVE igen og kontrollér, om problemet er løst.

Du skal ikke ændre farver tilfældigt. Brug værktøjets information til at finde den konkrete CSS-regel, der giver problemet.

---

## 10.4 – Undersøg Alerts

Et **Alert** i WAVE er ikke nødvendigvis en accessibility-fejl.

Hvis WAVE viser et alert, skal du:

- undersøge hvorfor elementet markeres
- vurdere om koden faktisk bør ændres
- kunne forklare din beslutning

Det er vigtigt at kunne skelne mellem:

```text
automatisk fundet fejl
og
noget der kræver menneskelig vurdering
```

---

## 10.5 – Test også med tastatur

Efter WAVE-testen skal du teste alle sider uden mus.

Brug:

```text
Tab
Shift + Tab
Enter
```

Kontrollér:

- Kan du nå alle links?
- Kan du nå alle formularfelter?
- Kan du nå submit-knapper?
- Kan navigationen bruges med tastaturet?
- Følger fokus en logisk rækkefølge?
- Kan du tydeligt se, hvilket element der har fokus?

Starterprojektets CSS indeholder allerede egne fokusregler.

Eksempel:

```css
form input:focus {
    border: 4px dashed #4B4B4B;
    outline: none;
}
```

`outline: none` er ikke automatisk en accessibility-fejl, hvis browserens standardfokus erstattes af en tydelig fokusindikator.

Din opgave er derfor at **teste fokusmarkeringen**, ikke blot at fjerne eller erstatte CSS-reglen mekanisk.

Hvis fokus ikke er tydeligt nok, skal du forbedre CSS'en og teste igen.

---

# Opgave 11 – Kør Lighthouse igen

Når du har gennemført optimeringerne, skal du køre Lighthouse igen.

Brug samme indstillinger som i din første test.

Sammenlign:

```text
Før optimering
vs.
Efter optimering
```

Dit mål er en **Performance-score på 90 eller højere**.

Kør også Lighthouse-kategorien **Accessibility**.

Lighthouse kan hjælpe med at finde en række accessibility-problemer, men en høj Lighthouse-score er ikke i sig selv bevis på, at en side er fuldt tilgængelig.

Du skal derfor kombinere Lighthouse med:

- WAVE
- HeadingsMap
- manuel tastaturtest
- kontrol af formularlabels
- kontrol af `autocomplete`
- kontrol af alt-tekster
- HTML-validering

---

# Dokumentér dine resultater

Notér resultaterne før og efter optimering.

Du kan eksempelvis bruge denne tabel:

| Side | Performance før | Performance efter | Accessibility efter |
|---|---:|---:|---:|
| `index.html` |  |  |  |
| `news.html` |  |  |  |
| `games.html` |  |  |  |
| `contact.html` |  |  |  |

Skriv derefter kort:

1. Hvilke ændringer gav den største performanceforbedring?
2. Hvilke accessibility-problemer fandt du?
3. Hvilke problemer kunne Lighthouse finde?
4. Hvilke problemer fandt WAVE?
5. Hvilke problemer krævede HeadingsMap eller manuel kontrol?
6. Hvad har du lært om sammenhængen mellem performance og accessibility?

---

# Kontrol af din løsning

Inden du afslutter opgaven, skal du kontrollere:

- [ ] Lighthouse er kørt før ændringerne.
- [ ] Performance-resultaterne før optimering er dokumenteret.
- [ ] Relevante billeder er konverteret til WebP.
- [ ] HTML-filerne anvender de nye WebP-filer.
- [ ] Billedkvaliteten er kontrolleret.
- [ ] Relevante billeder længere nede på siden bruger `loading="lazy"`.
- [ ] Vigtige billeder øverst på siden er ikke lazy-loadet uden grund.
- [ ] Alt-teksterne er gennemgået.
- [ ] Dekorative billeder er vurderet i forhold til `alt=""`.
- [ ] Headingstrukturen er kontrolleret med HeadingsMap både før og efter ændringer.
- [ ] Den aktuelle navigationsside anvender `aria-current="page"`.
- [ ] Formularfelter har relevante labels.
- [ ] `for` og `id` matcher.
- [ ] `textarea` har et label.
- [ ] `datalist`-input har et label.
- [ ] Relevante `autocomplete`-værdier er anvendt.
- [ ] Formularer har en tydelig submit-handling.
- [ ] Eksisterende gyldige submit-kontroller er vurderet, før de eventuelt ændres.
- [ ] Dokumentets tegnsæt er kontrolleret og er korrekt angivet med `<meta charset="utf-8">`.
- [ ] `<head>` er organiseret i en logisk og læsbar rækkefølge.
- [ ] Dokumentets primære sprog er angivet med `lang="en"` på `<html>`.
- [ ] Alle fire sider har en unik og beskrivende `<title>`.
- [ ] CSS er kontrolleret efter ændringer i HTML-strukturen.
- [ ] Alle fire sider er testet med WAVE.
- [ ] Relevante WAVE Errors er undersøgt og udbedret.
- [ ] WAVE Contrast Errors er undersøgt og udbedret, hvor det var nødvendigt.
- [ ] WAVE Alerts er undersøgt og vurderet.
- [ ] Alle interaktive elementer har en tydelig synlig fokusmarkering.
- [ ] Siderne er testet med tastatur.
- [ ] HTML-koden er valideret.
- [ ] Lighthouse er kørt igen efter optimering.
- [ ] Performance-score er 90 eller højere.
- [ ] Resultater før og efter er sammenlignet.

---

# Værktøjer i opgaven

| Værktøj | Anvendelse |
|---|---|
| **Lighthouse** | Performance og overordnet accessibility-audit før og efter optimering |
| **WAVE** | Accessibility-fejl, kontrast, alerts, struktur og ARIA |
| **HeadingsMap** | Visualisering og analyse af headinghierarki |
| **Chrome DevTools** | Network, responsive test og undersøgelse af HTML/CSS |
| **W3C Validator** | Validering af HTML-koden |
| **Tastatur** | Manuel test af navigation, formularer og fokus |

---

# Useful Links / Nyttige links

## Chrome DevTools

[Chrome DevTools](https://developer.chrome.com/docs/devtools/)

## Lighthouse

[Lighthouse](https://developer.chrome.com/docs/lighthouse/)

[Lighthouse i Chrome DevTools](https://developer.chrome.com/docs/devtools/lighthouse/)

## WebP

[Google WebP](https://developers.google.com/speed/webp/)

## Billedværktøjer

[GIMP](https://www.gimp.org/)

[GIMP – Export Image as WebP](https://docs.gimp.org/3.0/en/file-webp-export.html)

[XnConvert](https://www.xnview.com/en/xnconvert/)

[ImageMagick](https://imagemagick.org/)

## Accessibility-værktøjer

- WAVE Evaluation Tool – Chrome Extension
- HeadingsMap – Chrome Extension

## HTML og accessibility

[MDN – Heading elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)

[MDN – label](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/label)

[MDN – placeholder](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/placeholder)

[MDN – autocomplete](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/autocomplete)

[MDN – button](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/button)

[MDN – datalist](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/datalist)

[MDN – aria-current](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-current)

[W3C – Understanding Identify Input Purpose](https://www.w3.org/WAI/WCAG22/Understanding/identify-input-purpose.html)

[W3C HTML Validator](https://validator.w3.org/)

---

## Afsluttende note

> Udviklet til studerende på **3. semester**. Ingen AI-værktøjer er nødvendige — opgaven kan løses med en browser, en teksteditor, et tastatur og et simpelt billedværktøj.
