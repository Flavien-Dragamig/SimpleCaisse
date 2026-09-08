# SimpleCaisse, micro-mission en cours

## Objectif
Outil web mono-fichier de suivi de caisse pour activités associatives : comptage guidé
coupure par coupure, navigation au pavé numérique, ouverture/clôture d'événement,
calcul automatique du CA en espèces.

## État
- [x] `index.html` autonome (zéro dépendance externe, polices comprises : fonctionne hors ligne, en local
      par double-clic ou hébergé sur n'importe quel serveur statique).
- [x] Écran accueil : nom d'activité, date, mode Ouverture (`O`) / Clôture (`C`).
- [x] Comptage : 15 écrans (7 billets, 8 pièces), un par coupure, visuel aux couleurs
      réelles du billet ou de la pièce, sous-total et total courant en direct.
- [x] Clavier : `0-9` saisie, `Entrée` valide et passe à la coupure suivante,
      `⌫` corrige, `↑`/`↓` navigue, `Échap` bascule au récapitulatif.
      Pavé tactile à l'écran pour tablette.
- [x] Récapitulatif : tableaux billets/pièces, sous-totaux, total.
      En clôture : fond de caisse de l'ouverture correspondante (retrouvée par nom
      d'activité), CA en espèces = total clôture - fond, saisie du CA attendu et
      calcul de l'écart de caisse.
- [x] Enregistrement `localStorage`, historique cliquable, copie tableur, impression
      avec cases de visa (comptée par / vérifiée par).
- [x] Thèmes clair et sombre, responsive, exemple de caisse affiché tant qu'aucune
      donnée réelle n'existe.

## Suite (raffinage)
- Vérifier le rendu réel dans le navigateur (aucune capture n'a été prise).
- Points ouverts à trancher : export CSV/fichier, plusieurs caisses en parallèle sur
  un même événement, décompte des tickets vendus, mot de passe ou verrou d'édition,
  hébergement (GitHub Pages ? kDrive ?).
