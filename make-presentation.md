# Prompt: Maak een HTML-presentatie

Maak een volledige, zelfstandige HTML-presentatie als één `index.html` bestand (met een losse `style.css`).
De presentatie draait volledig in de browser — geen frameworks, geen build-stap.

---

## Wat ik wil opgeven

- **Titel** van de presentatie: `[TITEL]`
- **Auteur / spreker**: `[NAAM]` – `[ROL]`
- **Onderwerp / context**: `[BESCHRIJVING]`
- **Slides / secties** (geef per slide een titel + kerninhoud):
  1. Hero / titelpagina
  2. Agenda / overzicht
  3. … (voeg zelf slides toe)
  4. Afsluiting / bedankt

---

## Technische vereisten

### Structuur
- Elke slide is een `<section>` met `height: 100vh` en `scroll-snap-align: start`
- De body heeft `scroll-snap-type: y mandatory` zodat je per slide scrolt
- Navigatie via scrollwiel, pijltjestoetsen én klikbare dot-navigatie (rechts in beeld)
- Boven-in een vaste `<nav>` met de titel en een slideteller

### Animaties
- Elementen verschijnen met `.reveal` (fade + slide omhoog) zodra de slide in beeld komt
- Gebruik `IntersectionObserver` om `.visible` toe te voegen
- Staggered delays via `.d1` t/m `.d5`

### Preloader
- Volledig-scherm preloader die verdwijnt zodra alle afbeeldingen geladen zijn
- Voortgangsbalk op basis van `document.images` load-events
- Fallback-timeout van 6 seconden

### Slides – beschikbare layouts
Gebruik één van deze layouts per sectie, naar keuze:

| Layout | Beschrijving |
|--------|-------------|
| `hero` | Fullscreen achtergrondafbeelding, grote titel, subtitle, naam/rol |
| `agenda-grid` | 2×3 kaartjesraster met genummerde items |
| `stats` | Links een mockup/afbeelding, rechts stat-pills met getallen |
| `two-col` | Twee gelijke kolommen (tekst + visueel) |
| `three-cards` | Drie kaarten naast elkaar (icon + titel + tekst) |
| `chat` | Geanimeerde chat-berichten tussen twee of meer personen |
| `org-chart` | Organogram met root → branches → items |
| `timeline` | Horizontale of verticale tijdlijn |
| `closing` | Donkere afsluiting met foto-cirkels, naam en rol per persoon |

### Afbeeldingen
- Zet alle afbeeldingen in een `images/` submap
- Verwijs ernaar als `images/bestandsnaam.ext`
- Gebruik `https://images.unsplash.com/…?w=800&q=80` als plaatshouder indien geen eigen afbeeldingen beschikbaar zijn

### CSS
- Gebruik `clamp()` voor alle font-sizes zodat het schaalbaar is
- CSS variabelen in `:root` voor kleuren
- Geen externe CSS-frameworks — puur vanilla CSS

### JavaScript
- Puur vanilla JS, geen dependencies
- Scroll-snap navigatie + keyboard (ArrowUp/ArrowDown)
- IntersectionObserver voor reveal-animaties
- Dot-navigatie links met actieve staat

---

## Wat ik terugkrijg

1. `index.html` — volledige HTML met alle secties
2. `style.css` — alle stijlen
3. Een `images/` map structuur (of verwijzingen naar Unsplash placeholders)

---

## Voorbeeld aanroep

> Maak een HTML-presentatie over het jaarplan 2026 van het marketingteam.
> Auteur: Lisa van den Berg, Marketing Manager.
> Slides:
> 1. Hero: "Marketing 2026"
> 2. Agenda: 6 onderwerpen (Doelen, Budget, Campagnes, Team, Tools, Tijdlijn)
> 3. Doelen: 3 KPI-kaarten
> 4. Budget: Staafgrafiek + toelichting
> 5. Team: Organogram
> 6. Afsluiting: Bedankt + foto's teamleden
