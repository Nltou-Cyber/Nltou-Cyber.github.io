# Portfolio de Baptiste Counil — consignes pour Claude Code

Site statique (HTML + CSS, sans framework ni build) publié par GitHub Pages depuis le dossier `docs/` de la branche `main`.
Adresse : https://bcounil.github.io. Le propriétaire débute avec Git et GitHub : expliquer simplement, en français.

Seul `docs/` est publié (réglage Settings, Pages : branche `main`, dossier `/docs`). `CLAUDE.md` et `README.md`
restent à la racine : ils sont lisibles dans le dépôt public, mais pas sur le site. Ne rien ajouter d'autre à la racine.

## Deux parties

| Partie | Dossier | Public visé |
|---|---|---|
| Vitrine pro | `docs/index.html` | Recruteurs, lien mis sur LinkedIn |
| Espace oral BTS SIO (épreuve E5) | `docs/bts-sio/` | Jury du BTS SIO SISR, session 2027 |

Pages communes dans `docs/` : `mentions-legales.html`, `confidentialite.html`, `404.html` (chemins absolus, servie partout),
`sitemap.xml`, `robots.txt`, `.nojekyll`. Styles : `docs/assets/style.css` (un seul fichier pour tout le site).

### Espace oral E5 (`docs/bts-sio/`)
- `index.html` : la « baie de brassage », une prise RJ45 par compétence.
- Une page par compétence : `patrimoine.html`, `incidents.html`, `presence-en-ligne.html`, `projet.html`, `service.html`, `developpement-pro.html`.
- `contexte.html`, `competences.html`, `formation.html`, `annexes.html`.
- Trame imposée par l'Aftec : contexte → organisation et démarche → ce que j'ai fait personnellement → preuves (annexes) → recul.

## Règle n°1 : confidentialité

Le dépôt, son historique Git et le site sont **publics**. Ce fichier aussi : il ne doit contenir aucun nom réel
(outil, service, site, ville, domaine, machine), même pour dire qu'il est interdit.

