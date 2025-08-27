# 1) Copie le fichier dans le conteneur en cours
docker cp realm-export.json keycloak-1:/opt/keycloak/data/import/realm-export.json

# 2) Lance l’import manuel avec override
docker compose exec keycloak /opt/keycloak/bin/kc.sh \
  import --file /opt/keycloak/data/import/realm-export.json --override=true

# 3) Redémarre Keycloak normalement
docker compose restart keycloak

# 4) Autoriser Docker Desktop à lire “Documents”

Ouvre Réglages Système → Confidentialité et sécurité

Va dans Accès complet au disque

Ajoute “Docker Desktop” (et active le bouton)

(Sur certaines versions : aussi Fichiers et dossiers → coche Documents)

# 5) edémarre Docker Desktop

# 6) Recrée nginx :

docker compose up -d --force-recreate nginx
docker compose exec nginx ls -la /usr/share/nginx/html# poc-keycloack-security
