# CICD

## Exemple d'utilisation

```
name: Deploy

on:
  push:
    tags:
      - '*'

jobs:
  deploy:
    uses: redyd-git/.github/.github/workflows/deploy.yml@main
    with:
      image_name: <nom de l'image>
    secrets:
      REGISTRY_USER: ${{ secrets.REGISTRY_USER }}
      REGISTRY_PASSWORD: ${{ secrets.REGISTRY_PASSWORD }}
```

**Veuillez à bien ajouter les variables dans le repo**
**Ne pas oubliez d'ajouter dans le docker-compose le networks proxy**:
```
services:
  app:
    image: registry.redyd.dev/<nom de l'image>:latest
    container_name: <nom du container>
    restart: unless-stopped
    ports:
      - "3000:3000"
    networks:
      - proxy

networks:
  proxy:
    external: true
```
