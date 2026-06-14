# Architecture du pipeline CI/CD

```mermaid
flowchart LR
    A[Dev pousse le code sur GitHub] --> B[Webhook GitHub Actions]
    B --> C[Runner GitHub]
    C --> D[Job 1: tests Pytest]
    D -->|OK| E[Job 2: build Docker image]
    E -->|Sur main| F[Login Docker Hub]
    F --> G[Push image vers Docker Hub]
    G --> H[Serveur Linux ou Cloud]
    H --> I[Docker container en production]
    D -->|KO| X[Pipeline échoue]
    E -->|KO| X
```

## Lecture du schéma

- Le code part de GitHub
- GitHub Actions déclenche le pipeline
- Un runner exécute les jobs
- Les tests valident le code
- Docker construit l'image
- Docker Hub stocke l'image
- Le serveur cible peut ensuite la récupérer et la lancer
