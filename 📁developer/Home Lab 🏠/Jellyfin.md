#music #media #player
# [Jellyfin](https://jellyfin.org/)
The Free Software Media System.

I use this exclusively for music hosting because [Plex.tv](Plex.tv.md) has more restrictions on client music playback. 

## connections
- one

## installation
### [Docker](Docker.md)
1. `./compose.yml`
```
version: "3.7"

services:

  jellyfin:
    image: jellyfin/jellyfin:latest
    container_name: jellyfin
    restart: unless-stopped
    ports:
      - 8096:8096
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Chicago
    volumes:
      - ./config:/config
      - ./cache:/cache
      - /mnt/<externalDrive>/jellyfin/media:/media:ro #:ro = read-only

# networks:
#   default:
#     external:
#       name: nginx-prox-mgmt-3_default
```