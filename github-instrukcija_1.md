# Git + GitHub atsiskaitymui (svetimas kompiuteris)

## 1. Prisijungti prie GitHub

1. Naršyklė **incognito** lange: **`Ctrl + Shift + N`**
2. [github.com](https://github.com) → **Sign in**
3. „Išsaugoti slaptažodį?“ → **Never**

---

## 2. Sukonfigūruoti Git

Atidaryk **Git Bash** arba VS Code → **Terminal** → **New Terminal**.

```
git config --global user.name "Tavo Vardas"
git config --global user.email "tavo@github.pastas"
```

---

## 3. Paimti savo šablonus (jei reikia)

```
cd Desktop
git clone https://github.com/TAVO-VARDAS/html-css-pagalba.git
```
Nuoroda: GitHub'e žalias mygtukas **Code** → nukopijuok.

---

## 4. Naujas projektas ir išsiuntimas į GitHub

**GitHub'e:** **+** → **New repository** → pavadinimas → **be README** → **Create repository** → nukopijuok nuorodą (`https://github.com/.../....git`).

**Terminale, projekto aplanke** (VS Code: **File** → **Open Folder** → tada **Terminal**):

```
git init
git add .
git commit -m "Pirmas commit"
git branch -M main
git remote add origin https://github.com/TAVO-VARDAS/REPO.git
git push -u origin main
```

| Komanda | Ką daro |
|---|---|
| `git init` | Sukuria naują vietinę Git repozitoriją |
| `git add .` | Įtraukia visus pakeitimus į staging |
| `git commit -m "..."` | Sukuria commit (įrašą) |
| `git branch -M main` | Pervadina šaką į `main` |
| `git remote add origin URL` | Prijungia GitHub repozitoriją vardu `origin` |
| `git push -u origin main` | Išsiunčia į GitHub (pirmą kartą) |

**Pirmo push metu** iššoks langas → **Sign in with your browser** → **Authorize** → grįžk į terminalą.

Patikrink GitHub'e (atnaujink puslapį) – failai turi būti ten.

---

## 5. Kasdienis darbas (po kiekvieno pakeitimo)

```
git status
git add .
git commit -m "Ką pakeičiau"
git push
```

| Komanda | Ką daro |
|---|---|
| `git status` | Parodo, kas pasikeitė |
| `git add index.html` | Įtraukia tik vieną failą |
| `git log --oneline` | Trumpa commit istorija |
| `git pull` | Atsisiunčia pakeitimus iš GitHub |

**Atšaukimas:**

| Komanda | Ką daro |
|---|---|
| `git restore failas.html` | Atšaukia failo pakeitimus (dar nepadarius `add`) |
| `git restore --staged failas.html` | Išima failą iš staging (pakeitimai faile lieka) |

---

## 6. Pabaigoje – išvalyti savo duomenis

**1. Ištrinti Git vardą ir el. paštą**
```
git config --global --unset user.name
git config --global --unset user.email
```

**2. Ištrinti išsaugotą prisijungimą**
- Windows paieška → **Credential Manager** → **Windows Credentials**
- **`git:https://github.com`** → **Remove**

**3. VS Code**
- Kairėje apačioje **žmogeliuko ikonėlė** → jei matai savo GitHub → **Sign Out**
- **File** → **Close Folder**

**4. GitHub naršyklėje**
- Avataras → **Sign out**
- Uždaryk **visus** incognito langus

**5. Failai**
- Ištrink projekto aplanką (jei nereikia palikti dėstytojui)
- Ištuštink **Šiukšlinę**

---

## Patikrinimas

- [ ] Darbas matosi GitHub'e
- [ ] `git config --global --list` – nėra mano vardo
- [ ] Credential Manager – nėra `git:https://github.com`
- [ ] GitHub – Sign out
- [ ] Incognito langai uždaryti
- [ ] Aplankas ištrintas

> Jei pamiršai atsijungti – savo telefone: GitHub → **Settings** → **Sessions** → **Revoke**, ir **Applications** → **Authorized OAuth Apps** → **Git Credential Manager** → **Revoke**.

---

## Dažnos klaidos

| Klaida | Ką daryti |
|---|---|
| `Please tell me who you are` | Nepadarei 2 žingsnio (`git config`) |
| `not a git repository` | Esi ne tame aplanke – atsidaryk projekto aplanką |
| `src refspec main does not match any` | Dar nėra commit – pirma `git add .` ir `git commit` |
| `remote origin already exists` | `git remote set-url origin URL` |
| `rejected ... fetch first` | GitHub'e sukūrei su README – `git pull origin main --allow-unrelated-histories`, tada `git push` |
| `nothing to commit` | Neišsaugojai failo (`Ctrl + S`) |
