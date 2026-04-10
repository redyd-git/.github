# CICD

## Exemple d'utilisation

### Avant, nécessaire de push une première fois sur le serveur

```
docker build -t registry.redyd.dev/mon-app:latest .

docker login registry.redyd.dev -u TON_USER -p TON_PASSWORD

docker push registry.redyd.dev/mon-app:latest
```

```
# .github/workflows/deploy.yml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    uses: redyd-git/.github/.github/workflows/deploy.yml@main
    with:
      image_name: mon-app
      compose_path: /opt/mon-app
    secrets: inherit   # ← injecte automatiquement les secrets de l'org
```
