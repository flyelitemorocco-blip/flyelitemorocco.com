# Guide d'Installation - Fly Elite

## 📋 Prérequis

- Node.js 18+ installé
- npm ou yarn
- Un compte SMTP pour l'envoi d'emails

## 🚀 Installation Rapide

### 1. Installer les dépendances

```bash
npm install
```

Cette commande installera tous les packages nécessaires :
- Next.js 14
- TypeScript
- Tailwind CSS
- Framer Motion
- Nodemailer
- Lucide React (icônes)

### 2. Configurer les variables d'environnement

Copiez le fichier d'exemple et configurez vos paramètres :

```bash
cp .env.local.example .env.local
```

Éditez `.env.local` avec vos informations SMTP :

```env
# Configuration SMTP
SMTP_HOST=smtp.votre-serveur.com
SMTP_PORT=587
SMTP_SECURE=false
SMTP_USER=votre-email@example.com
SMTP_PASS=votre-mot-de-passe

# Configuration Email
EMAIL_FROM="Fly Elite <no-reply@flyelite.fr>"
EMAIL_TO=flyelite.morocco@gmail.com

# Configuration Marque
BRAND_NAME="Fly Elite"
BASE_URL=http://localhost:3000
```

### 3. Ajouter vos assets

Placez vos images dans le dossier `public/assets/images/` :

```
public/
└── assets/
    └── images/
        ├── logo.svg (votre logo Fly Elite)
        ├── hero.jpg (image du slider)
        └── offers/
            ├── porto-manchester/
            │   ├── 1.jpg
            │   ├── 2.jpg
            │   └── 3.jpg
            └── ...
```

### 4. Lancer le serveur de développement

```bash
npm run dev
```

Ouvrez [http://localhost:3000](http://localhost:3000) dans votre navigateur.

## 📝 Configuration des Données

Toutes les données sont éditables dans le dossier `data/` :

### Paramètres Généraux (`data/settings.json`)

```json
{
  "brand": {
    "name": "Fly Elite",
    "logo": "/assets/images/logo.svg"
  },
  "colors": {
    "primary": "#0f4068",
    "accent": "#69cce2",
    "light": "#dedede",
    "dark": "#090f10",
    "white": "#ffffff"
  },
  "topBar": {
    "enabled": true,
    "bg": "#0f4068",
    "text": "Devise : MAD — Une question ? ..."
  },
  "contact": {
    "phones": ["+212 689 33 02 02", "+33 744 96 62 68"],
    "email": "flyelite.morocco@gmail.com",
    "address": "66, Av de France et 37, Av Ibn Sina...",
    "social": {
      "instagram": "https://instagram.com/flyelite",
      "facebook": "https://facebook.com/flyelite",
      "twitter": "https://twitter.com/flyelite",
      "linkedin": "https://linkedin.com/company/flyelite"
    },
    "mapEmbedUrl": "https://www.google.com/maps/embed?..."
  }
}
```

### Aéroports (`data/airports.json`)

Le fichier contient déjà 316 aéroports. Format :

```json
[
  {
    "id": "AAL",
    "name": "Aalborg",
    "city": "Aalborg",
    "country": "",
    "code": "AAL",
    "slug": "aalborg-aal"
  }
]
```

### Offres (`data/offers.json`)

Ajoutez ou modifiez les offres du moment :

```json
[
  {
    "id": "porto-manchester-2025-11-19",
    "slug": "porto-manchester-19-nov",
    "date": "2025-11-19",
    "from": "OPO",
    "to": "MAN",
    "aircraft": "Embraer Phenom 300",
    "seats": 6,
    "flightTimeMin": 180,
    "schedule": {
      "depart": "18:00",
      "arrive": "20:00"
    },
    "price": {
      "currency": "MAD",
      "amount": 112500
    },
    "gallery": [
      "/assets/images/offers/porto-manchester/1.jpg"
    ],
    "featured": true
  }
]
```

## 🎨 Personnalisation

### Modifier les couleurs

Éditez `tailwind.config.ts` :

```typescript
colors: {
  primary: '#0f4068',
  accent: '#69cce2',
  light: '#dedede',
  dark: '#090f10',
},
```

### Ajouter une nouvelle offre

1. Ajoutez les images dans `public/assets/images/offers/nom-offre/`
2. Ajoutez l'offre dans `data/offers.json`
3. Le site se mettra à jour automatiquement

## 📧 Test des Emails

Pour tester l'envoi d'emails en développement, vous pouvez utiliser :

- **Mailtrap** (recommandé pour le dev) : https://mailtrap.io
- **Gmail SMTP** (pour la production)
- **SendGrid**, **Mailgun**, etc.

Configuration Mailtrap (dev) :
```env
SMTP_HOST=smtp.mailtrap.io
SMTP_PORT=2525
SMTP_USER=votre-username-mailtrap
SMTP_PASS=votre-password-mailtrap
```

## 🏗️ Build Production

```bash
# Créer le build
npm run build

# Lancer en production
npm start
```

## 📁 Structure Complète

```
flyelite.fr/
├── app/                    # Pages Next.js
│   ├── layout.tsx         # Layout principal
│   ├── page.tsx           # Homepage
│   ├── globals.css        # Styles globaux
│   ├── offres/            # Pages offres
│   ├── notre-concept/     # Page Notre Concept
│   ├── faq/               # Page FAQ
│   ├── contact/           # Page Contact
│   └── api/               # API Routes
│       ├── quote/         # Endpoint devis
│       ├── booking/       # Endpoint réservation
│       └── contact/       # Endpoint contact
├── components/            # Composants React
│   ├── layout/           # TopBar, Header, Footer
│   ├── home/             # Composants homepage
│   ├── search/           # Formulaire recherche
│   ├── offers/           # Cartes offres
│   └── ui/               # Composants UI
├── data/                 # Données JSON
│   ├── settings.json
│   ├── airports.json
│   ├── offers.json
│   └── faq.json
├── lib/                  # Utilitaires
│   ├── email.ts         # Service Nodemailer
│   └── utils.ts         # Fonctions utilitaires
├── types/               # Types TypeScript
│   └── index.ts
├── public/              # Assets statiques
│   └── assets/
│       └── images/
├── scripts/             # Scripts utilitaires
│   └── generate-airports.js
├── package.json
├── tsconfig.json
├── tailwind.config.ts
├── next.config.js
└── README.md
```

## ✅ Checklist de Déploiement

Avant de déployer en production :

- [ ] Configurer les variables d'environnement de production
- [ ] Ajouter toutes les images des offres
- [ ] Tester l'envoi d'emails
- [ ] Vérifier les liens sociaux
- [ ] Mettre à jour l'URL de la carte Google Maps
- [ ] Compléter le contenu FAQ
- [ ] Tester le formulaire de recherche
- [ ] Tester le formulaire de contact
- [ ] Vérifier la responsive sur mobile
- [ ] Optimiser les images (compression)
- [ ] Configurer le domaine personnalisé

## 🆘 Support

Pour toute question ou problème :

1. Vérifiez que toutes les dépendances sont installées
2. Vérifiez les variables d'environnement
3. Consultez les logs dans la console
4. Vérifiez que les chemins des images sont corrects

## 🚀 Prochaines Étapes

1. **Installer les dépendances** : `npm install`
2. **Configurer `.env.local`** avec vos paramètres SMTP
3. **Ajouter vos images** dans `public/assets/images/`
4. **Lancer le dev** : `npm run dev`
5. **Personnaliser** les données dans `data/`
6. **Tester** les formulaires et emails
7. **Builder** pour production : `npm run build`

Bon développement ! 🎉
