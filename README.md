<div align="center">
  <h1>ANTRENAMENT SAIYAN BAC</h1>

  <p>
    <b>Bac-Saiyan</b> este o aplicație web de tip <b>spaced repetition</b> pentru pregătirea examenului de Bacalaureat la Limba Română — dar nu orice antrenament. Acesta e antrenamentul unui <b>Super Saiyan</b>.
  </p>

  <blockquote>
    <em>"Nivelul meu de putere... este INCREDIBIL de mare."</em><br>
    — Vegeta, după ce a trecut BAC-ul
  </blockquote>
</div>

<hr>
<a href="https://www.vecteezy.com/vector-art/65440803-vegeta-super-saiyan-blue-close-up-anime-illustration">vegeta-super-saiyan-blue-close-up-anime-illustration Vectors by Vecteezy</a>
## Despre proiect

Nu mai memora eseuri la întâmplare.

Aplicația folosește algoritmul **SM-2** (același nucleu folosit de Anki) pentru a-ți prezenta eseurile exact când creierul tău este gata să le uite — maximizând retenția cu efort minim. Fiecare sesiune de studiu este o **luptă**. Fiecare răspuns corect este un **Ki blast**. Fiecare eseu stăpânit este un nou nivel de putere atins.

<br>

## Funcționalități Principale

<table>
  <tr>
    <td><b>Sesiuni de luptă</b></td>
    <td>3 runde per eseu — fiecare rundă testează un aspect diferit al operei literare.</td>
  </tr>
  <tr>
    <td><b>Corectare AI</b></td>
    <td>Răspunsurile tale scrise sunt evaluate de Gemini AI cu feedback instant și detaliat.</td>
  </tr>
  <tr>
    <td><b>Spaced Repetition (SM-2)</b></td>
    <td>Algoritmul calculează exact momentul în care trebuie să revii la un eseu.</td>
  </tr>
  <tr>
    <td><b>Streak zilnic</b></td>
    <td>Menține seria de zile consecutive pentru a-ți crește nivelul de putere.</td>
  </tr>
  <tr>
    <td><b>Dashboard de progres</b></td>
    <td>Vizualizează precis câte opere ai stăpânit din totalul de 30.</td>
  </tr>
  <tr>
    <td><b>Quiz interactiv</b></td>
    <td>Întrebări grilă cu efecte sonore și animații energetice specifice luptelor.</td>
  </tr>
  <tr>
    <td><b>Panel Admin</b></td>
    <td>Adaugă noi opere direct din interfață, asistat de inteligența artificială.</td>
  </tr>
</table>

<br>

## Stack Tehnologic

<div align="center">
  <img src="https://img.shields.io/badge/Next.js_14-000000?style=for-the-badge&logo=next.js&logoColor=white" alt="Next.js" />
  <img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" alt="Tailwind CSS" />
  <img src="https://img.shields.io/badge/Neon_DB-00E599?style=for-the-badge&logo=postgresql&logoColor=black" alt="Neon Database" />
  <img src="https://img.shields.io/badge/Google_Gemini-8E75B2?style=for-the-badge&logo=google&logoColor=white" alt="Google Gemini" />
</div>

<br>

## Rulare locală

### 1. Clonare repository

```bash
git clone https://github.com/CiobanicaCrenguta/AntrenamentBacSaiyan.git
cd AntrenamentBacSaiyan/bac-saiyan
```

### 2. Instalare dependențe

```bash
npm install
```

### 3. Configurare variabile de mediu

Creează un fișier `.env` în rădăcina aplicației (lângă `package.json`):

```env
DATABASE_URL=postgresql://...       # Conexiunea la Neon DB
GEMINI_API_KEY=...                  # Cheia API Google Gemini
```

### 4. Inițializare bază de date

Rulează schema SQL în consola Neon sau folosind `psql`:

```bash
psql $DATABASE_URL -f schema.sql
```

### 5. Pornire antrenament

```bash
npm run dev
```

Deschide `http://localhost:3000` în browser și începe antrenamentul.

## Structura proiectului

```text
src/
├── app/
│   ├── dashboard/        [ Dashboard principal cu toate operele ]
│   ├── session/[id]/     [ Sesiune de antrenament per eseu (3 runde) ]
│   ├── admin/            [ Panou admin pentru adăugare opere ]
│   └── api/
│       └── grade/        [ API route pentru corectare AI ]
├── components/
│   ├── EssayCard.tsx     [ Cardul unei opere: status, autor, titlu ]
│   ├── ProgressBar.tsx   [ Bara de progres globală ]
│   └── SaiyanQuiz.tsx    [ Componenta de quiz interactiv ]
└── lib/
    └── actions.ts        [ Server actions: DB queries, SM-2 logic ]
```

## Algoritmul SM-2

Fiecare eseu primește un **factor de ușurință** și un **interval de repetare** care se ajustează dinamic în funcție de performanța ta în luptă:

- **[ Scor 3 ] Stăpânit** — Intervalul de repetiție crește exponențial.
- **[ Scor 2 ] Parțial** — Intervalul rămâne același; necesită consolidare.
- **[ Scor 1 ] Ratat** — Intervalul este resetat la o zi; necesită reînvățare imediată.

**Traseul evoluției:** `unseen` → `due` → `learning` → `mastered`
