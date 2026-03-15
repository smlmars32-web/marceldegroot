# Prompt: Maak een presentatie in de Vegro BotNet-stijl

Maak een HTML-presentatie die **exact de stijl volgt** van de Vegro BotNet Attack-presentatie in de `botnet/` map.
Gebruik dezelfde structuur, CSS-variabelen, componenten en animaties — pas alleen de inhoud aan.

---

## Inhoud die ik wil opgeven

- **Titel**: `[TITEL]`
- **Auteur**: `[NAAM]` – `[ROL]`
- **Achtergrondafbeelding hero**: `images/[BESTAND]`
- **Accentkleur** (optioneel, standaard navy `#005695` + green `#7ec07b`): `[KLEUR HEX]`
- **Slides**: (zie onderaan)

---

## Design-systeem — NIET wijzigen

### Kleuren (`:root`)
```css
--navy:      #005695;
--navy-mid:  #004a82;
--blue-lt:   #3a87cc;
--green:     #7ec07b;
--green-dk:  #5da45a;
--bg-light:  #f1f6fb;
--orange:    #e56a54;
--text-muted: rgba(0,86,149,.45);
```

### Typografie
- Font: **Baloo Chettan 2** (Google Fonts, weights 400/500/600/700/800)
- Alle font-sizes via `clamp(min, vw, max)` — nooit vaste `px` voor tekst
- Titels: `font-weight: 800–900`

### Paginastructuur
```html
<body>
  <!-- Preloader -->
  <div id="preloader"> … </div>

  <!-- Dot-navigatie (rechts) -->
  <div class="slide-dots" id="slideDots"></div>
  <div class="slide-counter" id="slideCounter"></div>

  <!-- Vaste nav -->
  <nav> … </nav>

  <!-- Slides -->
  <section class="parallax-section"> … </section>
  …

  <!-- Footer -->
  <footer> … </footer>
</body>
```

Elke `<section>` heeft:
- `class="parallax-section"` → `height:100vh`, `scroll-snap-align:start`
- Een `<div class="parallax-bg">` voor de achtergrond
- Een `<div class="section-content">` → `<div class="section-inner">`
- Wave-dividers boven/onder met `<div class="wave-bottom"><svg…></div>`

---

## Beschikbare slide-componenten

### 1. Hero
```html
<section id="hero" class="parallax-section">
  <div class="parallax-bg" id="heroBg"
       style="background: linear-gradient(to right, rgba(0,0,0,1) 0%, rgba(0,0,0,0) 100%),
              url('images/FOTO.jpg') 80% center/cover no-repeat;">
  </div>
  <div class="section-content">
    <div class="hero-inner">
      <div>
        <h1 class="hero-title reveal d1">
          <span class="glitch" data-text="WOORD" style="color:#e53935;">WOORD</span>Titel
        </h1>
      </div>
    </div>
  </div>
  <!-- Naam + rol linksonder -->
  <div class="reveal" style="position:absolute;bottom:8rem;left:3rem;z-index:4;">
    <div style="font-size:clamp(2rem,3vw,2.8rem);font-weight:700;color:#fff;">Naam</div>
    <div style="font-size:clamp(1.5rem,2vw,2rem);color:rgba(255,255,255,.5);">Rol</div>
  </div>
  <div class="wave-bottom"><svg viewBox="0 0 1440 80" preserveAspectRatio="none" fill="#f1f6fb">
    <path d="M0,40 C320,80 720,0 1080,50 C1200,65 1320,30 1440,40 L1440,80 L0,80 Z"/>
  </svg></div>
</section>
```

### 2. Agenda (2×3 grid)
```html
<div class="agenda-grid">
  <div class="agenda-card reveal d1">
    <div class="agenda-num">01</div>
    <h3>Onderwerp</h3>
    <p>Korte omschrijving</p>
    <img class="step-img" src="https://images.unsplash.com/…?w=800&q=80" alt="">
  </div>
  <!-- herhaal voor 02–06 -->
</div>
```
Accentueer een kritieke kaart met `style="border-top-color:#c62828;"`.

