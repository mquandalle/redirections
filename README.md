# Outil de gestion des redirections

Vous pouvez par exemple rediriger : https://workinfrance.beta.gouv.fr vers https://work-in-france.incubateur.social.gouv.fr/

## Comment utiliser ?

Vous devez avoir accès à la configuration DNS du domaine redirigé, à la console Scalingo de l'app `redirections-beta`, et à ce dépôt. A défaut, vous coordonner avec des personnes qui ont ces accès; vous pouvez demander sur le chan `#incubateur-ops` du Slack beta.

La redirection fonctionne sous réserve de ces *trois* conditions:
- configuration de la redirection `anciendomaine` -> `nouveaudomaine` dans ce dépôt: créez une pull request en ajoutant votre domaine dans `servers.conf.erb` (si vous voulez de l'aide sur le config nginx, vous pouvez demander sur `#incubateur-ops` sur le Slack); le déploiement est automatique
- configuration du DNS: `anciendomaine` est un CNAME vers betagouv-redirections.osc-fr1.scalingo.io.
- configuration de Scalingo: déclarer `anciendomaine` parmi les domaines de l'app redirection

Si `anciendomaine` est de la forme `ancien.beta.gouv.fr` c'est la zone DNS `beta.gouv.fr` qu'il faut modifier.

## Notes
- Si vous hésitez entre "permanent" ou pas, n'hésitez pas à demander de l'aide
- Le `$1` a la fin de l'url de redirection indique que vous conservez la partie après le domaine ( `https://workinfrance.beta.gouv.fr/mapage?params` deviens `https://work-in-france.incubateur.social.gouv.fr/mapage?params`
