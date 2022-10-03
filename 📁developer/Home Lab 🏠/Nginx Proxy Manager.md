# [Nginx Proxy Manager](https://nginxproxymanager.com/)
Expose your services easily and securely

### connections
- [Pi-hole](Pi-hole.md) for local DNS. Make pretty names for any service

## installation
## [Docker](Docker.md)
1. `compose.yml`
```
version: '3'
services:
  app:
    image: 'jc21/nginx-proxy-manager:latest'
    restart: unless-stopped
    ports:
      - '80:80'
      - '81:81'
      - '443:443'
    volumes:
      - ./data:/data
      - ./letsencrypt:/etc/letsencrypt
```

Default Admin User:
```
Email:    admin@example.com
Password: changeme
```