### 3. Organogram
```html
<div class="org-chart reveal d1">
  <div class="oc-root">Hoofd <span class="oc-sub">(Functietitel)</span></div>
  <div class="oc-connector-root"></div>
  <div class="oc-branches">
    <div class="oc-branch">
      <div class="oc-branch-line"></div>
      <div class="oc-branch-head">Afdeling A <span class="oc-sub">(Manager)</span></div>
      <div class="oc-items">
        <div class="oc-item">Taak 1</div>
        <div class="oc-item">Taak 2</div>
      </div>
    </div>
    <!-- herhaal voor meer branches -->
  </div>
</div>
```

### 4. Website-monitor stage (3-koloms device mock)
```html
<div class="ws-stage reveal d1">
  <div class="ws-col">
    <div class="ws-monitor">
      <div class="ws-screen-wrap">
        <div class="ws-screen" style="padding:0;overflow:hidden;">
          <img src="images/screenshot.png" style="width:100%;height:100%;object-fit:cover;object-position:top;">
        </div>
      </div>
      <div class="ws-stand"></div><div class="ws-base"></div><div class="ws-shadow"></div>
      <div class="ws-label"><span class="ws-dot" style="background:var(--green);"></span>Label</div>
    </div>
  </div>
  <!-- voeg ws-monitor.lg toe voor midden-kolom (groot scherm) -->
</div>
```

### 5. Stats (monitor links + pills rechts)
```html
<div class="stats-layout">
  <div class="monitor-wrap reveal-l">
    <div class="monitor">
      <div class="monitor-screen" style="padding:0;overflow:hidden;">
        <img src="images/screenshot.png" style="width:100%;height:100%;object-fit:cover;object-position:top;">
      </div>
    </div>
    <div class="monitor-stand"></div>
    <div class="monitor-base"></div>
  </div>
  <div class="stats-right">
    <div class="stat-pill reveal d1">
      <span class="icon">📊</span>
      <div>
        <div class="num">42 <span>k</span></div>
        <div class="lbl">Omschrijving van de stat</div>
      </div>
    </div>
    <!-- herhaal voor meer pills -->
  </div>
</div>
```

### 6. Aanval / Drama sectie
Gebruik een donkere achtergrond (`background:#0a0505`) met de volgende drama-elementen:
```html
<div class="attack-ip-bg" id="attackIpBg"></div>
<div class="attack-vignette"></div>
<div class="attack-scan"></div>
<div class="attack-alert-bar">⚠ KRITIEKE MELDING — TEKST — ⚠</div>
```
Titels krijgen class `glitch`, de CPU-grafiek krijgt class `danger`.
Gebruik `#attack .consequence`, `#attack .section-title` etc. overrides die al in `style.css` staan.

### 7. Chat-feed
```html
<div class="ct-wrap">
  <div class="chat-feed">
    <div class="chat-feed-inner">
      <div class="chat-msg cm-vegro">
        <img class="chat-av" src="images/logo-vegro.png" alt="Vegro">
        <div class="chat-bubble-wrap">
          <div class="chat-sender">Vegro</div>
          <div class="chat-bubble">Bericht tekst…</div>
        </div>
      </div>
      <div class="chat-msg cm-asker">
        <img class="chat-av" src="images/logo asker.jpg" alt="Asker">
        <div class="chat-bubble-wrap">
          <div class="chat-sender">Asker</div>
          <div class="chat-bubble">Antwoord tekst…</div>
        </div>
      </div>
    </div>
  </div>
</div>
```
Stuur berichten geanimeerd met JS: `setTimeout` + `classList.add('cm-in')` per bericht.

### 8. Oplossing (stappen + architectuurdiagram)
```html
<div class="solution-layout">
  <div class="sol-steps">
    <div class="sol-step reveal d1">
      <div class="sol-icon-box">🛡️</div>
      <div>
        <h4>Stap titel</h4>
        <p>Toelichting</p>
      </div>
    </div>
  </div>
  <div class="arch-box reveal-r d2">
    <h4>Architectuur</h4>
    <div class="arch-flow">
      <div class="anode anode-bad">Aanvaller / Bron</div>
      <div class="arch-arr">↓</div>
      <div class="anode anode-waf">WAF / Filter</div>
      <div class="arch-arr">↓</div>
      <div class="anode anode-app">Applicatie</div>
    </div>
  </div>
</div>
```

