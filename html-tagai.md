# HTML žymės (tagai) – špargalkė

## Turinys
1. [Puslapio skeletas](#1-puslapio-skeletas)
2. [head dalies žymės](#2-head-dalies-žymės)
3. [Semantinė struktūra](#3-semantinė-struktūra)
4. [Tekstas](#4-tekstas)
5. [Sąrašai](#5-sąrašai)
6. [Nuorodos ir keliai](#6-nuorodos-ir-keliai)
7. [Paveikslėliai ir medija](#7-paveikslėliai-ir-medija)
8. [Lentelės](#8-lentelės)
9. [Formos](#9-formos)
10. [Bendros (be prasmės) žymės](#10-bendros-be-prasmės-žymės)
11. [Svarbūs atributai](#11-svarbūs-atributai)
12. [Block ir inline](#12-block-ir-inline)

---

## 1. Puslapio skeletas

```html
<!DOCTYPE html>
<html lang="lt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Puslapio pavadinimas</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <!-- Viskas, kas matoma puslapyje -->
</body>
</html>
```

| Žymė | Kam naudojama |
|---|---|
| `<!DOCTYPE html>` | Pasako naršyklei, kad tai HTML5 dokumentas. Visada pirma eilutė. |
| `<html lang="lt">` | Viso puslapio „konteineris“. `lang` – puslapio kalba. |
| `<head>` | Informacija apie puslapį (nematoma puslapyje): pavadinimas, CSS, šriftai. |
| `<body>` | Visas matomas puslapio turinys. Tik **vienas** `body` puslapyje. |
| `<!-- ... -->` | Komentaras. Naršyklė jo nerodo, skirtas programuotojui. |

---

## 2. head dalies žymės

| Žymė | Kam naudojama |
|---|---|
| `<meta charset="UTF-8">` | Kad lietuviškos raidės (ą, č, ę...) rodytųsi teisingai. |
| `<meta name="viewport" content="width=device-width, initial-scale=1.0">` | Būtina responsive dizainui – telefone puslapis neatrodys „sumažintas“. Be jos neveiks media queries telefone. |
| `<title>` | Tekstas naršyklės skirtuke (tab). |
| `<link rel="stylesheet" href="...">` | Prijungia CSS failą. Taip pat naudojama Google Fonts prijungti. |
| `<style>` | CSS rašomas tiesiai HTML faile (geriau naudoti atskirą failą). |
| `<script src="...">` | Prijungia JavaScript failą (pvz. ikonų bibliotekai). |

Google Fonts pavyzdys:
```html
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
```

---

## 3. Semantinė struktūra

Semantinės žymės pasako, **kokia tai puslapio dalis**. Vizualiai jos kaip `div`, bet geriau naršyklėms, Google ir ekrano skaitytuvams.

| Žymė | Kam naudojama |
|---|---|
| `<header>` | Puslapio (ar skyriaus) viršus: logotipas, pavadinimas, meniu. |
| `<nav>` | Navigacijos meniu (nuorodų grupė). |
| `<main>` | Pagrindinis puslapio turinys. Tik **vienas** puslapyje. |
| `<section>` | Teminė puslapio dalis (pvz. „Paslaugos“, „Kontaktai“). Dažniausiai turi antraštę. |
| `<article>` | Savarankiškas turinys, kurį galima atskirai perskaityti (straipsnis, įrašas, kortelė). |
| `<aside>` | Šoninis, papildomas turinys (šoninė juosta, reklama). |
| `<footer>` | Puslapio apačia: kontaktai, autorių teisės, nuorodos. |

```html
<body>
    <header>
        <nav>...</nav>
    </header>
    <main>
        <section>...</section>
        <section>...</section>
    </main>
    <footer>...</footer>
</body>
```

---

## 4. Tekstas

| Žymė | Kam naudojama |
|---|---|
| `<h1>` ... `<h6>` | Antraštės. `h1` – svarbiausia (dažniausiai viena puslapyje), `h6` – mažiausia. Nešokinėti lygių (po `h1` eina `h2`, ne `h4`). |
| `<p>` | Pastraipa (teksto blokas). |
| `<br>` | Eilutės laužimas (nauja eilutė pastraipos viduje). Neturi uždaromosios žymės. |
| `<hr>` | Horizontali linija – temos pasikeitimas. Neturi uždaromosios žymės. |
| `<strong>` | Svarbus tekstas (rodomas **paryškintas**). |
| `<b>` | Paryškintas tekstas be ypatingos svarbos. |
| `<em>` | Pabrėžtas tekstas (rodomas *pasviręs*). |
| `<i>` | Pasviręs tekstas. Dažnai naudojamas **ikonoms** (Font Awesome). |
| `<span>` | Inline „dėžutė“ teksto daliai pažymėti, kad galėtum ją stilizuoti. |
| `<small>` | Smulkus tekstas (pvz. © autorių teisės). |
| `<blockquote>` | Ilgesnė citata. |
| `<q>` | Trumpa citata eilutėje (prideda kabutes). |
| `<code>` | Kodo fragmentas. |
| `<sup>` / `<sub>` | Viršutinis indeksas (m²) / apatinis indeksas (H₂O). |

```html
<h1>Mano svetainė</h1>
<p>Čia yra <strong>svarbus</strong> tekstas ir <span class="spalvotas">pažymėta dalis</span>.</p>
<hr>
<p>Pirma eilutė<br>Antra eilutė</p>
```

---

## 5. Sąrašai

| Žymė | Kam naudojama |
|---|---|
| `<ul>` | Nenumeruotas sąrašas (su taškais). Dažnai naudojamas **meniu**. |
| `<ol>` | Numeruotas sąrašas (1, 2, 3...). |
| `<li>` | Sąrašo elementas. Būna **tik** `ul` arba `ol` viduje. |
| `<dl>`, `<dt>`, `<dd>` | Aprašų sąrašas: `dt` – terminas, `dd` – jo paaiškinimas. |

Įdėtas (nested) sąrašas – naujas `ul`/`ol` dedamas **į `li` vidų**:
```html
<ol>
    <li>Vaisiai
        <ul>
            <li>Obuolys</li>
            <li>Kriaušė</li>
        </ul>
    </li>
    <li>Daržovės</li>
</ol>
```

Naudingi `ol` atributai: `start="5"` (pradėti nuo 5), `reversed` (atbulai), `type="A"` (raidės).

Meniu pavyzdys:
```html
<nav>
    <ul>
        <li><a href="index.html">Pradžia</a></li>
        <li><a href="apie.html">Apie</a></li>
    </ul>
</nav>
```

---

## 6. Nuorodos ir keliai

| Žymė / atributas | Kam naudojama |
|---|---|
| `<a href="...">` | Nuoroda. `href` – kur ji veda. |
| `target="_blank"` | Atidaro nuorodą naujame skirtuke. |
| `href="#kontaktai"` | Nuoroda į elementą tame pačiame puslapyje su `id="kontaktai"`. |
| `href="mailto:vardas@pastas.lt"` | Atidaro el. pašto programą. |
| `href="tel:+37060000000"` | Telefono numeris (paspaudus telefone – skambina). |

```html
<a href="https://google.com" target="_blank">Google</a>
<a href="apie.html">Apie mus</a>
```

### Keliai (paths)

Tarkim, failų struktūra:
```
projektas/
├── index.html
├── css/
│   └── style.css
├── img/
│   └── foto.jpg
└── puslapiai/
    └── apie.html
```

| Iš kur | Į ką | Kelias |
|---|---|---|
| `index.html` | `style.css` | `css/style.css` |
| `index.html` | `foto.jpg` | `img/foto.jpg` |
| `index.html` | `apie.html` | `puslapiai/apie.html` |
| `apie.html` | `index.html` | `../index.html` |
| `apie.html` | `foto.jpg` | `../img/foto.jpg` |
| `style.css` | `foto.jpg` (background) | `../img/foto.jpg` |

- `aplankas/failas` – eik **į** aplanką.
- `../` – išeik **vienu aplanku aukštyn**.
- Keliai CSS faile skaičiuojami **nuo CSS failo vietos**, ne nuo HTML.

---

## 7. Paveikslėliai ir medija

| Žymė | Kam naudojama |
|---|---|
| `<img src="..." alt="...">` | Paveikslėlis. `src` – kelias, `alt` – aprašymas (rodomas, jei nuotrauka neužsikrauna, ir skaitomas ekrano skaitytuvų). **`alt` privalomas.** Neturi uždaromosios žymės. |
| `<figure>` | Paveikslėlio (ar diagramos) „konteineris“ kartu su prierašu. |
| `<figcaption>` | Prierašas po paveikslėliu `figure` viduje. |
| `<video src="..." controls>` | Video. `controls` – rodo valdymo mygtukus. |
| `<audio src="..." controls>` | Garso įrašas. |
| `<iframe src="...">` | Kito puslapio įdėjimas (pvz. YouTube video, Google žemėlapis). |

```html
<figure>
    <img src="img/kate.jpg" alt="Ruda katė miega ant sofos">
    <figcaption>Mano katė</figcaption>
</figure>
```

---

## 8. Lentelės

| Žymė | Kam naudojama |
|---|---|
| `<table>` | Visa lentelė. |
| `<caption>` | Lentelės pavadinimas (iškart po `<table>`). |
| `<thead>` | Lentelės antraštės dalis. |
| `<tbody>` | Lentelės duomenų dalis. |
| `<tfoot>` | Lentelės apačia (pvz. „Iš viso“). |
| `<tr>` | Eilutė (table row). |
| `<th>` | Antraštės langelis (paryškintas, centruotas). |
| `<td>` | Paprastas duomenų langelis. |
| `colspan="2"` | Langelis užima 2 **stulpelius** (į plotį). |
| `rowspan="2"` | Langelis užima 2 **eilutes** (į aukštį). |

```html
<table>
    <caption>Pažymiai</caption>
    <thead>
        <tr>
            <th>Vardas</th>
            <th>Pažymys</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Jonas</td>
            <td>9</td>
        </tr>
        <tr>
            <td colspan="2">Daugiau duomenų nėra</td>
        </tr>
    </tbody>
</table>
```

Naudingas CSS lentelėms: `border-collapse: collapse;` (sujungia dvigubus rėmelius į vieną).

---

## 9. Formos

| Žymė | Kam naudojama |
|---|---|
| `<form action="..." method="...">` | Visa forma. `action` – kur siųsti duomenis, `method` – `get` arba `post`. |
| `<label for="vardas">` | Laukelio pavadinimas. `for` turi sutapti su laukelio `id` – paspaudus ant teksto, aktyvuojamas laukelis. |
| `<input>` | Įvesties laukelis. Tipas nurodomas `type` atributu (žr. lentelę žemiau). Neturi uždaromosios žymės. |
| `<textarea>` | Didelis teksto laukas (žinutei). `rows`, `cols` – dydis. |
| `<select>` | Išskleidžiamas sąrašas. |
| `<option value="...">` | Pasirinkimas `select` viduje. |
| `<button type="submit">` | Mygtukas. `submit` – siunčia formą, `reset` – išvalo, `button` – nieko nedaro (JS). |
| `<fieldset>` | Grupuoja susijusius laukelius (nupiešia rėmelį). |
| `<legend>` | Grupės pavadinimas `fieldset` viduje. |

### input tipai

| `type` | Kas tai |
|---|---|
| `text` | Paprastas tekstas. |
| `email` | El. paštas (tikrina, ar yra @). |
| `password` | Slaptažodis (rodo taškelius). |
| `number` | Tik skaičiai (galima `min`, `max`, `step`). |
| `tel` | Telefono numeris. |
| `date` | Data (kalendorius). |
| `checkbox` | Varnelė – galima pažymėti **kelias**. |
| `radio` | Apskritimas – galima pasirinkti **tik vieną** iš grupės (visi grupės `radio` turi **tą patį `name`**). |
| `range` | Slankiklis. |
| `color` | Spalvos pasirinkimas. |
| `file` | Failo įkėlimas. |
| `submit` | Siuntimo mygtukas. |

### Formos atributai

| Atributas | Kam |
|---|---|
| `name` | Laukelio vardas – su juo siunčiami duomenys. Radio grupei – bendras. |
| `id` | Unikalus vardas – sujungia su `label for`. |
| `value` | Reikšmė (ypač svarbu `radio`, `checkbox`, `option`). |
| `placeholder` | Pilkas pavyzdinis tekstas laukelyje. |
| `required` | Privalomas laukelis. |
| `min` / `max` | Mažiausia / didžiausia skaičiaus reikšmė. |
| `minlength` / `maxlength` | Mažiausias / didžiausias simbolių kiekis. |
| `pattern` | Taisyklė (regex), kokį tekstą galima įvesti. |
| `checked` | `radio`/`checkbox` pažymėtas iš anksto. |
| `selected` | `option` pasirinktas iš anksto. |
| `disabled` | Laukelis neaktyvus. |

```html
<form action="#" method="post">
    <label for="vardas">Vardas</label>
    <input type="text" id="vardas" name="vardas" placeholder="Jonas" required>

    <label for="pastas">El. paštas</label>
    <input type="email" id="pastas" name="pastas" required>

    <fieldset>
        <legend>Lytis</legend>
        <input type="radio" id="vyras" name="lytis" value="vyras">
        <label for="vyras">Vyras</label>
        <input type="radio" id="moteris" name="lytis" value="moteris">
        <label for="moteris">Moteris</label>
    </fieldset>

    <label for="miestas">Miestas</label>
    <select id="miestas" name="miestas">
        <option value="vilnius">Vilnius</option>
        <option value="kaunas">Kaunas</option>
    </select>

    <label for="zinute">Žinutė</label>
    <textarea id="zinute" name="zinute" rows="4"></textarea>

    <button type="submit">Siųsti</button>
</form>
```

---

## 10. Bendros (be prasmės) žymės

| Žymė | Kam naudojama |
|---|---|
| `<div>` | **Block** „dėžutė“ elementams grupuoti ir stilizuoti (pvz. `.container`, kortelės, flex tėvas). Naudoti, kai netinka jokia semantinė žymė. |
| `<span>` | **Inline** „dėžutė“ teksto daliai stilizuoti. |

```html
<div class="container">
    <div class="korta">...</div>
    <div class="korta">...</div>
</div>
```

---

## 11. Svarbūs atributai

| Atributas | Kam |
|---|---|
| `class="..."` | Klasė CSS stilizavimui. Gali kartotis, vienas elementas gali turėti kelias: `class="korta korta--aktyvi"`. **Stilizuoti naudoti klases.** |
| `id="..."` | Unikalus vardas (tik vienas puslapyje). Naudoti `label for` ir `href="#..."` nuorodoms, **ne stilizavimui**. |
| `href` | Kur veda nuoroda / kur yra CSS failas. |
| `src` | Kur yra paveikslėlis / video / skriptas. |
| `alt` | Paveikslėlio aprašymas. |
| `title` | Tekstas, rodomas užvedus pelę. |
| `lang` | Kalba. |
| `style="..."` | CSS tiesiai elemente (vengti). |

---

## 12. Block ir inline

**Block** – užima visą plotį, prasideda iš naujos eilutės, galima keisti `width`/`height`:
`div`, `p`, `h1–h6`, `ul`, `ol`, `li`, `header`, `nav`, `main`, `section`, `article`, `footer`, `form`, `table`, `hr`, `figure`, `fieldset`

**Inline** – užima tik tiek vietos, kiek turinys, stovi eilutėje, `width`/`height` neveikia:
`a`, `span`, `strong`, `em`, `b`, `i`, `label`, `small`, `code`, `br`

**Inline-block** – stovi eilutėje, bet galima keisti dydį:
`img`, `input`, `button`, `select`, `textarea`

Pakeisti galima CSS: `display: block;`, `display: inline;`, `display: inline-block;`, `display: none;`, `display: flex;`

---

## Žymės be uždaromosios dalies (void)

`<br>`, `<hr>`, `<img>`, `<input>`, `<meta>`, `<link>`

Visos kitos žymės **turi būti uždarytos**: `<p>...</p>`, `<div>...</div>`.
