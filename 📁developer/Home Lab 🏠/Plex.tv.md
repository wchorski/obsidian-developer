#music #movie #tv #film #media #player
# [Plex](https://www.plex.tv/)
Stream Movies & TV Shows.

Why do I use this for movies when I have [Jellyfin](Jellyfin.md)? Because movie playback seems more stable, it's easy to share libraries, and I don't watch movies on mobile 

## connections
- one

## installation
### [Docker](Docker.md) 
- [plexinc/pms-docker: Plex Media Server Docker repo, for all your PMS docker needs. (github.com)](https://github.com/plexinc/pms-docker)
- get token from [Claim | Plex](https://www.plex.tv/claim/)
1. `./compose.yml`
```
version: '2'
services:
  plex:
    container_name: plex-pms
    image: plexinc/pms-docker
    restart: unless-stopped
    ports:
      - 32400:32400/tcp
      - 3005:3005/tcp
      - 8324:8324/tcp
      - 32469:32469/tcp
      - 1900:1900/udp
      - 32410:32410/udp
      - 32412:32412/udp
      - 32413:32413/udp
      - 32414:32414/udp
    environment:
      - TZ=America/Chicago
      - PLEX_CLAIM=claim-<claim_Token>
      - ADVERTISE_IP=http://<yourDomain_or_IP>:32400/
    hostname: FireMedia

    volumes:
      - ./config:/config
      - ./transcodes:/transcode
      - /mnt/<externalDrive>/plex/media:/firemedia #unique name for inside the container
```