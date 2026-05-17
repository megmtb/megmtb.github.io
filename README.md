# Meg M.T.B. — Site vitrine

Site one-page de **Meg M.T.B.**, partenaire opérationnelle pour studios de jeux vidéo indépendants.

## Stack

- HTML / CSS / JS pur, tout inline dans `index.html`
- Pas de build, pas de dépendance à installer
- Bilingue FR / EN (toggle FR/EN dans le header, persisté en `localStorage`)
- Responsive (desktop / tablette / mobile)
- Système de gamification : XP par action, quest log, lift de la carte recommandée

## Structure

```
.
├── index.html       # Tout le site (HTML + CSS + JS inline)
├── 404.html         # Page d'erreur custom
├── favicon.svg      # Favicon (flamme orange)
├── robots.txt       # Indexation
├── .nojekyll        # Empêche GitHub Pages de passer par Jekyll
├── Icons/           # Logos clients (Capital Game, NTWU, Institut français, CAPCOM, Old Skull, Warning Up, Gamevestor) + autres assets
└── README.md
```

## Dev local

Aucune commande nécessaire. Soit ouvrir `index.html` dans un navigateur (les images se chargeront), soit servir avec un serveur statique :

```bash
# Python
python3 -m http.server 8000

# Node
npx serve

# Puis http://localhost:8000
```

## Déploiement sur GitHub Pages

1. **Créer le repo** sur GitHub (public ou privé peu importe, GitHub Pages marche dans les deux cas avec un compte gratuit en 2024+).
2. **Pousser le dossier** :
   ```bash
   git remote add origin git@github.com:<ton-user>/<nom-repo>.git
   git branch -M main
   git push -u origin main
   ```
3. **Activer Pages** dans `Settings → Pages` :
   - Source : `Deploy from a branch`
   - Branch : `main` / dossier `/ (root)`
4. Le site sera dispo sous 1–2 minutes à `https://<ton-user>.github.io/<nom-repo>/`

### Domaine personnalisé

1. Créer un fichier `CNAME` à la racine du repo contenant juste le domaine (ex: `meg-mtb.com`)
2. Chez le registrar, ajouter un enregistrement CNAME (sous-domaine) ou A (apex) pointant vers GitHub Pages :
   - Apex (`meg-mtb.com`) → 4 records A : `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Sous-domaine (`www.meg-mtb.com`) → CNAME vers `<ton-user>.github.io`
3. Décommenter la ligne `Sitemap:` dans `robots.txt` une fois le domaine actif
4. Activer HTTPS dans `Settings → Pages`

## Notes

- Le site charge **Google Fonts** (Space Grotesk) en CDN externe — aucune autre dépendance réseau.
- Les icônes sont un **sprite SVG inline** (style Lucide, MIT) en haut du `body`, donc aucun fichier d'icônes à charger.
- Le système gamification se réinitialise à chaque visite (state en mémoire, rien n'est persisté côté serveur).
