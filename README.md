# KraftInk Market

Catalogue public des plugins, thèmes et modules de jeu disponibles pour KraftInk. Les fiches et les versions proviennent des releases GitHub des dépôts inscrits.

La configuration `resources.json` est maintenue sur `dev`. Sa liste `repositories` contient des entrées comme :

```json
{ "repository": "Kraftink-CMS/Plugin-Example", "auto_update": true }
```

L’option `auto_update` contrôle les mises à jour automatiques de l’offre. Une valeur `false` conserve sa fiche et ses versions publiées. La liste `resources` contient les offres manuelles.

Le [catalogue public au format JSON](https://raw.githubusercontent.com/Kraftink-CMS/Market/master/catalogue.json) est publié sur `master` et utilisé par le CMS et le site KraftInk.

Le workflow central [Refresh Market](https://github.com/Kraftink-CMS/automation/actions/workflows/refresh-market.yml) s’exécute sur `master` avec trois portées manuelles :

| Portée | Actualisation |
| --- | --- |
| `automatic` | Dépôts avec `auto_update: true` |
| `repository` | Dépôt inscrit indiqué dans le champ `repository`, pauses incluses |
| `all` | Tous les dépôts inscrits, pauses incluses |

Les modes `repository` et `all` actualisent les offres sans modifier `auto_update`.
