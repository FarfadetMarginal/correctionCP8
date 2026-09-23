## rapport de validation

| vérification | requete | résultat attendus |
| --- | --- | --- |
| santé du sercice | GET .../api/health | HTTP 200 et JSON avec status OK |
| liste | GET .../curiosities | HTTP 200 et tableau 'data |
| recherche | GET .../curiosities?q=recherche | HTTP 200 et objet 'data |
| ressource absente | GET .../curiosities/inconnu | HTTP 404 et réponse json |
| route absente | GET .../curfds| HTTP 404 et réponse json |

## contexte local supplementaire

```text
npm run check
npm test
```

# preuves acceptables

- screenshots
- sorties de commandes
- dates, URL, version de l'API testée
