# Effective Mobile — DevOps Test Assignment

## Запуск

```bash
git clone https://github.com/DidandKO/eff_mobile.git && cd eff_mobile
docker compose up --build -d
```

## Проверка

```bash
curl http://localhost
# Hello from Effective Mobile!
```

## Остановка

```bash
docker compose down
```

## Архитектура

```
User → nginx:80 (em-nginx) → backend:8080 (em-backend)
```

nginx принимает HTTP-запросы на порту 80 и проксирует их на бэкенд.  
Бэкенд (Python `http.server`) отвечает текстом `Hello from Effective Mobile!`.  
Порт бэкенда не публикуется наружу — обмен только внутри docker-сети `em-network`.

## Технологии

- Python 3.12-alpine — бэкенд
- nginx 1.27-alpine — reverse proxy
- Docker Compose 3.9
