# Fly Elite - Plateforme de Réservation de Jets Privés

Site web professionnel de réservation de vols en jet privé, développé avec Next.js 14, TypeScript, Tailwind CSS et Framer Motion.

## 🚀 Fonctionnalités

- **Recherche de vols** avec options Aller Simple / Aller-Retour
- **Offres du Moment** avec prix visibles et réservation directe
- **Système de devis** pour vols personnalisés (sans affichage de prix)
- **300+ aéroports** disponibles
- **Formulaire de contact** avec envoi d'emails
- **FAQ complète** avec sections accordéon
- **Design responsive** et animations professionnelles
- **Emails automatiques** via Nodemailer (confirmation client + notification interne)

## 📦 Installation

```bash
# Installer les dépendances
npm install

# Copier le fichier d'environnement
cp .env.local.example .env.local

# Configurer vos variables d'environnement dans .env.local
```

## ⚙️ Configuration

Éditez le fichier `.env.local` avec vos paramètres SMTP:

```env
SMTP_HOST=smtp.votre-serveur.com
SMTP_PORT=587
SMTP_SECURE=false
SMTP_USER=votre-email@example.com
SMTP_PASS=votre-mot-de-passe

EMAIL_FROM="Fly Elite <no-reply@flyelite.fr>"
EMAIL_TO=contact@flyelite.fr

BRAND_NAME="Fly Elite"
BASE_URL=http://localhost:3000
```

## 🎨 Personnalisation

### Modifier les données

Toutes les données sont centralisées dans le dossier `data/`:

- `data/settings.json` - Configuration générale (marque, couleurs, coordonnées)
- `data/airports.json` - Liste complète des aéroports
- `data/offers.json` - Offres du moment avec prix
- `data/faq.json` - Contenu de la FAQ
- `data/pages/` - Contenu des pages statiques

### Ajouter une offre

Éditez `data/offers.json` et ajoutez:

```json
{
  "id": "unique-id",
  "slug": "porto-manchester-19-nov",
  "date": "2025-11-19",
  "from": "OPO",
  "to": "MAN",
  "aircraft": "Embraer Phenom 300",
  "seats": 6,
  "flightTimeMin": 180,
  "schedule": { "depart": "18:00", "arrive": "20:00" },
  "price": { "currency": "MAD", "amount": 112500 },
  "gallery": ["/assets/images/offers/votre-offre/1.jpg"],
  "featured": true
}
```

### Modifier les couleurs

Éditez `tailwind.config.ts` ou `data/settings.json`:

```json
{
  "colors": {
    "primary": "#0f4068",
    "accent": "#69cce2",
    "light": "#dedede",
    "dark": "#090f10"
  }
}
```

## 🏃 Développement

```bash
# Lancer le serveur de développement
npm run dev
```

Ouvrez [http://localhost:3000](http://localhost:3000) dans votre navigateur.

## 🏗️ Build Production

```bash
# Créer le build de production
npm run build

# Lancer en production
npm start
```

## 📁 Structure du Projet

```
flyelite.fr/
├── app/                    # Pages Next.js (App Router)
│   ├── layout.tsx         # Layout principal
│   ├── page.tsx           # Page d'accueil
│   ├── offres/            # Pages offres
│   ├── notre-concept/     # Page Notre Concept
│   ├── faq/               # Page FAQ
│   ├── contact/           # Page Contact
│   └── api/               # API Routes
│       ├── quote/         # Endpoint devis
│       ├── booking/       # Endpoint réservation
│       └── contact/       # Endpoint contact
├── components/            # Composants réutilisables
│   ├── layout/           # TopBar, Header, Footer
│   ├── search/           # Formulaire de recherche
│   ├── offers/           # Cartes et carousel d'offres
│   └── ui/               # Composants UI génériques
├── data/                 # Données éditables (JSON)
│   ├── settings.json
│   ├── airports.json
│   ├── offers.json
│   ├── faq.json
│   └── pages/
├── lib/                  # Utilitaires et services
│   ├── email.ts         # Service Nodemailer
│   └── utils.ts         # Fonctions utilitaires
├── types/               # Types TypeScript
└── public/              # Assets statiques
    └── assets/
        └── images/
```

## 📧 Système d'Emails

Le site envoie automatiquement des emails via Nodemailer:

1. **Demande de devis** (recherche personnalisée)
   - Email de confirmation au client
   - Notification interne avec tous les détails

2. **Réservation** (Offres du moment)
   - Confirmation de réservation au client
   - Notification interne avec détails + prix

3. **Contact**
   - Accusé de réception au client
   - Notification interne du message

## 🎯 Pages

- `/` - Accueil avec recherche et offres
- `/offres` - Liste des offres du moment
- `/offres/[slug]` - Détail d'une offre
- `/notre-concept` - Présentation du concept
- `/faq` - Questions fréquentes
- `/contact` - Formulaire de contact

## 🔧 Technologies

- **Next.js 14** (App Router)
- **TypeScript**
- **Tailwind CSS**
- **Framer Motion** (animations)
- **Nodemailer** (emails)
- **Lucide React** (icônes)

## 📝 License

Propriétaire - Fly Elite © 2025
# flyelitemorocco.com
