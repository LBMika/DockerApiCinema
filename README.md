# Description

Exercice sur Docker : créer une image Docker de l'application située sur le repository https://github.com/progfiler/apiCinema

# Installation

Créer l'image Docker :
~~~shell
docker build -t lbmika/api-cinema:1.0.0 . 
~~~

# Utilisation
Pour fonctionner, l'application à besoin d'une base de données Mongo sur le port 27017 sur le même network.
Le conteneur Mongo doit être nommé 'db-cinema' pour être trouvé par l'application.
~~~shell
docker network create net-cinema
docker run -d -p 27017:27017 --name db-cinema --network net-cinema mongo
docker run -d -p 80:80 --name api-cinema --network net-cinema lbmika/api-cinema:1.0.0
~~~

# Docker compose
Un ficher docker-compose.yml est inclus dans ce projet pour lancer l'application en une seule ligne de commande.
~~~shell
docker compose up
~~~