### 9. Vervolgstappen (3-koloms cards met status)
```html
<div class="fu-grid">
  <div class="fu-card reveal d1">
    <div class="ficn">🔒</div>
    <h3>Maatregel titel</h3>
    <p>Omschrijving</p>
    <div class="fu-status fs-done">✓ Gereed</div>
  </div>
  <!-- fs-wip = In uitvoering | fs-plan = Gepland -->
</div>
```

### 10. Afsluiting (donker, foto-cirkels)
```html
<section id="thanks" class="parallax-section">
  <div class="parallax-bg" style="background: linear-gradient(rgba(2,13,26,.45),rgba(2,13,26,.45)),
       url('images/FOTO.webp') center/cover no-repeat;">
  </div>
  <div class="thanks-overlay"></div>
  <div class="section-content">
    <div class="thanks-inner">
      <h2 class="thanks-title">Bedankt</h2>
      <p class="thanks-sub">Ondertitel / tagline</p>
      <div class="thanks-circles">
        <div class="thanks-circle">
          <img class="thanks-circ-img" src="images/logo.png" alt="Naam">
          <div class="thanks-circ-name">Naam</div>
          <div class="thanks-circ-org">Organisatie</div>
          <div class="thanks-circ-role">Rol / functie</div>
        </div>
      </div>
    </div>
  </div>
</section>
```

---

## Wave-dividers — kleurverwijzing

| Van sectie → naar    | `fill` waarde       |
|----------------------|---------------------|
| Hero → Agenda        | `#f1f6fb`           |
| Agenda → Team        | `#fff`              |
| Team → Websites      | `var(--bg-light)`   |
| Websites → Stats     | `#fff`              |
| Stats → Attack       | `var(--bg-light)`   |
| Attack → Steps       | `#fff`              |
| Steps → Call         | `var(--bg-lighter)` |
| Call → Solution      | `#fff`              |
| Solution → Followup  | `var(--bg-light)`   |
| Followup → Thanks    | `#fff`              |

---

## JavaScript — verplichte blokken

```js
// 1. Scroll-snap navigatie
const sections = Array.from(document.querySelectorAll('.parallax-section, footer'));
function goTo(idx) { sections[idx]?.scrollIntoView({ behavior: 'smooth' }); }
document.addEventListener('keydown', e => {
  if (e.key === 'ArrowDown') goTo(getCurrentIdx() + 1);
  if (e.key === 'ArrowUp')   goTo(getCurrentIdx() - 1);
});

// 2. IntersectionObserver voor .reveal
const ro = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) e.target.classList.add('visible');
    else e.target.classList.remove('visible');
  });
}, { threshold: 0.15 });
document.querySelectorAll('.reveal, .reveal-l, .reveal-r').forEach(el => ro.observe(el));

// 3. Dot-navigatie opbouwen
// (genereer een .slide-dot per sectie, markeer actieve via IntersectionObserver)

// 4. Preloader
const imgs = Array.from(document.images);
// … (zie make-presentation.md voor volledige implementatie)
```

---

## Bestandsstructuur verwacht output

```
[projectnaam]/
├── index.html
├── style.css          ← identiek aan botnet/style.css, inhoud ongewijzigd
└── images/
    ├── logo.png
    ├── hero-bg.jpg
    └── …
```

---

## Voorbeeld aanroep

> Maak een presentatie in de Vegro BotNet-stijl over een datalek bij een ziekenhuis.
> Titel: "Data Breach — Ziekenhuis Noord"
> Auteur: Ahmed Yilmaz, CISO
> Hero-afbeelding: images/hospital.jpg
> Slides:
> 1. Hero
> 2. Agenda (6 items: Team, Systemen, Incident, Impact, Oplossing, Vervolgstappen)
> 3. IT-team organogram
> 4. Getroffen systemen (monitor-stage)
> 5. Impact stats
> 6. Drama-slide: het datalek
> 7. Chat: communicatie tijdens incident
> 8. Oplossing + architectuur
> 9. Vervolgstappen
> 10. Afsluiting
