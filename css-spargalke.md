# CSS špargalkė

## Turinys
1. [CSS prijungimas](#1-css-prijungimas)
2. [Selektoriai](#2-selektoriai)
3. [Specifiškumas ir kaskada](#3-specifiškumas-ir-kaskada)
4. [Paveldėjimas](#4-paveldėjimas)
5. [Vienetai](#5-vienetai)
6. [Spalvos](#6-spalvos)
7. [Tekstas ir šriftai](#7-tekstas-ir-šriftai)
8. [Box model](#8-box-model)
9. [Display](#9-display)
10. [Fonas](#10-fonas)
11. [Rėmeliai, šešėliai, kampai](#11-rėmeliai-šešėliai-kampai)
12. [Position ir z-index](#12-position-ir-z-index)
13. [Transform ir transition](#13-transform-ir-transition)
14. [Overflow](#14-overflow)
15. [Media queries](#15-media-queries)
16. [Kintamieji](#16-kintamieji)

---

## 1. CSS prijungimas

```html
<link rel="stylesheet" href="css/style.css">
```
- Rašoma `<head>` viduje.
- Kelias – nuo **HTML failo** vietos.
- Kitame aplanke esantis HTML: `href="../css/style.css"`.

Taisyklės sandara:
```css
selektorius {
    savybe: reiksme;
}
```

---

## 2. Selektoriai

| Selektorius | Pvz. | Ką pasirenka |
|---|---|---|
| Visi | `*` | Visus elementus |
| Žymė | `p` | Visus `<p>` |
| Klasė | `.card` | Visus su `class="card"` |
| ID | `#logo` | Elementą su `id="logo"` (**stiliams nenaudoti**) |
| Grupavimas | `h1, h2, p` | Visus išvardintus |
| Palikuonis | `.nav a` | Visus `a` **bet kur** `.nav` viduje |
| Tiesioginis vaikas | `.nav > li` | Tik **tiesioginius** `li` vaikus |
| Kaimynas | `h2 + p` | `p`, kuris **iškart po** `h2` |
| Atributas | `input[type="email"]` | `input` su tokiu atributu |
| Dvi klasės kartu | `.btn.btn--big` | Elementą, turintį **abi** klases |

### Pseudo klasės (`:`)
| Selektorius | Kada veikia |
|---|---|
| `:hover` | Užvedus pelę |
| `:focus` | Paspaudus ant laukelio |
| `:active` | Spaudžiant |
| `:first-child` | Pirmas vaikas (`li:first-child` – **li**, kuris yra pirmas) |
| `:last-child` | Paskutinis vaikas |
| `:nth-child(2)` | Antras vaikas |
| `:nth-child(odd)` / `(even)` | Nelyginiai / lyginiai (zebra lentelėms) |
| `:not(.active)` | Visi, **išskyrus** `.active` |
| `:checked` | Pažymėtas radio / checkbox |

### Pseudo elementai (`::`)
| Selektorius | Ką daro |
|---|---|
| `::before` | Prideda turinį **prieš** elemento turinį (reikia `content: "";`) |
| `::after` | Prideda turinį **po** |
| `::placeholder` | Placeholder teksto stilius |
| `::first-letter` | Pirma raidė |

```css
.title::after {
    content: "";
    display: block;
    width: 3rem;
    height: 0.25rem;
    background-color: orange;    /* linija po antrašte */
}
```

---

## 3. Specifiškumas ir kaskada

Kai keli selektoriai keičia tą pačią savybę – laimi **stipresnis**.

| Kas | Svoris |
|---|---|
| `style="..."` HTML | 1-0-0-0 |
| `#id` | 0-1-0-0 |
| `.klase`, `:hover`, `[atributas]` | 0-0-1-0 |
| `zyme`, `::before` | 0-0-0-1 |

Pavyzdžiai:
- `p` → 0-0-0-1
- `.card` → 0-0-1-0
- `.card p` → 0-0-1-1 (**laimi** prieš `.card`)
- `.nav .nav__link:hover` → 0-0-3-0

**Taisyklės:**
1. Laimi didesnis specifiškumas (nepriklausomai nuo tvarkos).
2. Jei vienodas – laimi tas, kuris parašytas **žemiau**.
3. `!important` – nugali viską (**nenaudoti**).

---

## 4. Paveldėjimas

**Paveldima** (užtenka nustatyti `body`): `color`, `font-family`, `font-size`, `font-weight`, `line-height`, `text-align`, `list-style`

**Nepaveldima**: `margin`, `padding`, `border`, `background`, `width`, `height`, `display`, `position`

Priverstinai paveldėti: `color: inherit;`

---

## 5. Vienetai

| Vienetas | Nuo ko skaičiuojamas | Kada naudoti |
|---|---|---|
| `rem` | `html` šrifto dydžio (16px) | **Beveik visur**: šriftai, tarpai, pločiai |
| `em` | **tėvo** šrifto dydžio | Tarpai, kurie turi augti kartu su elemento šriftu (mygtuko padding) |
| `%` | tėvo dydžio | Pločiai (`width: 50%`) |
| `vh` | 1% ekrano **aukščio** | `min-height: 100vh` |
| `vw` | 1% ekrano **pločio** | Retai |
| `fr` | laisvos vietos dalis | Tik grid |
| `px` | fiksuoti pikseliai | **Atsiskaityme negalima** |

**px → rem** (padalink iš 16):

| px | rem |
|---|---|
| 1 | 0.0625 |
| 2 | 0.125 |
| 4 | 0.25 |
| 8 | 0.5 |
| 12 | 0.75 |
| 14 | 0.875 |
| 16 | 1 |
| 18 | 1.125 |
| 20 | 1.25 |
| 24 | 1.5 |
| 32 | 2 |
| 40 | 2.5 |
| 48 | 3 |
| 64 | 4 |
| 768 | 48 |
| 1024 | 64 |
| 1200 | 75 |

---

## 6. Spalvos

| Formatas | Pvz. |
|---|---|
| Pavadinimas | `red`, `white`, `transparent` |
| HEX | `#ff0000`, trumpai `#f00` |
| HEX su skaidrumu | `#ff000080` (paskutiniai 2 – skaidrumas) |
| RGB | `rgb(255, 0, 0)` |
| RGBA | `rgba(255, 0, 0, 0.5)` – 0.5 = 50% skaidrumas |
| HSL | `hsl(0, 100%, 50%)` |

`opacity: 0.5;` – permatomas **visas** elementas (su turiniu), `rgba` – tik ta spalva.

---

## 7. Tekstas ir šriftai

| Savybė | Pvz. | Ką daro |
|---|---|---|
| `font-family` | `"Roboto", sans-serif` | Šriftas (+ atsarginis) |
| `font-size` | `1.25rem` | Dydis |
| `font-weight` | `400`, `700`, `bold` | Storis |
| `font-style` | `italic` | Pasviręs |
| `line-height` | `1.5` | Eilutės aukštis (be vienetų) |
| `color` | `#333` | Teksto spalva |
| `text-align` | `center`, `left`, `right`, `justify` | Lygiavimas |
| `text-decoration` | `none`, `underline` | Pabraukimas |
| `text-transform` | `uppercase`, `capitalize` | DIDŽIOSIOS raidės |
| `letter-spacing` | `0.1rem` | Tarpai tarp raidžių |
| `list-style` | `none` | Nuima sąrašo taškus |

---

## 8. Box model

```
┌─────────── margin ───────────┐
│ ┌───────── border ─────────┐ │
│ │ ┌─────── padding ──────┐ │ │
│ │ │       turinys        │ │ │
│ │ └──────────────────────┘ │ │
│ └──────────────────────────┘ │
└──────────────────────────────┘
```

| Savybė | Ką daro |
|---|---|
| `padding` | Tarpas **viduje** (tarp turinio ir rėmelio) – fonas matosi |
| `margin` | Tarpas **išorėje** (tarp elementų) – permatomas |
| `border` | Rėmelis |
| `width` / `height` | Plotis / aukštis |
| `max-width` | Maksimalus plotis |
| `min-height` | Minimalus aukštis |
| `box-sizing: border-box` | `width` įskaičiuoja padding ir border |

**Trumpiniai (margin ir padding vienodai):**
```css
padding: 1rem;                 /* visos 4 pusės */
padding: 1rem 2rem;            /* viršus/apačia | kairė/dešinė */
padding: 1rem 2rem 3rem;       /* viršus | kairė/dešinė | apačia */
padding: 1rem 2rem 3rem 4rem;  /* viršus | dešinė | apačia | kairė (laikrodžio rodykle) */
margin: 0 auto;                /* centruoja block elementą (reikia width/max-width) */
```

---

## 9. Display

| Reikšmė | Ką daro |
|---|---|
| `block` | Visas plotis, nauja eilutė, galima `width`/`height` |
| `inline` | Eilutėje, tik turinio dydžio, **neveikia** `width`/`height` ir vertikalus `margin` |
| `inline-block` | Eilutėje, bet **galima** keisti dydį |
| `none` | Paslepia (neužima vietos) |
| `flex` | Žr. `flex.md` |
| `grid` | Žr. `grid.md` |

`visibility: hidden;` – paslepia, bet **vieta lieka**.

---

## 10. Fonas

```css
.hero {
    background-color: #222;                      /* jei nuotrauka neužsikrauna */
    background-image: url("../img/hero.jpg");    /* kelias NUO CSS FAILO */
    background-size: cover;                      /* uždengia visą dėžutę */
    background-position: center;
    background-repeat: no-repeat;
}
```

| `background-size` | Ką daro |
|---|---|
| `cover` | Uždengia **visą dėžutę**, gali apkirpti |
| `contain` | Telpa **visa nuotrauka** dėžutėje, gali likti tuščių vietų |

**Tamsus sluoksnis ant nuotraukos:**
```css
background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url("../img/hero.jpg");
```

**Gradientas:**
```css
background: linear-gradient(to right, #2a6f97, #61a5c2);
```

---

## 11. Rėmeliai, šešėliai, kampai

```css
border: 0.0625rem solid #ccc;    /* storis | stilius | spalva */
border-bottom: 0.125rem solid red;
border-radius: 0.5rem;           /* suapvalinti kampai */
border-radius: 50%;              /* apskritimas (kai plotis = aukštis) */
box-shadow: 0 0.25rem 0.5rem rgba(0, 0, 0, 0.2);   /* x | y | blur | spalva */
text-shadow: 0.0625rem 0.0625rem 0.125rem #000;
outline: none;                   /* nuima mėlyną rėmelį paspaudus laukelį */
```
Border stiliai: `solid`, `dashed`, `dotted`, `double`, `none`.

---

## 12. Position ir z-index

| Reikšmė | Ką daro |
|---|---|
| `static` | Numatyta, įprastas srautas |
| `relative` | Lieka savo vietoje, bet galima pastumti `top/left`. **Dažniausiai – tėvas absolute vaikui** |
| `absolute` | **Iškrenta iš srauto**, pozicionuojamas nuo artimiausio **ne static** tėvo |
| `fixed` | Prikabintas prie **ekrano** (nejuda slenkant) |
| `sticky` | Įprastas, kol nuslenki iki `top: 0`, tada prilimpa |

```css
.card {
    position: relative;          /* atskaitos taškas */
}

.card__badge {
    position: absolute;
    top: 1rem;
    right: 1rem;                 /* dešiniame viršutiniame kampe */
}

.header {
    position: sticky;
    top: 0;
    z-index: 10;                 /* didesnis z-index = arčiau žiūrovo */
}
```
`z-index` veikia tik elementams su `position` (ne `static`), flex ir grid vaikams.

**Centruoti absolute elementą:**
```css
.center {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
```

---

## 13. Transform ir transition

| Transform | Ką daro |
|---|---|
| `translate(2rem, 1rem)` | Pastumia (x, y) |
| `translateY(-0.5rem)` | Pakelia aukštyn |
| `scale(1.1)` | Padidina 10% |
| `rotate(45deg)` | Pasuka |
| `skew(10deg)` | Pakreipia |

Kelios kartu: `transform: translateY(-0.5rem) scale(1.05);`

```css
.card {
    transition: transform 0.3s ease;     /* savybė | trukmė | eiga */
}

.card:hover {
    transform: translateY(-0.5rem);
}
```
`transition` rašomas **pagrindiniam** elementui, ne `:hover`.
`transition: all 0.3s;` – visoms savybėms.

---

## 14. Overflow

| Reikšmė | Ką daro |
|---|---|
| `visible` | Numatyta, turinys išlenda |
| `hidden` | Kas išlenda – paslepiama (naudinga su `border-radius`) |
| `scroll` | Visada slinkimo juosta |
| `auto` | Slinkimo juosta, tik jei reikia |

Ilgas tekstas su `...`:
```css
.text {
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}
```

---

## 15. Media queries

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
**Be šios eilutės media queries telefone neveiks.**

**Mobile first** – pirma rašai stilius telefonui, tada `min-width` – kas keičiasi didesniame ekrane:
```css
.cards {
    flex-direction: column;
}

@media (min-width: 48rem) {      /* nuo 768px ir daugiau */
    .cards {
        flex-direction: row;
    }
}
```

| Ekranas | min-width |
|---|---|
| Didesnis telefonas | `36rem` (576px) |
| Planšetė | `48rem` (768px) |
| Kompiuteris | `64rem` (1024px) |
| Didelis ekranas | `75rem` (1200px) |

- `min-width` – „**nuo** tokio pločio ir didesni“ (mobile first).
- `max-width` – „**iki** tokio pločio“ (desktop first).
- Media queries rašomi **failo apačioje**, kad perrašytų viršuje esančius.

Patikrinti: naršyklėje **`F12`** → **`Ctrl + Shift + M`** (telefono vaizdas).

---

## 16. Kintamieji

```css
:root {
    --color-main: #2a6f97;
    --space: 1rem;
}

.btn {
    background-color: var(--color-main);
    padding: var(--space);
}
```
Pakeitus vienoje vietoje – pasikeičia visur.
