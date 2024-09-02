---
description: A Guide about how to self host the Webinterface with Docker!
---

# Self host with Docker

## Docker Compose

```yaml
version: "3"

services:
  frontend:
    name: frontend
    image: ree6/frontend
    environment:
      - BACKEND_URL=https://api.ree6.de # Change this to use your backend url
      - INVITE_URL=https://invite.ree6.de # Change this to your bot's invite link

      - HOST=0.0.0.0 # IP address to listen to

      - TZ=Europe/Berlin # Set your timezone
      - NODE_ENV=production # Internal server error messages will not send stacktrace to the browser in production

    # Uncomment the lines below to enable Traefik
    # Don't forget to uncomment the bottom of the file as well
    # Don't forget to comment out the `ports` section
    # labels:
    #   - traefik.http.routers.ree6_frontend.rule=Host(`ree6.example.com`) # Set to your domain (+subdomain)
    #   - traefik.http.routers.ree6_frontend.entrypoints=websecure
    #   - traefik.http.routers.ree6_frontend.tls.certresolver=lets-encrypt
    #   - traefik.http.routers.ree6_frontend.service=ree6_frontend
    #   - traefik.http.services.ree6_frontend.loadBalancer.server.port=3000 # Must be same as `PORT` variable
    # networks:
    #   - traefik
    ports: # Comment this out if using traefik
      - 3000:3000 # Comment this out if using traefik

    restart: unless-stopped
  backend:
    name: backend
    image: ree6/backend
    volumes:
      - /PATH/backend/config.yml:/config.yml
    depends_on:
      - db
  db:
    image: mariadb:latest
    environment:
      MYSQL_ROOT_PASSWORD: password
      MYSQL_DATABASE: ree6
      MYSQL_USER: ree6
      MYSQL_PASSWORD: ree6
    volumes:
      - /PATH/db:/var/lib/mysql

# Uncomment this to use everything in one stack.    
#  ree6:
#    image: ree6/bot:3.1.12
#    volumes:
#      - /PATH/bot/storage:/storage
#      - /PATH/bot/languages:/languages
#      - /PATH/bot/config.yml:/config.yml
#    depends_on:
#      - db

# Uncomment this for Traefik
# networks:
#   traefik:
#     external: true
```
