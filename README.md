# Carnet de cuisine

Petit site statique publié avec GitHub Pages. Il affiche les recettes de `recipes.json`, avec quantités ajustables, cases à cocher, minuteurs et lecture hors connexion.

Ce dépôt est indépendant du site principal `jourdainatlas.github.io`.

## Ajouter ou modifier une recette

Toutes les recettes sont dans `recipes.json`, un tableau d'objets :

| Champ | Rôle |
|---|---|
| `id` | identifiant unique, en minuscules avec des tirets (sert dans l'adresse `#r-<id>`) |
| `title`, `description`, `category` | titre, résumé, catégorie (les catégories deviennent des filtres) |
| `order` | position dans la liste |
| `base_servings` | nombre de personnes pour lequel les quantités sont écrites |
| `total_minutes` | durée totale indicative |
| `added_at` | date ISO facultative ; une recette ajoutée depuis moins de 7 jours porte la pastille « Nouveau » |
| `ingredients` | `{ id, name, amount, unit?, fixed? }` ; unités : `g`, `kg`, `ml`, `l`, `tsp`, `tbsp`, `pinch` ; `fixed: true` empêche le recalcul selon les portions (huile de friture, œufs de panure) |
| `steps` | `{ id, title, content, timer_seconds? }` ; `{0001}` dans `content` insère la quantité recalculée de l'ingrédient `0001` |
| `notes` | astuces, paragraphes séparés par une ligne vide |

Après un push sur `main`, GitHub Pages republie le site en une minute environ.

## Fichiers

- `index.html` : l'application
- `recipes.json` : les recettes
- `sw.js` : copie hors connexion (réseau d'abord, copie locale en secours)
- `manifest.webmanifest`, `icons/` : nom et icône sur l'écran d'accueil
