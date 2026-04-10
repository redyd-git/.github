# CICD

## Exemple d'utilisation

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
