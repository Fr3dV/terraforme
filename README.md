# Terraforme

Jeu de terraformation en 3D, jouable dans le navigateur. Site : https://tf.gamzu.fr

Tout le jeu tient dans `index.html`. Le moteur 3D (three.js r128) est embarqué dans `vendor/`, il n'y a donc aucune dépendance externe à part les polices Google Fonts (le jeu fonctionne aussi sans elles).

## Mise en ligne avec GitHub Pages

1. Crée un dépôt GitHub (par exemple `terraforme`) et pousse le contenu de ce dossier à la racine de la branche `main` :
   ```
   git init
   git add .
   git commit -m "Terraforme : première version"
   git branch -M main
   git remote add origin https://github.com/<ton-compte>/terraforme.git
   git push -u origin main
   ```
2. Dans le dépôt : Settings > Pages > Source « Deploy from a branch », branche `main`, dossier `/ (root)`.
3. Le fichier `CNAME` déclare déjà le domaine `tf.gamzu.fr` ; vérifie qu'il apparaît dans Settings > Pages > Custom domain.
4. Dans la zone DNS de `gamzu.fr`, ajoute :
   ```
   tf    CNAME    <ton-compte>.github.io.
   ```
5. Une fois le DNS propagé (de quelques minutes à quelques heures), coche « Enforce HTTPS » dans Settings > Pages.

## Tester en local

Lance un serveur statique dans ce dossier (`python3 -m http.server 8000`), puis ouvre http://localhost:8000.

## Notes

- La sauvegarde est stockée dans le navigateur du joueur (localStorage, clé `terraforme-v3`) : elle ne suit pas d'un appareil à l'autre.
- Classement : l'indice de terraformation est envoyé au classement partagé de gamzu.fr (script `https://gamzu.fr/scores.js`) à chaque nouvelle étape et toutes les 5 minutes de jeu, si le joueur a choisi un pseudo. Le top 10 s'affiche dans le menu. Sans connexion, le jeu fonctionne normalement.
- Sur un vrai domaine, la capture de la souris fonctionne normalement : clic sur Jouer, Échap pour la pause.
- Licence de three.js : `vendor/THREE-LICENSE.txt` (MIT).
