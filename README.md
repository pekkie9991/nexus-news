# NEXUS // Terminale Notizie Mondiale

> Aggregatore RSS client-side con mappa interattiva mondiale. Zero server, zero database — funziona interamente nel browser.

![preview](https://img.shields.io/badge/NEXUS-v5.0-00d4ff?style=flat-square&logo=rss&logoColor=white)
![license](https://img.shields.io/badge/license-MIT-00ff9d?style=flat-square)

## 🚀 Deploy su GitHub Pages (passo a passo)

### 1. Crea il repository

```bash
git init
git add .
git commit -m "chore: init NEXUS news terminal"
```

### 2. Crea un repository su GitHub

Vai su [github.com/new](https://github.com/new) e crea un repo **pubblico** chiamato `nexus-news` (o come preferisci).

### 3. Push

```bash
git remote add origin https://github.com/TUO-USERNAME/nexus-news.git
git branch -M main
git push -u origin main
```

### 4. Abilita GitHub Pages

1. Vai su **Settings → Pages**
2. Source: **Deploy from a branch**
3. Branch: `main` / `/ (root)`
4. Salva — il sito sarà live a `https://TUO-USERNAME.github.io/nexus-news/`

---

## 💰 Configurazione Google AdSense

### Requisiti
- Sito approvato da Google (contenuto originale, traffico reale)
- Account AdSense attivo su [adsense.google.com](https://adsense.google.com)

### Passi

1. **Registra il sito** su AdSense e ottieni il tuo **Publisher ID** (`ca-pub-XXXXXXXXXXXXXXXX`)
2. Apri `index.html` e sostituisci **tutte le occorrenze** di `ca-pub-XXXXXXXXXX` con il tuo ID
3. Crea due **Ad Unit** in AdSense:
   - **Banner orizzontale** (tipo: Display, formato responsivo) → copia lo slot ID in `data-ad-slot="0000000001"`
   - **Sidebar verticale** (tipo: Display, 160×600) → copia lo slot ID in `data-ad-slot="0000000002"`
4. Fai commit e push → Google inizierà a servire inserzioni dopo 24-48h

```html
<!-- In <head> — sostituisci il publisher ID -->
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-TUO-ID" crossorigin="anonymous"></script>

<!-- In ogni tag <ins> -->
data-ad-client="ca-pub-TUO-ID"
data-ad-slot="TUO-SLOT-ID"
```

> **Nota bene:** Non cliccare sulle tue stesse inserzioni — viola le policy AdSense e rischi la sospensione dell'account.

---

## 🗞 Fonti (14)

| Fonte | Regione | Lingua |
|-------|---------|--------|
| ANSA | Italia | IT |
| Repubblica | Italia | IT |
| Corriere della Sera | Italia | IT |
| Rai News | Italia | IT |
| BBC World | Europa / Mondiale | EN |
| Deutsche Welle | Europa | EN |
| Le Monde | Europa | FR |
| El Pais | Europa | ES |
| UN News | Global | EN |
| NPR | Americhe | EN |
| Al Jazeera | Medio Oriente | EN |
| WHO | Global | EN |
| r/WorldNews | Social | EN |
| Africanews | Africa | EN |

## ⚙️ Architettura

- **Zero dipendenze** — nessun framework JS, nessun bundler
- **CORS proxies** — 4 proxy in cascata per aggirare le restrizioni CORS sugli RSS
- **Canvas API** — mappa mondiale disegnata nativamente, con TopolJSON decode integrato
- **DOMParser** — parsing RSS/Atom nativo del browser
- Aggiornamento automatico ogni **120 secondi**
