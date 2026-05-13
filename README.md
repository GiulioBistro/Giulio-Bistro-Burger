# Giulio Bistro & Burger — Website

Statische Webseite für [giuliobistro.de](https://www.giuliobistro.de) — gehostet kostenlos über **GitHub Pages**.

---

## 🚀 Deployment in 5 Minuten

### 1. Repository anlegen
1. Auf [github.com](https://github.com) einloggen
2. Oben rechts auf **+** → **New repository**
3. Name z.B. `giuliobistro-web` (egal welcher Name)
4. **Public** auswählen (für kostenloses Pages-Hosting)
5. Auf **Create repository** klicken

### 2. Dateien hochladen
1. Im neuen Repo auf **uploading an existing file** klicken
2. `index.html` und `CNAME` reinziehen
3. Unten auf **Commit changes**

### 3. GitHub Pages aktivieren
1. Im Repo auf **Settings** (oben rechts)
2. Links auf **Pages**
3. Unter "Build and deployment":
   - **Source:** `Deploy from a branch`
   - **Branch:** `main` → `/ (root)` → **Save**
4. Bei "Custom domain" prüfen, dass `www.giuliobistro.de` schon eingetragen ist (kommt aus der CNAME-Datei)
5. Häkchen bei **Enforce HTTPS** setzen (kann ein paar Minuten dauern, bis verfügbar)

---

## 🌐 Domain umziehen (Wix → GitHub Pages)

> ⚠️ **Wichtig:** Erst die DNS-Einträge ändern, **dann** Wix kündigen. Sonst ist die Seite kurz offline.

### Wo liegt die Domain aktuell?

Falls die Domain bei Wix **registriert** ist, am besten erst zu einem normalen Registrar transferieren (z.B. INWX, Namecheap, Cloudflare). Falls sie schon bei einem anderen Provider liegt (IONOS, Strato, etc.) und Wix nur die DNS-Einträge verwaltet, einfach die DNS-Records ändern.

### DNS-Einträge setzen

Beim DNS-Provider folgende **A-Records** für `giuliobistro.de` setzen (zeigen auf GitHub Pages):

```
@   A   185.199.108.153
@   A   185.199.109.153
@   A   185.199.110.153
@   A   185.199.111.153
```

Und einen **CNAME-Record** für `www`:

```
www   CNAME   DEIN-USERNAME.github.io
```

(`DEIN-USERNAME` durch deinen GitHub-Usernamen ersetzen)

### ⚠️ Google Workspace Email NICHT anfassen!

Die **MX-Records** für die E-Mails dürfen **nicht gelöscht** werden! Die bleiben so wie sie sind. MX-Records sind unabhängig von den A/CNAME-Records für die Website.

Die Google-Workspace MX-Records sehen typischerweise so aus (zur Kontrolle):

```
@   MX   1    SMTP.GOOGLE.COM
```

Diese Einträge unverändert lassen — dann läuft `kontakt@giuliobistro.de` weiter normal.

---

## ✏️ Inhalte anpassen

Alles in einer Datei: `index.html`. Einfach mit einem Editor öffnen (VS Code empfohlen) und Text ändern.

**Bilder:** Aktuell aus Unsplash geladen — einfach `<img src="...">` auf eigene Bilder umstellen. Ordner `images/` im Repo anlegen und z.B. `images/burger.jpg` referenzieren.

**Speisekarte-PDF:** Der Link zeigt aktuell noch auf die Wix-PDF. Das PDF runterladen, ins Repo legen (z.B. `speisekarte.pdf`) und den Link im HTML auf `/speisekarte.pdf` ändern.

---

## 🔧 Lokal testen

Einfach `index.html` per Doppelklick im Browser öffnen — fertig. Oder mit einem kleinen Server:

```bash
# Mit Python
python3 -m http.server 8000

# Oder mit Node
npx serve
```

Dann im Browser: `http://localhost:8000`

---

## 💸 Was kostet das?

- **GitHub Pages Hosting:** 0 € (für öffentliche Repos und unter 100 GB Traffic/Monat — also de facto immer kostenlos)
- **Domain:** ~10-15 €/Jahr beim Registrar (Wix nimmt da gerne mehr)
- **Google Workspace:** läuft wie bisher

**Vorher (Wix):** ~15-25 € pro Monat
**Nachher:** ~1 € pro Monat (nur die Domain)
