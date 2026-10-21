# Tableau comparatif a remplir



| #   | Mesure                             | VM (releve TP1/TP2) | Conteneur (ce TP)                                   |     |     |     |
| --- | ---------------------------------- | ------------------- | --------------------------------------| ---          |---                  | ---                 |
| C1  | Temps de demarrage                 | 45sec               | ![](https://g0v.hackmd.io/_uploads/B1xrNqxLhMx.png) |     |     |   |
| C2  | Espace occupe                      | 8 Go                | ![](https://g0v.hackmd.io/_uploads/r1mSAlLhfl.png)  |     |     |   |
| C3  | Memoire consomee au repos          | 19 Mo               | ![](https://g0v.hackmd.io/_uploads/SktOAeIhMg.png)  |     |     |   |
| C4  | Nombre de noyaux en fonctionnement | 1,045 Mo            |                                       | C5  |            |     |     |     |     |                     |

**Question 1:** Appartenir au groupe `docker` donne pratiquement les mêmes pouvoirs que disposer d’un accès administrateur avec `sudo`. En montant `/` de l’hôte dans un conteneur, l’utilisateur peut accéder aux fichiers système et les modifier sans nouvelle demande de mot de passe. Il faut donc réserver ce groupe aux utilisateurs de confiance. Dans ce TP, l’hôte Docker est la VM Debian, pas Windows.

**Question 2:** La partie `-p 8080:80` correspond à la redirection de port : le port 8080 de la VM Debian est redirigé vers le port 80 du conteneur nginx. Docker gère cette redirection et le lancement du conteneur, mais ce n’est pas un hyperviseur : le conteneur partage le noyau de la VM Debian.

**Question 3:** Les deux commandes `uname -r` affichent le même résultat : `6.12.111+deb13-amd64`. Les processus nginx du conteneur sont aussi visibles depuis la VM. Le conteneur partage donc le noyau de la VM Debian : il n’a pas son propre noyau, contrairement à une machine virtuelle.

**Question 4:** C’est le mécanisme des espaces de noms de processus, appelé PID namespace, qui produit cet effet. Le conteneur ne voit que ses propres processus et nginx y porte le PID 1. Depuis la VM, ces mêmes processus sont visibles avec des PID différents.

**Question 5:** Les dix conteneurs ont été créés en 20,941 secondes. Chaque conteneur affiché utilise environ 81,9 ko de données propres, soit environ 819 ko pour dix, hors métadonnées Docker. Les 207 Mo indiqués comme « virtual » ne sont pas copiés dix fois : les conteneurs partagent les couches de la même image nginx et possèdent chacun leur couche modifiable.
Créer dix VM aurait pris bien plus de temps et d’espace, car chacune possède son propre disque et démarre son propre système.

**Question 6:** Mon travail était enregistré dans la couche modifiable du conteneur. Cette couche a été supprimée avec le conteneur, donc la page personnalisée a disparu. Le nouveau conteneur repart de l’image nginx d’origine et affiche sa page par défaut.

**Question 7:** `-v ~/site:/...` monte un dossier précis de la VM dans le conteneur. C’est pratique pour modifier directement les fichiers d’un site depuis la VM.
`-v donnees-test:/...` utilise un volume nommé dont Docker gère l’emplacement. Il convient notamment aux données persistantes d’une base de données.
Avec `--rm`, le conteneur est supprimé à sa sortie, mais le volume nommé est conservé : le fichier reste donc disponible pour un autre conteneur.

**Question 8:** L’historique affiche 22 entrées, dont 10 couches de taille non nulle ; les autres correspondent à des métadonnées. La plus volumineuse fait 122 Mo et correspond à l’installation de nginx et de ses dépendances dans l’image de base.
Le nettoyage `rm -rf /var/lib/apt/lists/*` doit être dans la même instruction `RUN` que l’installation pour éviter d’enregistrer les listes apt dans une couche. Dans une instruction séparée, les fichiers resteraient présents dans la couche précédente et continueraient à prendre de la place.

**Question 9:** La première construction a pris 19,941 secondes, contre 2,653 secondes pour la deuxième, soit environ 7,5 fois moins de temps. L’image de base a été réutilisée et l’étape `RUN` d’installation des paquets a été reprise du cache, comme l’indique `CACHED`. Seule la copie du site avec `COPY` a dû être refaite, puisque son contenu avait changé.
Il vaut donc mieux placer les instructions qui changent rarement au début du Dockerfile et celles qui changent souvent à la fin, pour profiter au maximum du cache.

**Question 10:** Docker fournit un DNS interne sur le réseau créé par Compose. Il traduit le nom du service `base` en adresse IP, ici `172.18.0.2`, ce qui permet au conteneur web de le joindre sans connaître son IP. Le ping fonctionne avec 3 réponses et 0 % de perte.
Comme le DNS vu en séance 3, ce mécanisme associe un nom à une adresse IP, mais ici il sert à retrouver les services du réseau Docker.

**Question 11:** Oui, la table a survécu : après la suppression et la recréation des conteneurs, la requête affiche toujours la valeur 42. Les données sont conservées dans le volume nommé `donnees-pg`, que `docker compose down` ne supprime pas.
Avec `docker compose down -v`, ce volume aurait aussi été supprimé : la table et ses données auraient donc été perdues.

**Question 12:**

| Besoin | VM ou conteneur ? | Pourquoi ? |
|---|---|---|
| a. Site web mis à jour dix fois par jour | Conteneur | Les nouvelles versions sont rapides à construire et à déployer. |
| b. Analyser un logiciel malveillant inconnu | VM | Son noyau séparé offre une isolation plus forte, avec un réseau isolé et les partages désactivés. |
| c. Logiciel uniquement Windows sur un serveur Linux | VM | Elle permet d’exécuter Windows avec son propre noyau sur un hôte Linux. |
| d. Donner à 30 étudiants le même environnement de développement | Conteneur | Une même image fournit un environnement identique, léger et rapide à distribuer. |
| e. Héberger une base de données de production | Conteneur | Un volume persistant conserve les données indépendamment du conteneur, avec des sauvegardes adaptées. |