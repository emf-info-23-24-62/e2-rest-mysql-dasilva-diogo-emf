# Fichiers de configuration
Ce répertoire contient les fichiers de configuration pour installer votre application.

- Dockerfile
```Dockerfile
#base dde l'image
FROM node:18-alpine

#définit le répertoire
WORKDIR /app

#clone le répertoire github
RUN git clone https://github.com/almoggutin/Node-Express-REST-API-MySQL-JS-Example

WORKDIR ./Node-Express-REST-API-MySQL-JS-Example
#lance le script dev du package.json
CMD ["npm" "run" "dev"]

```
- docker-compose.yml
```yml
services:
  db:
    image: mysql:5.7 
    environment :
      MYSQL_DATABASE: api_example
      MYSQL_ROOT_PASSWORD: rootpass347
      MYSQL_USER: user347
      MYSQL_PASSWORD: pass345
    ports: 
      - 3306:3306

  app:
    #construit une image par rapport au dockerfile dans le répertoir /pp
    build: ./app
    #a besoin du service db pour fonctionner
    depends_on:
      - db
    ports:
      - 8080:8080
```
