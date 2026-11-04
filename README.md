# Morpion — Deux joueurs sur le même écran

Jeu réalisé avec Codex pour les exercices de création et de publication du morpion. Le jeu entier tient dans `index.html`, sans serveur ni ressource externe. Ouvrir ce fichier par double-clic pour jouer localement.

## Règles

Grille 3 × 3. X commence, puis X et O alternent. Une case occupée ne modifie ni la grille ni le tour. Trois symboles alignés en ligne, colonne ou diagonale donnent la victoire. Une grille pleine sans vainqueur donne un match nul. Après la fin, aucun coup supplémentaire n’est accepté. « Nouvelle partie » vide la grille et redonne la main à X.

## Vérifications

Les cinq séquences de l’annexe sont conservées dans `tests/logic.cjs` et `tests/browser.cjs` : case occupée, victoire de X, blocage après la fin, redémarrage et match nul. Les tests vérifient aussi les huit alignements et une victoire de O.

- `npm test` : exécution du script avec un DOM simulé ; les cinq séquences exactes réussissent.
- `npm run test:browser` : vérification dans Chromium des commandes visibles, des cinq séquences, du clavier et d’une largeur mobile de 375 px. Son exécution locale reste à faire : Chromium n’est pas disponible dans cet environnement. Le workflow GitHub l’exécutera avant publication.

Pour relancer les tests navigateur :

```sh
npm install --no-save --package-lock=false playwright@1.62.1
npx playwright install chromium
npm run test:browser
```

Une fois le site publié, le même script peut vérifier l’URL en ligne :

```sh
MORPION_URL=https://dycms.github.io/morpion/ npm run test:browser
```

## Publication

Dépôt prévu : https://github.com/DYCMS/morpion

Adresse prévue après activation et déploiement : https://dycms.github.io/morpion/

Dans le dépôt, choisir **Settings → Pages → Source → GitHub Actions**. Le workflow `.github/workflows/pages.yml` vérifie le jeu et publie uniquement `index.html`. L’ouverture du site publié et une partie sur cette URL restent à confirmer après le déploiement.

## Fichiers envoyés

Le projet contient le jeu, le README, les tests, la configuration de publication et un `.gitignore`. Aucun compte utilisateur, mot de passe, clé API, donnée personnelle ou conversation n’est nécessaire au fonctionnement et aucun n’est inclus dans ces fichiers. Le projet ne charge aucune ressource externe pendant une partie. Les dépendances de tests sont utilisées uniquement pour la vérification.
