# Tableau comparatif a remplir



| #   | Mesure                                 | VM (releve TP1/TP2) | Conteneur (ce TP)                                   |                                                    |
| --- | -------------------------------------- | ------------------- | --------------------------------------------------- | -------------------------------------------------- |
| C1  | Temps de demarrage                     | 45sec               | ![](https://g0v.hackmd.io/_uploads/B1xrNqxLhMx.png) |                                                    |
| C2  | Espace occupe                          | 8 Go                | ![](https://g0v.hackmd.io/_uploads/r1mSAlLhfl.png)  |                                                    |
| C3  | Memoire consomee au repos              | 19 Mo               | ![](https://g0v.hackmd.io/_uploads/SktOAeIhMg.png) |
| C4  | Nombre de noyaux en fonctionnement     | 1,045 Mo            |                                                     |                                                    |
| C5  | Temps pour creer un deuxieme identique | 30 min              |                                                     |                                                    

Question 1: Appartenir au groupe `docker` donne pratiquement les mêmes pouvoirs que disposer d’un accès administrateur avec `sudo`. En montant `/` de l’hôte dans un conteneur, l’utilisateur peut accéder aux fichiers système et les modifier sans nouvelle demande de mot de passe. Il faut donc réserver ce groupe aux utilisateurs de confiance. Dans ce TP, l’hôte Docker est la VM Debian, pas Windows.

Question 2: La partie `-p 8080:80` correspond à la redirection de port : le port 8080 de la VM Debian est redirigé vers le port 80 du conteneur nginx. Docker gère cette redirection et le lancement du conteneur, mais ce n’est pas un hyperviseur : le conteneur partage le noyau de la VM Debian.

Question 3: Les deux commandes `uname -r` affichent le même résultat : `6.12.111+deb13-amd64`. Les processus nginx du conteneur sont aussi visibles depuis la VM. Le conteneur partage donc le noyau de la VM Debian : il n’a pas son propre noyau, contrairement à une machine virtuelle.

Question 4: C’est le mécanisme des espaces de noms de processus, appelé PID namespace, qui produit cet effet. Le conteneur ne voit que ses propres processus et nginx y porte le PID 1. Depuis la VM, ces mêmes processus sont visibles avec des PID différents.