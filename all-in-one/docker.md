# 🐋 Docker

If you use docker here is a docker-compose file containing the frontend, backend, and the bot!

{% code title="docker-compose.yml" fullWidth="false" %}
```yaml
services:
  bot:
    container_name: ree6_bot
    image: ree6/bot:latest
    environment:
      - config=/opt/ree6/config/config.yml
    volumes:
      - ./bot/storage/:/storage/
      - ./bot/languages/:/languages/
      - ./bot/config/:/opt/ree6/config/
    depends_on:
      - db
  frontend:
    container_name: ree6_frontend
    image: ree6/frontend:latest

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
    container_name: ree6_backend
    image: ree6/backend:latest
    environment:
      - config=/opt/ree6/config/config.yml
    volumes:
      - ./backend/config/:/opt/ree6/config/
    depends_on:
      - db
  db:
    container_name: ree6_db
    image: mariadb:latest
    environment:
      MYSQL_ROOT_PASSWORD: password
      MYSQL_DATABASE: ree6
      MYSQL_USER: ree6
      MYSQL_PASSWORD: ree6
    volumes:
      - ./db:/var/lib/mysql
```
{% endcode %}
