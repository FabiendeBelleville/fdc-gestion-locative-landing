# Landing — liste d'attente « gestion locative »

Source de vérité : ce dossier, dans le dépôt privé `gestion-locative`. Publication : GitHub Pages depuis le dépôt public `FabiendeBelleville/fdc-gestion-locative-landing`, sur https://gestion-locative.fabiendrouinconsulting.com. Ne pas éditer dans le dépôt public, il est écrasé à chaque publication.

## Publier une modification

Depuis la racine du dépôt privé, après avoir commité les changements du dossier `landing/` :

```
git push --force landing-public "$(git subtree split --prefix=landing main):main"
```

Le remote `landing-public` pointe sur https://github.com/FabiendeBelleville/fdc-gestion-locative-landing.git. GitHub Pages redéploie en une à deux minutes. Le `--force` est normal : le dépôt public n'est qu'une cible de déploiement, et dès que `main` contient des commits de fusion, l'historique découpé par subtree n'est plus en avance rapide (le simple `git subtree push` est alors refusé).

## DNS (à faire une fois, chez Squarespace Domains)

| Type | Hôte | Cible |
|---|---|---|
| CNAME | `gestion-locative` | `fabiendebelleville.github.io` |

Une fois le CNAME propagé et le certificat émis par GitHub (quelques minutes à une heure), forcer HTTPS :

```
gh api -X PUT repos/FabiendeBelleville/fdc-gestion-locative-landing/pages -F https_enforced=true
```

## Configuration (bloc `CONFIG` de `index.html`)

- `calendlyUrl` : page de réservation Google Agenda FDC — branchée.
- `contactEmail` : fabien@fabiendrouinconsulting.com — branché.
- `formEndpoint` : vide. Repli actif : la confirmation s'affiche et un email pré-rempli est proposé au visiteur, rien n'est perdu. Pour recevoir les inscriptions sans dépendre de la boîte mail du visiteur, créer un formulaire Formspree (offre gratuite) et coller son URL ici, puis republier.

## Mentions légales

Éditeur : Fabien Drouin. Hébergeur : GitHub, Inc. (GitHub Pages). La réserve légale loi Hoguet et la note sur les données figurent en pied de page.
