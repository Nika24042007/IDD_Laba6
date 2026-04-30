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

kubectl create namespace gift-app
cd infrastructure/postgres/kustomize/overlays/dev
kubectl apply -k .

kubectl get pods -n gift-app -w

### Kustomization

cd application/k8s/kustomization/overlays/dev
kubectl apply -k .

### Helm

cd application/k8s/helm/app
helm upgrade --install wishlist-app . \
  --namespace gift-app \
  -f values-dev.yaml \
  --set database.password=mysecretpassword

## Проверка(в разных терминалах)
kubectl port-forward -n gift-app service/frontend-service 3000:3000

kubectl port-forward -n gift-app service/backend-service 5000:5000