# Audit du projet

# Procédure de déploiement

## 1 Prérequis

- Node.js 24 LTS
- pnpm 11
- compte et repo GitHub
- compte vercel
- dossier projet configuré comme répertoire racine du projet Vercel
fichier .nvmrc fixe node.js 24 pour éviter environnement implicite.

## 2 installation locale

```text
pnpm install
pnpm run check
pnpm test
```
résulats attendus : 
```text
node --check api/index.js && node --check tests/api.test.js
API tests passed
```

## 3 déploiement vercel

depuis la racine du projet :
 ```
vercel link
create new project
nom du projet
connect this git... : y
code directory : default (entrée)
customize settings? : n
 ```

On configure les variables d'environnement sur Vercel. menu `environment variables` → `add envorinment variables` → `config`
ajouter les clés qui sont dans .env.example et configurer la variable d'environnement en fonction de l'environnement

ensuite déployer avec `vercel`, ça permet de déployer la version en production

### 3.1 déployer la version de dev

- créer une branche develop `git checkout -b develop` 
- déployer `vercel`
- configurer les variables d'environnement pour la version preview

## 4 mise à jour 

Pour publier une nouvelle version : 
passer sur la branche develop
`git switch develop`
mettre à jour le projet
mettre à jour les tests si le comportement change
lancer npm run check et npm test
créer un commit explicite
déployer la preview : `vercel`
vérifier les routes
publier en production 


### 4.1 Publier en production

fusionner develop avec main
lancer `vercel --prod`

## 5 retour arrière

en cas d'echec, sélctionner le déploiement précedent dans l'historique Vercel et le promouvoir en production



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

## La mise à jour et le retour en arrière

Une mise à jour se fait automatiquement lors d'un push sur GitHub.
Pour un retour à une version précedente, sur Vercel : page du projet → deploiement → on choisis la version voulue → promote
