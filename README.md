# Wish list ToDo
## Структура
<pre>
APP-TODO/
├── backend/                   # Flask бэкенд-сервер
│   ├── app.py                 # Основной файл приложения Flask (роуты API)
│   ├── models.py              # Модели SQLAlchemy для таблицы gifts
│   ├── database.py            # Конфигурация подключения к БД
│   ├── requirements.txt       # Зависимости Python (Flask, SQLAlchemy, psycopg2)
│   ├── .env.example           # Переменные окружения (DATABASE_URL)
│   
├── frontend/                 # Next.js фронтенд-приложение
│   ├── package.json          # Зависимости Node.js и скрипты
│   ├── next.config.js        # Конфигурация Next.js
│   ├── package-lock.json
│   ├── postcss.config.js
│   ├── tailwind.config.js
│   ├── .env.local            # Переменные окружения (NEXT_PUBLIC_API_URL)
│   ├── pages/                # Страницы Next.js
│   │   ├── _app.js           # Главный компонент приложения
│   │   ├── index.js          # Главная страница со списком подарков
│   │   └── api/
│   │       └── gifts.js      # Прокси-роут для API (опционально)
│   ├── components/           # React компоненты
│   │   └── GiftList.js       # Компонент списка подарков (логика и UI)
│   └── styles/               # Стили
│       └── globals.css       # Глобальные CSS стили (Tailwind)
│
└── README.md                 # Эта инструкция
</pre>




## Сборка образов
cd backend
docker build -t backend:latest .
cd ../frontend
docker build -t frontend:latest .
cd ..

## Cоздание манифестов

kubectl apply -f namespace.yaml
kubectl apply -f configmap.yaml
kubectl apply -f secret.yaml
kubectl apply -f postgres-pvc.yaml
kubectl apply -f postgres.yaml
kubectl apply -f backend.yaml
kubectl apply -f frontend.yaml
kubectl apply -f ingress.yaml

## Проверить состояние подов

kubectl get pods -n gift-app -w

## Открытие приложения (открывать в двух разных терминалах)

kubectl port-forward -n gift-app service/frontend-service 3000:3000

kubectl port-forward -n gift-app service/backend-service 5000:5000