Ne jamais publier sans autorisation écrite :
- captures d'écran d'outils internes, numéros de tickets ou d'inventaire, noms d'agents ;
- noms des outils internes de l'employeur, nom exact du service, noms des sites et des villes où ils se trouvent ;
- chiffres internes (taille d'équipe, nombre de postes, nombre de sites), délais de traitement (SLA) ;
- détails techniques du labo du centre de formation (projet Lab Refresh) : architecture, nom de domaine,
  noms des serveurs et des postes, plan d'adressage IP, nom du réseau WiFi, mots de passe ;
- numéro de téléphone, adresse personnelle, adresse e-mail personnelle.

Formulations génériques autorisées : « outil de ticketing interne », « outil d'inventaire de type OCS Inventory », « base de gestion de parc basée sur GLPI ».
Le détail complet est réservé à la version PowerPoint montrée au jury.

### Vérification de confidentialité

1. **En début de session**, avant toute modification, demander à Baptiste la liste des termes interdits.
   Il la garde dans une note privée, hors du dépôt. Ne jamais écrire ces termes dans un fichier du dépôt,
   un message de commit, un nom de branche ou une page du site.
2. Avant chaque commit, chercher ces termes (remplacer `terme1|terme2` par la liste reçue). La commande ne doit rien renvoyer :
   `grep -rniIE "terme1|terme2" --exclude-dir=.git .`
3. Chercher aussi les adresses IP, numéros de téléphone français, adresses e-mail et adresses MAC. La commande ne doit rien renvoyer :
   `grep -rnIE "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b|(\+33 ?|\b0)[1-9]([ .-]?[0-9]{2}){4}\b|[A-Za-z0-9._%+-]+@[A-Za-z0-9-]+\.[A-Za-z.]{2,}|\b([0-9A-Fa-f]{2}[:-]){5}[0-9A-Fa-f]{2}\b" --exclude-dir=.git .`

Si Baptiste ne donne pas la liste, faire seulement l'étape 3 et le lui signaler à la fin.

## Conventions de contenu
- Français, phrases simples, voix active, première personne pour ce que Baptiste a fait.
- Encadrés à remplir : `<div class="todo">` (« À compléter : … »). Les remplacer par le contenu final, puis supprimer l'encadré.
- État d'une compétence sur `docs/bts-sio/index.html` : LED `led` (verte) = page complète, `led wip` (orange) = en cours.
  Mettre aussi à jour la colonne « État » de `docs/bts-sio/competences.html`.
- Couleur de câble par compétence (variables CSS) : patrimoine `--c-patrimoine` (bleu), incidents `--c-incidents` (rouge),
  présence en ligne `--c-presence` (violet), projet `--c-projet` (orange), service `--c-service` (vert), développement pro `--c-devpro` (jaune).
  Pour colorer un élément, lui ajouter la classe correspondante : `cable-patrimoine`, `cable-incidents`, `cable-presence`,
  `cable-projet`, `cable-service` ou `cable-devpro`.
- En-tête et pied de page sont recopiés dans chaque fichier HTML : une modification de navigation doit être faite dans toutes les pages
  de la partie concernée.

## Conventions de style
- Polices : Barlow (texte) et Barlow Condensed (titres). Pas de capitales pour les libellés, pas de « · » entre des éléments, pas de flèche « → » dans les liens.
- Le seul élément visuel fort est la baie de brassage. Le reste reste sobre : texte aligné à gauche, lignes de moins de 75 caractères.
- Vérifier le rendu sur mobile (390 px de large) et le contraste. Respecter `prefers-reduced-motion`.

## Politique de sécurité du contenu (CSP)
Chaque page a, juste après la balise `viewport`, la même balise `<meta http-equiv="Content-Security-Policy" ...>`.
Une nouvelle page doit la reprendre à l'identique. Le navigateur bloque tout ce qu'elle n'autorise pas :
- pas d'attribut `style="..."`, de balise `<style>`, de script écrit dans la page ni d'attribut `onclick` :
  utiliser des classes de `docs/assets/style.css` ;
- seuls les fichiers du site sont chargés, y compris le script GoatCounter (`docs/assets/count.js`) ;
  seul l'envoi du comptage sort du site, vers `bcounil.goatcounter.com` ;
- ajouter un service externe (vidéo, carte, police…) oblige à modifier la CSP dans toutes les pages,
  puis à vérifier qu'aucune erreur CSP n'apparaît dans la console du navigateur.

`frame-ancestors`, qui interdit d'afficher le site dans une iframe, ne fonctionne pas dans une balise meta,
et GitHub Pages ne permet pas d'ajouter d'en-têtes HTTP : cette protection n'est pas possible ici.

## Statistiques GoatCounter
`docs/assets/count.js` est une copie du script officiel de GoatCounter (licence ISC : garder l'en-tête).
Il ne se met pas à jour tout seul, et c'est rarement utile. Pour le mettre à jour : télécharger
https://gc.zgo.at/count.js, remplacer `docs/assets/count.js`, puis vérifier qu'aucune erreur CSP n'apparaît
dans la console et que la visite apparaît dans GoatCounter.

## Si le nom d'utilisateur GitHub change
1. Renommer le dépôt en `nouveau-nom.github.io` (Settings du dépôt).
2. Remplacer `bcounil.github.io` partout : balises `canonical`, `docs/sitemap.xml`, `docs/robots.txt`, `README.md`, ce fichier.
3. Prévenir Baptiste : l'ancienne adresse ne redirige pas. Mettre à jour le lien LinkedIn et la bannière LinkedIn.

## Avant de pousser
- Vérifier que tous les liens internes existent.
- Lancer la vérification de confidentialité ci-dessus.
- Commits en français, courts et clairs.
