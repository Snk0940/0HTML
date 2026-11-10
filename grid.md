# CSS Grid – špargalkė su pavyzdžiais

## Kada grid, o kada flex?

| Flex | Grid |
|---|---|
| **Viena kryptis** – eilutė **arba** stulpelis | **Dvi kryptys** – eilutės **ir** stulpeliai |
| Meniu, header, mygtukų eilė, centravimas | Kortelių tinklelis, galerija, viso puslapio išdėstymas |

## Pagrindas

Grid, kaip ir flex, dedamas **tėvui**.

```html
<div class="grid">
    <div class="grid__item">1</div>
    <div class="grid__item">2</div>
    <div class="grid__item">3</div>
    <div class="grid__item">4</div>
    <div class="grid__item">5</div>
    <div class="grid__item">6</div>
</div>
```

```css
.grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;   /* 3 vienodi stulpeliai */
    gap: 1rem;
}
```
```
[1][2][3]
[4][5][6]
```

### `fr` vienetas
`fr` = **dalis laisvos vietos**.
- `1fr 1fr 1fr` – trys po lygiai
- `2fr 1fr` – pirmas dvigubai platesnis
- `15rem 1fr` – pirmas fiksuotas 15rem, antras – visa likusi vieta

---

## Savybės TĖVUI

| Savybė | Pvz. | Ką daro |
|---|---|---|
| `display` | `grid` | Įjungia grid |
| `grid-template-columns` | `1fr 1fr 1fr` | Stulpeliai ir jų pločiai |
| `grid-template-rows` | `auto 1fr auto` | Eilutės ir jų aukščiai |
| `repeat()` | `repeat(3, 1fr)` | Tas pats kaip `1fr 1fr 1fr` |
| `gap` | `1rem` | Tarpas tarp langelių |
| `row-gap` / `column-gap` | `2rem` | Tarpas tik tarp eilučių / stulpelių |
| `justify-items` | `center` | Turinio lygiavimas langelyje horizontaliai |
| `align-items` | `center` | Turinio lygiavimas langelyje vertikaliai |
| `place-items` | `center` | Abu kartu |
| `grid-template-areas` | žr. 4 pvz. | Išdėstymas pavadinimais |

## Savybės VAIKUI

| Savybė | Pvz. | Ką daro |
|---|---|---|
| `grid-column` | `span 2` | Užima 2 stulpelius |
| `grid-row` | `span 2` | Užima 2 eilutes |
| `grid-column` | `1 / 3` | Nuo 1 iki 3 linijos (= 2 stulpeliai) |
| `grid-column` | `1 / -1` | Per visą plotį |
| `grid-area` | `header` | Pavadinimas `grid-template-areas` |

> Linijos skaičiuojamos **tarp** stulpelių: 3 stulpeliai turi 4 linijas.
> ```
> 1   2   3   4
> | A | B | C |
> ```

---

## 1. Kortelių tinklelis – mobile first

```css
.cards {
    display: grid;
    grid-template-columns: 1fr;            /* telefone – 1 stulpelis */
    gap: 1.5rem;
}

@media (min-width: 48rem) {
    .cards {
        grid-template-columns: repeat(2, 1fr);   /* planšetė – 2 */
    }
}

@media (min-width: 64rem) {
    .cards {
        grid-template-columns: repeat(3, 1fr);   /* kompiuteris – 3 */
    }
}
```

---

## 2. Responsive tinklelis BE media query

```css
.cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(15rem, 1fr));
    gap: 1.5rem;
}
```
- `minmax(15rem, 1fr)` – kortelė **ne siauresnė nei 15rem**, bet gali plėstis.
- `auto-fit` – tiek stulpelių, kiek telpa.

---

## 3. Galerija – viena nuotrauka didesnė

```html
<div class="gallery">
    <img src="img/1.jpg" alt="..." class="gallery__img gallery__img--big">
    <img src="img/2.jpg" alt="..." class="gallery__img">
    <img src="img/3.jpg" alt="..." class="gallery__img">
    <img src="img/4.jpg" alt="..." class="gallery__img">
    <img src="img/5.jpg" alt="..." class="gallery__img">
</div>
```
```css
.gallery {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-auto-rows: 12rem;          /* visų eilučių aukštis */
    gap: 1rem;
}

.gallery__img {
    width: 100%;
    height: 100%;
    object-fit: cover;              /* nuotrauka neištempiama */
}

.gallery__img--big {
    grid-column: span 2;            /* 2 stulpeliai */
    grid-row: span 2;               /* 2 eilutės */
}
```
```
[ BIG  BIG ][2]
[ BIG  BIG ][3]
[4][5]
```

---

## 4. Viso puslapio išdėstymas – grid-template-areas

```html
<body class="page">
    <header class="page__header">Header</header>
    <aside class="page__aside">Šoninė</aside>
    <main class="page__main">Turinys</main>
    <footer class="page__footer">Footer</footer>
</body>
```
```css
.page {
    min-height: 100vh;
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: auto auto 1fr auto;
    grid-template-areas:
        "header"
        "aside"
        "main"
        "footer";                 /* telefone – viskas vienas po kito */
}

.page__header { grid-area: header; }
.page__aside  { grid-area: aside; }
.page__main   { grid-area: main; }
.page__footer { grid-area: footer; }

@media (min-width: 48rem) {
    .page {
        grid-template-columns: 15rem 1fr;
        grid-template-rows: auto 1fr auto;
        grid-template-areas:
            "header header"
            "aside  main"
            "footer footer";
    }
}
```
```
Kompiuteryje:
[      header      ]
[ aside ][  main   ]
[      footer      ]
```

---

## 5. Centruoti elementą (trumpiausias būdas)

```css
.hero {
    display: grid;
    place-items: center;
    min-height: 100vh;
}
```

---

## 6. Elementas per visą plotį

```css
.cards__title {
    grid-column: 1 / -1;     /* nuo pirmos iki paskutinės linijos */
}
```

---

## Dažnos klaidos

| Problema | Priežastis |
|---|---|
| Viskas vienas po kito | Nėra `grid-template-columns` |
| `grid-template-areas` neveikia | Pavadinimai rašomi **be kabučių** `grid-area: header;`, bet **su kabutėmis** areas eilutėse; kiekvienoje eilutėje turi būti **vienodas** stulpelių skaičius |
| Nuotraukos ištemptos | Trūksta `object-fit: cover` |
| Grid neveikia anūkams | Kaip ir flex – tik **tiesioginiams vaikams** |
