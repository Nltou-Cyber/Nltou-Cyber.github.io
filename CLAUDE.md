# Portfolio de Baptiste Counil — consignes pour Claude Code

Site statique (HTML + CSS, sans framework ni build) publié par GitHub Pages depuis la branche `main`.
Adresse : https://bcounil.github.io. Le propriétaire débute avec Git et GitHub : expliquer simplement, en français.

## Deux parties

| Partie | Dossier | Public visé |
|---|---|---|
| Vitrine pro | racine : `index.html` | Recruteurs, lien mis sur LinkedIn |
| Espace oral BTS SIO (épreuve E5) | `bts-sio/` | Jury du BTS SIO SISR, session 2027 |

Pages communes à la racine : `mentions-legales.html`, `confidentialite.html`, `404.html` (chemins absolus, servie partout),
`sitemap.xml`, `robots.txt`, `.nojekyll`. Styles : `assets/style.css` (un seul fichier pour tout le site).

### Espace oral E5 (`bts-sio/`)
- `index.html` : la « baie de brassage », une prise RJ45 par compétence.
- Une page par compétence : `patrimoine.html`, `incidents.html`, `presence-en-ligne.html`, `projet.html`, `service.html`, `developpement-pro.html`.
- `contexte.html`, `competences.html`, `formation.html`, `annexes.html`.
- Trame imposée par l'Aftec : contexte → organisation et démarche → ce que j'ai fait personnellement → preuves (annexes) → recul.

## Règle n°1 : confidentialité

Le dépôt et le site sont **publics** (y compris l'historique Git). Ne jamais publier sans autorisation écrite :
- captures d'écran d'outils internes, numéros de tickets, d'inventaire, noms d'agents ;
- noms des outils internes de la DGFiP, noms des sites, chiffres internes (taille d'équipe, nombre de postes), délais (SLA) ;
- détails techniques du projet Lab Refresh du centre de formation (architecture, plan d'adressage IP, noms des serveurs, mots de passe) ;
- numéro de téléphone, adresse personnelle.
Formulations génériques autorisées : « outil de ticketing interne », « outil d'inventaire de type OCS Inventory », « base de gestion de parc basée sur GLPI ».
Le détail complet est réservé à la version PowerPoint montrée au jury.

Avant chaque commit, vérifier : `grep -rniE "[termes retirés]" --include=*.html .` ne doit rien renvoyer.

## Conventions de contenu
- Français, phrases simples, voix active, première personne pour ce que Baptiste a fait.
- Encadrés à remplir : `<div class="todo">` (« À compléter : … »). Les remplacer par le contenu final, puis supprimer l'encadré.
- État d'une compétence sur `bts-sio/index.html` : LED `led` (verte) = page complète, `led wip` (orange) = en cours.
  Mettre aussi à jour la colonne « État » de `bts-sio/competences.html`.
- Couleur de câble par compétence (variables CSS) : patrimoine `--c-patrimoine` (bleu), incidents `--c-incidents` (rouge),
  présence en ligne `--c-presence` (violet), projet `--c-projet` (orange), service `--c-service` (vert), développement pro `--c-devpro` (jaune).
- En-tête et pied de page sont recopiés dans chaque fichier HTML : une modification de navigation doit être faite dans toutes les pages
  de la partie concernée.

## Conventions de style
- Polices : Barlow (texte) et Barlow Condensed (titres). Pas de capitales pour les libellés, pas de « · » entre des éléments, pas de flèche « → » dans les liens.
- Le seul élément visuel fort est la baie de brassage. Le reste reste sobre : texte aligné à gauche, lignes de moins de 75 caractères.
- Vérifier le rendu sur mobile (390 px de large) et le contraste. Respecter `prefers-reduced-motion`.

## Si le nom d'utilisateur GitHub change
1. Renommer le dépôt en `nouveau-nom.github.io` (Settings du dépôt).
2. Remplacer `bcounil.github.io` partout : balises `canonical`, `sitemap.xml`, `robots.txt`, `README.md`, ce fichier.
3. Prévenir Baptiste : l'ancienne adresse ne redirige pas. Mettre à jour le lien LinkedIn et la bannière LinkedIn.

## Avant de pousser
- Vérifier que tous les liens internes existent.
- Lancer la vérification de confidentialité ci-dessus.
- Commits en français, courts et clairs.
