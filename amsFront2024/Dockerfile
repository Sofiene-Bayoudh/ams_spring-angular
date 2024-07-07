# Étape 1 : Étape de construction

# Utilise la version 16 de Node.js comme image de base pour l'étape de construction.
FROM node:18.19 AS build

# Définir le répertoire de travail à /app dans le conteneur
WORKDIR /app

COPY package*.json ./
#RUN npm install -g npm@9.6.2
RUN npm i -g @angular/cli
RUN npm install --force
#RUN npm audit fix --force
COPY ./ .
RUN ng build --output-path=dist/

# Utiliser l'image officielle OpenJDK comme étape d'exécution
FROM nginx:latest AS ngi
# Copying compiled code and nginx config to different folder
# NOTE: This path may change according to your project's output folder
COPY --from=build /app/dist/* /usr/share/nginx/html
