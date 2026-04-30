# Wish list ToDo
## Структура
<pre>
APP-TODO/
lab6/
├── infrastructure/
│   └── postgres/
│       ├── README.md                     
│       ├── kustomize/
│       │   ├── base/
│       │   │   ├── kustomization.yaml    
│       │   │   ├── statefulset.yaml      
│       │   │   ├── service.yaml          
│       │   │   └── secret.yaml           
│       │   └── overlays/
│       │       ├── dev/
│       │       │   ├── kustomization.yaml 
│       │       │   └── patch-storage.yaml 
│       │       └── prod/
│       │           ├── kustomization.yaml 
│       │           └── patch-storage.yaml 
│       └── helm/
│           └── postgres-infra/
│               ├── Chart.yaml            
│               ├── values-dev.yaml       
│               ├── values-prod.yaml      
│               └── templates/
│                   ├── statefulset.yaml
│                   ├── service.yaml
│                   └── secret.yaml
└── application/
    └── k8s/
        ├── kustomization/
        │   ├── base/
        │   │   ├── kustomization.yaml    
        │   │   ├── backend.yaml          
        │   │   ├── frontend.yaml         
        │   │   ├── configmap.yaml        
        │   │   └── ingress.yaml          
        │   └── overlays/
        │       ├── dev/
        │       │   ├── kustomization.yaml 
        │       │   └── secret.yaml       
        │       └── prod/
        │           ├── kustomization.yaml 
        │           └── secret.yaml       
        └── helm/
            └── wishlist-app/
                ├── Chart.yaml          
                ├── values.yaml          
                ├── values-dev.yaml       
                ├── values-prod.yaml     
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