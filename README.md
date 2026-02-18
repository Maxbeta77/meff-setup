# MEFF Setup Page

Pagina di setup per connettere dispositivi mobili a MEFF Remote Scanner via Tailscale.

## 🚀 Deploy su GitHub Pages

### Opzione 1: Deploy Manuale

1. Crea un nuovo repository su GitHub (es: `meff-setup`)
2. Carica il file `index.html` nel repository
3. Vai su **Settings** → **Pages**
4. Seleziona **Source: Deploy from a branch**
5. Seleziona **Branch: main** e **Folder: / (root)**
6. Clicca **Save**
7. La pagina sarà disponibile su: `https://TUOUSERNAME.github.io/meff-setup/`

### Opzione 2: GitHub CLI (se hai gh installato)

```bash
# Crea il repository
gh repo create meff-setup --public

# Carica il file
git init
git add index.html
git commit -m "Initial commit - MEFF Setup Page"
git branch -M main
git remote add origin https://github.com/TUOUSERNAME/meff-setup.git
git push -u origin main

# Abilita GitHub Pages
gh repo edit --enable-pages --branch main
```

## ⚙️ Configurazione MEFF

Dopo il deploy, aggiungi l'URL al file `.env` del backend MEFF:

```env
SETUP_PAGE_URL=https://TUOUSERNAME.github.io/meff-setup
```

Riavvia il backend:
```bash
sudo supervisorctl restart backend
```

## 📱 Come Funziona

1. L'operatore MEFF genera un QR code dalla pagina Remote Scanner
2. Il QR code contiene: `https://TUOUSERNAME.github.io/meff-setup?key=AUTH_KEY`
3. Il cliente scansiona il QR con la fotocamera del telefono
4. La pagina guida il cliente in 3 passi:
   - **Passo 1:** Installa Tailscale (App Store / Play Store)
   - **Passo 2:** Copia la chiave di autenticazione (già nel link!)
   - **Passo 3:** Incolla la chiave in Tailscale e connettiti

## 🔒 Sicurezza

- L'auth key è inclusa nel link ma è **usa e getta** (single-use)
- Una volta usata, la chiave non può essere riutilizzata
- La comunicazione avviene su HTTPS

## 🎨 Personalizzazione

Puoi modificare il file `index.html` per:
- Cambiare colori e logo
- Aggiungere il nome della tua azienda
- Modificare le istruzioni
- Aggiungere traduzioni

---

**MEFF M3 Pro** - Mobile Forensics Scanner
