# [Homepage - Nextcloud](https://nextcloud.com/)

### connections
- syncs pictures for [PhotoPrism](PhotoPrism.md) to read

# installation
### [Docker](../Docker.md)
1. `compose.yml`
```
version: '2'

volumes:
  nextcloud:
  db:

services:
  db:
    image: mariadb
    restart: always
    command: --transaction-isolation=READ-COMMITTED --binlog-format=ROW --innodb-read-only-compressed=OFF
    volumes:
      - /home/<username>/docker/nextcloud/db:/var/lib/mysql
    environment:
      - MYSQL_ROOT_PASSWORD=<password09>
      - MYSQL_PASSWORD=<password09>
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextcloud

  app:
    image: nextcloud
    restart: always
    ports:
      - 8080:80
    links:
      - db
    volumes:
      - /home/<username>/docker/nextcloud/html:/var/www/html
      - /home/<username>/docker/nextcloud/html/apps:/var/www/html/custom_apps 
      - /home/<username>/docker/nextcloud/html/config:/var/www/html/config 
      - /mnt/<externalDrive>/nextcloud/data:/var/www/html/data
    environment:
      - MYSQL_PASSWORD=<password09>
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextcloud
      - MYSQL_HOST=db
```