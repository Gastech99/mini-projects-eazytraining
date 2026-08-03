# Définit une variable d'argument pour la version de l'image Nginx
ARG version="latest"

# Utilise l'image officielle Nginx avec la version choisie
FROM nginx:${version}

# Ajoute une métadonnée sur l'image
LABEL maintainer="gastech"

# Installe git et nettoie le cache pour garder l'image légère
RUN apt-get update && \
    apt-get install -y git \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Supprime le contenu par défaut de Nginx et clone un site statique dans le dossier de rendu
RUN rm -rf /usr/share/nginx/html/* \
    && git clone https://github.com/diranetafen/static-website-example.git /usr/share/nginx/html/

# Expose le port 80 pour servir le site web
EXPOSE 80

# Démarre Nginx en mode premier plan
ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]