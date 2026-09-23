## requêtes exécutées sur l’URL publique

https://lanterne-api.vercel.app/curiosities/fontaine-des-reflets
{
  "data": {
    "slug": "fontaine-des-reflets",
    "title": "La fontaine des reflets",
    "city": "Tours",
    "category": "eau",
    "description": "Une fontaine basse qui transforme les façades voisines en paysage mouvant."
  }
}
code HTTP : 200

https://lanterne-api.vercel.app/curiosities?q=canal&limit=5
{
  "data": [
    {
      "slug": "passage-bleu",
      "title": "Le passage bleu",
      "city": "Nantes",
      "category": "architecture",
      "description": "Une galerie discrète au bord du canal, reconnaissable à ses carreaux bleus."
    }
  ],
  "meta": {
    "count": 1,
    "limit": 5,
    "query": "canal",
    "category": ""
  }
}
code HTTP : 200

https://lanterne-api.vercel.app/health
{
  "status": "ok",
  "environment": "development",
  "version": "1.0.0"
}
code HTTP : 200

https://lanterne-api.vercel.app/curiosities
{
  "data": [
    {
      "slug": "passage-bleu",
      "title": "Le passage bleu",
      "city": "Nantes",
      "category": "architecture",
      "description": "Une galerie discrète au bord du canal, reconnaissable à ses carreaux bleus."
    },
    {
      "slug": "jardin-des-brumes",
      "title": "Le jardin des brumes",
      "city": "Nantes",
      "category": "nature",
      "description": "Un jardin partagé où les aromatiques sont entretenues avant l’ouverture des bureaux."
    },
    {
      "slug": "lettres-de-la-halle",
      "title": "Les lettres de la halle",
      "city": "Rennes",
      "category": "mémoire",
      "description": "Une ancienne halle dont les poutres portent encore les initiales des premiers artisans."
    },
    {
      "slug": "escalier-des-oiseaux",
      "title": "L’escalier des oiseaux",
      "city": "Angers",
      "category": "détail",
      "description": "Une rampe en pierre décorée de petits oiseaux que l’on ne voit qu’en descendant."
    },
    {
      "slug": "fontaine-des-reflets",
      "title": "La fontaine des reflets",
      "city": "Tours",
      "category": "eau",
      "description": "Une fontaine basse qui transforme les façades voisines en paysage mouvant."
    },
    {
      "slug": "cabane-des-cartographes",
      "title": "La cabane des cartographes",
      "city": "La Rochelle",
      "category": "mémoire",
      "description": "Une ancienne remise de quai devenue un repère pour les promeneurs curieux."
    }
  ],
  "meta": {
    "count": 6,
    "limit": 20,
    "query": "",
    "category": ""
  }
}
code HTTP : 200

https://lanterne-api.vercel.app/grfed
{
  "error": "Route not found"
}
code HTTP : 404

https://lanterne-api.vercel.app/curiosities/tyguhjk
{
  "error": "Curiosity not found"
}
code HTTP : 404


## Scripts

Les scripts sont documentés dans deploiement-vercel.md, ou simplement dans package.json. Ils fonctionnent correctement. 
Les 2 premiers lancent le serveur, et on obtient "Lanterne API listening on port 3000"
le 3e check si il y a des erreurs
le 4e renvoi bien "API tests passed", ce qui affirme la validité des tests.