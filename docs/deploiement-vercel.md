# Audit du projet

## Arborescence 

```
CP8_Lanterne/
├── .env        → variables d'environnement, à mettre dans .gitignore
├── .gitignore   → sert à ne pas rendre publique certains fichiers lors du déploiement, .env par exemple
├── package.json   → fichier qui stocke les infos de base du projet (nom, version, ect), les dépendances, et les scripts persos
├── pnpm-lock.yaml  → fichier de verrouillage qui enregistre les versions exactes et les dépendances des paquets installés
├── vercel.json    → configurations vercel
├── README.md    → documentation générale
├── api/    
    ├── index.js    → point d'entrée express, mise en place des sécurité, configurations de base, les routes du serveur 
    └── data/    → dossier contenant le ou les fichiers JSON qui composent les données de l'API
├── docs/    → dossier contenant la documentation nécessaire pour qu’une personne puisse déployer l'application
└── tests    → dossier contenant les fichiers tests, de manière à tester les requêtes disponibles
```

## Dépendances

CORS : version 2.8.5
Express : version 5.1.0

### Node

version : v24.16.0

## Scripts disponibles

Lancer le serveur: 
```bash
node api/index.js
```

Lancer le serveur en dev: 
```bash
node --watch api/index.js
```

Vérifie les fichiers sans les exécuter: 
```bash
node --check api/index.js && node --check tests/api.test.js
```

Lancer les tests: 
```bash
node tests/api.test.js
``` 

## Routes

- `GET /health`
- `GET /curiosities`
- `GET /curiosities?q=canal&limit=5`
- `GET /curiosities/:slug`

## Variables d'environnement

On peut les modifier directement sur Vercel, car elle ne doivent pas être publique.

## Procédure de déploiement
- Création repository GitHub
- Vercel → Add New → Project → trouver notre repo GitHub → import

## La mise à jour et le retour en arrière

Une mise à jour se fait automatiquement lors d'un push sur GitHub.
Pour un retour à une version précedente, sur Vercel : page du projet → deploiement → on choisis la version voulue → promote
