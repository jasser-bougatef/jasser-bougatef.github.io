# Portfolio — Jasser Bougatef (version finale)

Site d'une page, bilingue FR/EN, sans framework : tout est dans `index.html`.
Ouvre simplement `index.html` dans un navigateur pour le voir.

## Structure

```
index.html              ← le site (contenu + config en haut du <script>)
assets/photo.jpg        ← photo de profil
assets/cv/              ← CV en PDF (bouton « Télécharger mon CV »)
assets/media/           ← photos, captures CAO et vidéo de démo RL (compressée 720p, 8,5 Mo)
assets/docs/            ← rapports PDF liés depuis les projets (bin-picking, RL, Venom)
assets/logos/, assets/schools/ ← (optionnel) logos des outils / écoles
```

## Le fond animé

Dessiné en canvas, inspiré de la mécatronique :
- **pistes de PCB** avec des impulsions de signal qui circulent ;
- **engrenages** qui s'entraînent en bas à gauche (ils tournent aussi au scroll) ;
- **bras robotisé 3 axes** qui suit la souris par **cinématique inverse** (au repos, il trace une courbe de Lissajous) avec repères de liaisons et angles θ1/θ2/θ3 ;
- **clic** dans le vide = onde de scan LiDAR ;
- petit **HUD** en bas à gauche (position et angles du bras).

Respecte « réduire les animations » du système (image fixe) et se met en pause quand l'onglet est caché.

## Modifier le contenu

Tout est dans le `<script>` : `CONFIG` (liens, email, CV), puis `PROJ`, `JOBS`, `EDU`, `LEAD`, `SK`.

- **GitHub** : remplis `CONFIG.github` → le bouton apparaît partout. Pour chaque projet, remplis l'`url` du lien « Code (GitHub) » (vide = masqué).
- **Médias** : `{ type:"img", src:"assets/media/x.jpg", cap:{fr:"…",en:"…"}, fit:"contain" }`
  - `fit:"contain"` pour les schémas/CAO (pas de recadrage), `fit:"tall"` pour les photos en portrait.
  - Vidéo : `{ type:"video", src:"…mp4", poster:"…jpg" }` ; YouTube : `{ type:"youtube", id:"…" }`.
- **Logos des compétences** : table `LOGO` dans le script. Valeur = un fichier de `assets/logos/` (ex. `"python.svg"`) ou une icône dessinée (`"i:pid"`, `"i:bus"`… voir `ICO`). Compétence absente de la table = monogramme.
  Sources : logos de marques de [Simple Icons](https://simpleicons.org) (CC0) ; ROS, Gazebo, PCL, MATLAB de Wikimedia Commons ; SolidWorks / CATIA / 3DEXPERIENCE / Abaqus affichent le logo Dassault Systèmes (l'éditeur).
- **Logos des entreprises** : `assets/companies/` (aluk, ims, dwee, leoni) — champ `logo` de chaque expérience dans `JOBS`.
- **Logos des écoles** : `assets/schools/sigma-logo.png`, `eniso-logo.png`, `ipeis-logo.png` (remplace le fichier pour changer de logo).
- **CV anglais** : ajoute le fichier dans `assets/cv/` et renseigne `CONFIG.cv.en`.

## À compléter quand tu peux

- Photos AluK / IMS (banc, robot viticole) si l'entreprise/labo l'autorise → `media` de chaque expérience.
- Lien GitHub.

## Mettre en ligne avec GitHub Pages (gratuit)

1. Crée un dépôt nommé **`ton-pseudo.github.io`** (public).
2. Upload le contenu de ce dossier à la racine du dépôt.
3. Settings → Pages → *Deploy from a branch*, branche `main`, dossier `/ (root)`.
4. Le site est en ligne sur `https://ton-pseudo.github.io` après une minute.
