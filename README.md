# KraftInk Market

Catalogue public des plugins, thèmes et modules de jeu disponibles pour KraftInk. Les fiches et les versions proviennent des releases GitHub des dépôts inscrits.

Les noms, descriptions et images facultatives viennent de `manifest.market`. Un texte brut reste une chaîne, tandis qu’un champ traduit conserve toutes ses langues réellement disponibles. Les images du dossier `resources/market/` de l’extension sont déclarées par nom ou chemin relatif dans son manifeste, puis résolues en URL GitHub liée au tag de la version. Le catalogue contient une URL HTTPS ou un dictionnaire d’URL par langue. Le site KraftInk et le CMS utilisent directement ces fiches, avec un repli vers l’anglais puis la première langue disponible lorsqu’une traduction manque.

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
