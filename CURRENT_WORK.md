# SimpleCaisse, micro-mission en cours

## Objectif
Outil web mono-fichier de suivi de caisse pour activités associatives : comptage guidé
coupure par coupure, navigation au pavé numérique, suivi des encaissements pendant
l'événement, réconciliation en fin d'événement.

## État
- [x] `index.html` autonome, 312 ko, zéro dépendance réseau : polices (Bricolage
      Grotesque, IBM Plex Sans, IBM Plex Mono, subsets latin woff2 base64) et
      bibliothèque QR (qrcode-generator 1.4.4, MIT) intégrées dans la page.
      Ouvrable par double-clic ou déposable sur n'importe quel serveur statique.
- [x] Accueil : deux entrées, **Simple comptage** (`S`, rien n'est enregistré) et
      **Suivi d'événement** (`E`), puis la liste des événements enregistrés.
- [x] Événement : tableau de bord en trois étapes numérotées, fond de caisse (`F`),
      encaissements (`P`), clôture (`C`). Nom, date et lien de paiement modifiables
      (`M`). `Échap` revient à la liste, y compris depuis un champ de saisie.
- [x] Encaissements : client, quoi, montant, moyen (espèces, carte, chèque,
      HelloAsso, autre). Montant négatif = sortie de caisse. Autocomplétion sur les
      clients et les libellés déjà saisis, ventilation par moyen, suppression ligne
      à ligne.
- [x] Affichette QR (`Q`) vers la page de paiement en ligne (HelloAsso ou autre),
      plein écran et imprimable pour être posée sur la table.
- [x] Comptage : 15 écrans, un par coupure. Billets et pièces dessinés en SVG à
      l'échelle des dimensions réelles (160 × 82 mm pour un 500, 16,25 mm pour un
      centime), avec cannelures, fleur espagnole de la 20 cent et bimétal.
- [x] Clavier : `0-9`, `Entrée` valide et enchaîne, `⌫` corrige, `↑`/`↓` navigue,
      `Échap` ouvre le bilan. Depuis le bilan : `Entrée` valide, `P` encaissements,
      `C` clôture, `R` reprendre. Pavé tactile à l'écran pour tablette.
- [x] Réconciliation : fond d'ouverture + encaissements espèces - sorties = espèces
      attendues, comparées aux espèces comptées, écart qualifié (juste, excédent,
      manquant). En regard : encaissements tous moyens, part hors espèces, dépenses,
      résultat net, montant à déposer en banque.
- [x] Export CSV de l'événement complet (fond de caisse, opérations, clôture,
      réconciliation), séparateur point-virgule et virgule décimale, BOM UTF-8 :
      s'ouvre directement dans un tableur français.
- [x] Stockage `localStorage` (clé `fdc.events.v1`, migration depuis
      `fdc.sessions.v1`), impression avec cases de visa, copie tableur.
- [x] Thèmes clair et sombre, responsive. Aucun glyphe hors subset latin dans
      l'interface (les touches sont écrites en toutes lettres).

## Vérifications faites
Contrôle visuel fait par captures Chromium headless : accueil, tableau de bord,
tableau des encaissements (largeurs de colonnes calibrées sur HelloAsso), écran de
comptage en clair et en sombre, bilan de comptage, réconciliation, affichette QR,
planche des 15 coupures. Contenu du CSV vérifié par extraction du DOM. Syntaxe JS
validée (`node --check`).

## Suite (raffinage)
- Points ouverts : export CSV fichier, plusieurs caisses en parallèle sur un même
  événement, verrouillage d'un événement clôturé, hébergement (GitHub Pages ?).
