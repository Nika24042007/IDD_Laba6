# PostgreSQL инфраструктура

## Контракт для приложения

Приложение должно подключаться к PostgreSQL, используя следующие параметры:

| Параметр          | Значение                                                     |
|-------------------|--------------------------------------------------------------|
| Хост (DNS)        | `postgres-0.postgres-headless.gift-app.svc.cluster.local` |
| Порт              | 5432                                                         |
| Имя БД            | `giftdb`                                                     |
| Пользователь      | `giftuser`                                                   |
| Пароль            | Хранится в Secret `postgres-secret` (ключ `POSTGRES_PASSWORD`) в том же namespace, что и БД. |

**Строка подключения (DATABASE_URL):**

## Установка инфраструктуры

### Через Kustomize (dev окружение)
```bash
cd infrastructure/postgres/kustomize/overlays/dev
kubectl apply -k .