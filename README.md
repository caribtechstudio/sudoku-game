# The Caribbean Sudoku — site (`sudoku-game` repo)

Ce dossier est la **source unique** du site public de l'app, prêt à publier
sur GitHub Pages à `https://caribtechstudio.github.io/sudoku-game/`.

## Pages

| Fichier | URL publiée | Rôle |
|---|---|---|
| `index.html` | `/sudoku-game/` | Page d'accueil bilingue (EN/FR, bascule JS) : modes, captures d'écran réelles, fonctionnalités, tarifs |
| `privacy.en.html` / `privacy.fr.html` | `/sudoku-game/privacy.{en,fr}.html` | Politique de confidentialité — **URL à coller dans App Store Connect** |
| `terms.en.html` / `terms.fr.html` | `/sudoku-game/terms.{en,fr}.html` | Conditions d'utilisation |
| `support.en.html` / `support.fr.html` | `/sudoku-game/support.{en,fr}.html` | FAQ + contact — **URL à coller dans « URL de l'assistance »** |
| `privacy.html`, `terms.html`, `support.html` | — | Redirections automatiques vers la version `.en.html` (compatibilité avec l'ancienne fiche App Store) |

Toutes les pages reprennent la palette exacte de l'app (`Sudoku/DesignSystem/Theme.swift`,
thèmes Papier/Encre) et s'adaptent au mode clair/sombre du navigateur.

## Ce que ça remplace

- L'ancien contenu du repo `sudoku-game` (design daté, tarif obsolète
  « 3,99 € sans pub » — l'app est maintenant gratuite avec pubs + Premium).
- Le contenu qui vivait dans le repo racine `caribtechstudio.github.io`
  (page vitrine minimale). Ce repo racine garde uniquement `app-ads.txt`
  (obligatoire à la racine du domaine pour AdMob) et une page d'accueil qui
  renvoie ici — voir `../site/README.md`.

## Publication

```bash
cd site-sudoku-game
git init
git add .
git commit -m "Refonte du site : contenu à jour, captures réelles, pages légales"
git branch -M main
git remote add origin https://github.com/caribtechstudio/sudoku-game.git
git push -u origin main --force
```

`--force` écrase l'historique existant du repo `sudoku-game` — normal ici
puisqu'on remplace tout son contenu. Si tu préfères garder l'historique,
clone d'abord le repo existant, supprime son contenu, copie celui-ci
par-dessus, puis commit/push normalement.

Repo → **Settings** → **Pages** → Source : **Deploy from a branch** →
branche `main`, dossier `/ (root)`.

## À mettre à jour dans App Store Connect

Une fois en ligne (~2 min après le push) :

| Champ | Nouvelle valeur |
|---|---|
| URL de la politique de confidentialité | `https://caribtechstudio.github.io/sudoku-game/privacy.en.html` |
| URL de l'assistance | `https://caribtechstudio.github.io/sudoku-game/support.en.html` |
| URL marketing (site web du développeur) | `https://caribtechstudio.github.io` *(inchangé — doit rester la racine du domaine pour la vérification `app-ads.txt` par AdMob)* |

## Lien avec l'app

Les URLs `.../sudoku-game/...` sont désormais codées en dur dans l'app —
voir `Sudoku/Features/Settings/SettingsView.swift` et
`Sudoku/Features/Store/StoreView.swift`. Elles ne prendront effet pour les
utilisateurs de la version **déjà publiée** qu'après la sortie de la
prochaine mise à jour (les anciens liens `.../sudoku/...` restent
fonctionnels entre-temps grâce aux redirections placées dans le repo
racine, voir `../site/README.md`).
