# Portfolio

Site publié sur https://bcounil.github.io (GitHub Pages, branche `main`, dossier `docs/`).

## Contenu

Tout le site est dans `docs/` : c'est le seul dossier publié.

- `docs/index.html` : vitrine pro (parcours, compétences, projets, formation, contact), le lien à mettre sur LinkedIn.
- `docs/bts-sio/` : espace oral BTS SIO (épreuve E5), avec la baie de brassage (une prise par compétence) et une page par compétence.
- `docs/mentions-legales.html`, `docs/confidentialite.html`, `docs/404.html`, `docs/sitemap.xml`, `docs/robots.txt`.
- `CLAUDE.md` (à la racine, non publié sur le site) : consignes détaillées pour modifier le site avec Claude Code.
- `docs/assets/style.css` : toute la mise en forme. Chaque compétence a une couleur de câble (`--c-...`).

## Modifier une page

- Les encadrés « À compléter » ont la classe `todo` : les remplacer par le contenu final.
- État d'une compétence : dans `docs/bts-sio/index.html`, une LED `led` (verte) = page complète, `led wip` (orange) = en cours.

## Règle de confidentialité

Le dépôt et le site sont publics. Ne rien publier d'interne à l'employeur ou au centre de formation
(captures, noms de sites, chiffres, noms d'outils internes, architecture du labo) sans autorisation écrite.
Le détail complet est réservé à la version PowerPoint présentée au jury.
