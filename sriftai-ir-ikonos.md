# Google Fonts ir Font Awesome ikonos

## Google Fonts

1. Eik į [fonts.google.com](https://fonts.google.com).
2. Susirask šriftą (pvz. **Roboto**, **Poppins**, **Montserrat**, **Open Sans**).
3. **Get font** → **Get embed code**.
4. Pasirink reikalingus storius (pvz. 400 ir 700).
5. Nukopijuok `<link>` eilutes ir įklijuok į **`<head>`**, **PRIEŠ** savo `style.css`:

```html
<head>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap" rel="stylesheet">

    <link rel="stylesheet" href="css/style.css">
</head>
```

6. CSS – nustatyk `body`, visi vaikai paveldės:
```css
body {
    font-family: "Poppins", sans-serif;   /* sans-serif – atsarginis */
}

h1, h2 {
    font-weight: 700;
}
```

**Du šriftai** (pvz. antraštėms kitas):
```html
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&family=Playfair+Display:wght@700&display=swap" rel="stylesheet">
```
```css
body { font-family: "Poppins", sans-serif; }
h1, h2, h3 { font-family: "Playfair Display", serif; }
```

> Šriftas neveikia? Patikrink: ar pavadinimas CSS **tiksliai** toks pat kaip Google (su tarpais ir didžiosiomis), ar yra kabutės, ar `<link>` yra `<head>`.

---

## Font Awesome ikonos

### Prijungimas (CDN)

Į **`<head>`**:
```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">
```

> Nuorodą galima rasti: [cdnjs.com/libraries/font-awesome](https://cdnjs.com/libraries/font-awesome) → nukopijuok `all.min.css` nuorodą.

### Naudojimas

1. Eik į [fontawesome.com/icons](https://fontawesome.com/icons).
2. Pasirink filtrą **Free**.
3. Susirask ikoną → nukopijuok kodą.

```html
<i class="fa-solid fa-phone"></i>
<i class="fa-solid fa-envelope"></i>
<i class="fa-solid fa-location-dot"></i>
<i class="fa-solid fa-bars"></i>            <!-- hamburger meniu -->
<i class="fa-solid fa-cart-shopping"></i>
<i class="fa-solid fa-star"></i>
<i class="fa-brands fa-facebook"></i>
<i class="fa-brands fa-instagram"></i>
<i class="fa-brands fa-linkedin"></i>
<i class="fa-brands fa-github"></i>
```

| Klasė | Kas |
|---|---|
| `fa-solid` | Pilnos ikonos |
| `fa-regular` | Tuščiavidurės (tik kai kurios nemokamos) |
| `fa-brands` | Prekių ženklai (Facebook, Instagram...) |

### Stilizavimas

Ikona – tai **tekstas**, todėl keičiama kaip tekstas:
```css
.footer__icon {
    font-size: 1.5rem;      /* dydis */
    color: #ffffff;         /* spalva */
}

.footer__icon:hover {
    color: #61a5c2;
}
```

### Socialinių tinklų nuorodos

```html
<ul class="social">
    <li><a href="https://facebook.com" target="_blank" class="social__link"><i class="fa-brands fa-facebook"></i></a></li>
    <li><a href="https://instagram.com" target="_blank" class="social__link"><i class="fa-brands fa-instagram"></i></a></li>
</ul>
```
```css
.social {
    display: flex;
    gap: 1rem;
    list-style: none;
}

.social__link {
    font-size: 1.5rem;
    color: inherit;
}
```

### Ikona + tekstas

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

> Ikona nesimato (rodomas kvadratas arba nieko)? Patikrink: ar `<link>` yra `<head>`, ar ikona yra **Free**, ar teisinga klasė (`fa-solid` / `fa-brands`).
