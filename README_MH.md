# Running it locally with Cribl Lake direct access

## Running it in docker compose
```
docker compose --env-file .env --env-file .env.override up --force-recreate --remove-orphans --detach
```

## Stopping it
```
docker compose down --remove-orphans --volumes
```