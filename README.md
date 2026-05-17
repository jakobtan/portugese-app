# 🇵🇹 Português · Dagliga Ord

En PWA (Progressive Web App) som automatiskt genererar 10 nya portugisiska ord per tema varje dag med Claude AI. Lägg till den på hemskärmen – den fungerar precis som en vanlig app.

---

## ⚡ Snabbstart (ca 20 minuter)

### 1. Skapa GitHub-konto
Om du inte redan har ett: [github.com/signup](https://github.com/signup)

### 2. Skapa ett nytt repo
- Gå till [github.com/new](https://github.com/new)
- Namnge det t.ex. `portugues-app`
- Välj **Public** (krävs för gratis GitHub Pages)
- Klicka **Create repository**

### 3. Ladda upp filerna
Ladda upp alla filer i denna mapp till repot. Strukturen ska se ut så här:

```
portugues-app/
├── .github/
│   └── workflows/
│       └── daily-words.yml
├── public/
│   ├── index.html
│   ├── sw.js
│   ├── manifest.json
│   └── words/
│       └── today.json
└── _config.yml
```

### 4. Skaffa Claude API-nyckel
- Gå till [console.anthropic.com](https://console.anthropic.com)
- Skapa ett konto och generera en API-nyckel under **API Keys**
- Det kostar ungefär **$0.01–0.02 per dag** (extremt billigt)

### 5. Lägg till API-nyckeln i GitHub
- Gå till ditt repo → **Settings** → **Secrets and variables** → **Actions**
- Klicka **New repository secret**
- Namn: `ANTHROPIC_API_KEY`
- Värde: din API-nyckel
- Klicka **Add secret**

### 6. Aktivera GitHub Pages
- Gå till **Settings** → **Pages**
- Under **Source**: välj **GitHub Actions**
- Spara

### 7. Kör första gången manuellt
- Gå till **Actions** → **Generate Daily Words** → **Run workflow**
- Vänta ca 30 sekunder
- Orden genereras och sparas automatiskt

### 8. Din app är live!
Din app finns nu på:
```
https://DITT-ANVÄNDARNAMN.github.io/portugues-app/
```

---

## 📱 Lägg till på hemskärmen

**iPhone/iPad (Safari):**
1. Öppna appen i Safari
2. Tryck på dela-knappen (rutan med pilen upp)
3. Välj **Lägg till på hemskärmen**
4. Tryck **Lägg till**

**Android (Chrome):**
1. Öppna appen i Chrome
2. Tryck på menyn (tre punkter)
3. Välj **Lägg till på startskärmen**

---

## 🔄 Hur det fungerar

Varje natt klockan 05:00 svensk tid:
1. GitHub Actions kör automatiskt
2. Claude API anropas och genererar 5 teman × 10 ord
3. Orden sparas i `public/words/today.json`
4. Nästa gång du öppnar appen hämtas dagens ord

Om du saknar uppkoppling visas gårdagens ord (cachade offline).

---

## 🛠 Anpassa

**Byta klocktid för uppdatering:** Ändra `cron`-värdet i `.github/workflows/daily-words.yml`.
- `0 3 * * *` = 03:00 UTC = 05:00 svensk tid
- `0 5 * * *` = 05:00 UTC = 07:00 svensk tid

**Byta språk:** Ändra prompten i `daily-words.yml` – byt ut "Portuguese" och "Swedish" mot valfria språk.

**Lägga till ikoner:** Ersätt `icon-192.png` och `icon-512.png` i `public/` med egna bilder (valfritt – appen fungerar utan dem).
