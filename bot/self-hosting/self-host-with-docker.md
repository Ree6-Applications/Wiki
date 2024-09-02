---
description: A Guide about how to self host Ree6 with Docker!
---

# Self host with Docker

## Docker Compose

```yaml
services:
  ree6:
    image: ree6/bot:3.1.12
    volumes:
      - /PATH/bot/storage:/storage
      - /PATH/bot/languages:/languages
      - /PATH/bot/config.yml:/config.yml
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
    
```
