# Flexbox – špargalkė su pavyzdžiais

## Pagrindas

Flex dedamas **tėvui**, o jo **tiesioginiai vaikai** išsirikiuoja.

```html
<div class="tevas">
    <div class="vaikas">1</div>
    <div class="vaikas">2</div>
    <div class="vaikas">3</div>
</div>
```

```css
.tevas {
    display: flex;
}
```

### Ašys
- **Pagrindinė ašis** (main axis) – kryptis, kuria eina vaikai. Pagal nutylėjimą → (eilutė).
- **Skersinė ašis** (cross axis) – statmena pagrindinei.

| Savybė | Kuria ašimi |
|---|---|
| `justify-content` | **pagrindine** |
| `align-items` | **skersine** |

> Jei `flex-direction: column` – ašys **apsikeičia**: `justify-content` veikia vertikaliai, `align-items` – horizontaliai.

---

## Savybės TĖVUI

| Savybė | Reikšmės | Ką daro |
|---|---|---|
| `display` | `flex` | Įjungia flex |
| `flex-direction` | `row` (numatyta), `column`, `row-reverse`, `column-reverse` | Kryptis: eilute ar stulpeliu |
| `justify-content` | `flex-start`, `center`, `flex-end`, `space-between`, `space-around`, `space-evenly` | Lygiavimas pagrindine ašimi |
| `align-items` | `stretch` (numatyta), `center`, `flex-start`, `flex-end` | Lygiavimas skersine ašimi |
| `flex-wrap` | `nowrap` (numatyta), `wrap` | Ar netelpantys vaikai keliasi į kitą eilutę |
| `gap` | `1rem` | Tarpas tarp vaikų |
| `align-content` | kaip `justify-content` | Kelių eilučių lygiavimas (tik su `wrap`) |

### justify-content vizualiai
```
flex-start     [1][2][3]
center              [1][2][3]
flex-end                 [1][2][3]
space-between  [1]       [2]       [3]
space-around    [1]     [2]     [3]
space-evenly     [1]    [2]    [3]
```

---

## Savybės VAIKUI

| Savybė | Pvz. | Ką daro |
|---|---|---|
| `flex: 1` | `flex: 1;` | Užima visą laisvą vietą (keli su `flex: 1` – po lygiai) |
| `flex-grow` | `2` | Kiek dalių laisvos vietos pasiima |
| `flex-shrink` | `0` | `0` – neleidžia susitraukti |
| `flex-basis` | `15rem` | Pradinis plotis prieš dalinant vietą |
| `align-self` | `center` | Šio vieno vaiko `align-items` |
| `order` | `-1` | Tvarka (mažesnis – pirmesnis) |

---

## 1. Centruoti elementą (horizontaliai ir vertikaliai)

```html
<section class="hero">
    <h1 class="hero__title">Sveiki</h1>
</section>
```
```css
.hero {
    display: flex;
    justify-content: center;   /* horizontaliai */
    align-items: center;       /* vertikaliai */
    min-height: 100vh;         /* reikia aukščio, kad būtų ką centruoti */
}
```

---

## 2. Header: logo kairėje, meniu dešinėje

```html
<header class="header">
    <a href="#" class="header__logo">Logo</a>
    <nav>
        <ul class="nav__list">
            <li><a href="#">Pradžia</a></li>
            <li><a href="#">Apie</a></li>
            <li><a href="#">Kontaktai</a></li>
        </ul>
    </nav>
</header>
```
```css
.header {
    display: flex;
    justify-content: space-between;  /* logo kairėje, nav dešinėje */
    align-items: center;             /* vertikaliai per vidurį */
    padding: 1rem 2rem;
}

.nav__list {
    display: flex;                   /* meniu punktai į eilutę */
    gap: 1.5rem;
    list-style: none;
}
```

---

## 3. Kortelės – telefone stulpeliu, kompiuteryje eilute (mobile first)

```html
<div class="cards">
    <article class="card">1</article>
    <article class="card">2</article>
    <article class="card">3</article>
</div>
```
```css
.cards {
    display: flex;
    flex-direction: column;     /* telefone – viena po kita */
    gap: 1.5rem;
}

@media (min-width: 48rem) {
    .cards {
        flex-direction: row;    /* didesniame ekrane – eilute */
    }

    .card {
        flex: 1;                /* visos vienodo pločio */
    }
}
```

---

## 4. Kortelės, kurios pačios keliasi į kitą eilutę (be media query)

```css
.cards {
    display: flex;
    flex-wrap: wrap;            /* netelpa – keliasi žemyn */
    gap: 1.5rem;
}

.card {
    flex: 1 1 15rem;            /* grow 1, shrink 1, basis 15rem */
}
```
Kiekviena kortelė bent ~15rem pločio. Kiek telpa – tiek eilutėje.

---

## 5. Footer prilipęs prie apačios (kai turinio mažai)

```css
body {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
}

main {
    flex: 1;                    /* main užima visą likusią vietą, footer nustumiamas žemyn */
}
```

---

## 6. Ikona + tekstas vienoje eilutėje

```html
<p class="contact__item">
    <i class="fa-solid fa-phone"></i>
    <span>+370 600 00000</span>
</p>
```
```css
.contact__item {
    display: flex;
    align-items: center;
    gap: 0.5rem;
}
```

---

## 7. Paveikslėlis šalia teksto (2 stulpeliai)

```html
<section class="about">
    <img src="img/foto.jpg" alt="Aprašymas" class="about__img">
    <div class="about__text">
        <h2>Apie mus</h2>
        <p>Tekstas...</p>
    </div>
</section>
```
```css
.about {
    display: flex;
    flex-direction: column;
    gap: 2rem;
}

@media (min-width: 48rem) {
    .about {
        flex-direction: row;
        align-items: center;
    }

    .about__img,
    .about__text {
        flex: 1;                /* po pusę */
    }
}
```

---

## 8. Mygtukas kortelės apačioje (net jei tekstas skirtingo ilgio)

```css
.card {
    display: flex;
    flex-direction: column;
}

.card__button {
    margin-top: auto;           /* nustumia mygtuką į apačią */
}
```

---

## Dažnos klaidos

| Problema | Priežastis |
|---|---|
| Niekas nesikeičia | `display: flex` uždėtas **vaikui**, o ne **tėvui** |
| `align-items: center` neveikia vertikaliai | Tėvas neturi **aukščio** (`height` / `min-height`) |
| `justify-content` veikia ne ta kryptimi | Yra `flex-direction: column` – ašys apsikeitė |
| Elementai išlenda už ekrano | Trūksta `flex-wrap: wrap` |
| Flex neveikia anūkams | Flex veikia tik **tiesioginiams vaikams** |
