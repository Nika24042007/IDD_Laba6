# Wish list ToDo
## Структура
<pre>
APP-TODO/
lab6/
├── infrastructure/
│   └── postgres/
│       ├── README.md                     (новый)
│       ├── kustomize/
│       │   ├── base/
│       │   │   ├── kustomization.yaml    (новый)
│       │   │   ├── statefulset.yaml      (из postgres.yaml, переделан)
│       │   │   ├── service.yaml          (новый)
│       │   │   └── secret.yaml           (пароль из secret.yaml)
│       │   └── overlays/
│       │       ├── dev/
│       │       │   ├── kustomization.yaml (новый)
│       │       │   └── patch-storage.yaml (новый)
│       │       └── prod/
│       │           ├── kustomization.yaml (новый)
│       │           └── patch-storage.yaml (новый)
│       └── helm/
│           └── postgres-infra/
│               ├── Chart.yaml            (новый)
│               ├── values-dev.yaml       (новый)
│               ├── values-prod.yaml      (новый)
│               └── templates/
│                   ├── statefulset.yaml
│                   ├── service.yaml
│                   └── secret.yaml
└── application/
    └── k8s/
        ├── kustomization/
        │   ├── base/
        │   │   ├── kustomization.yaml    (новый)
        │   │   ├── backend.yaml          (из backend.yaml)
        │   │   ├── frontend.yaml         (из frontend.yaml)
        │   │   ├── configmap.yaml        (из configmap.yaml)
        │   │   └── ingress.yaml          (из ingress.yaml)
        │   └── overlays/
        │       ├── dev/
        │       │   ├── kustomization.yaml (новый)
        │       │   └── secret.yaml       (новый, с database_url)
        │       └── prod/
        │           ├── kustomization.yaml (новый)
        │           └── secret.yaml       (новый, с database_url для prod)
        └── helm/
            └── wishlist-app/
                ├── Chart.yaml            (новый)
                ├── values.yaml           (новый)
                ├── values-dev.yaml       (новый)
                ├── values-prod.yaml      (новый)
                └── templates/
                    ├── backend-deployment.yaml
                    ├── backend-service.yaml
                    ├── frontend-deployment.yaml
                    ├── frontend-service.yaml
                    ├── configmap.yaml
                    ├── ingress.yaml
                    └── secret.yaml
│
└── README.md                 # Эта инструкция
</pre>




## Запуск

### Kustomization

### Helm