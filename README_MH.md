# Running it locally with Cribl Lake direct access

## Create Lake Direct access and update `.env.override` with the details
Update `.env.override` with Lake DA HEC endpoint details:
```shell
# DO NOT PUSH CHANGES OF THIS FILE TO opentelemetry/opentelemetry-demo
# PLACE YOUR .env ENVIRONMENT VARIABLES OVERRIDES IN THIS FILE

# Demo Elastic App version
IMAGE_VERSION=2.0.4
IMAGE_NAME=ghcr.io/elastic/opentelemetry-demo

# *********************
# Elastic Demo Services
# *********************
AD_SERVICE_DOCKERFILE=./src/ad/Dockerfile.elastic
FRAUD_SERVICE_DOCKERFILE=./src/fraud-detection/Dockerfile.elastic
KAFKA_SERVICE_DOCKERFILE=./src/kafka/Dockerfile.elastic

# *********************
# Elastic Collector
# *********************
COLLECTOR_CONTRIB_IMAGE=quay.io/signalfx/splunk-otel-collector:0.134.0
OTEL_COLLECTOR_CONFIG=./src/otel-collector/otelcol-splunk-config.yaml

# Update your DA HEC endpoint details here
SPLUNK_HEC_ENDPOINT="https://xxxxx.cribl.cloud:10080/services/collector"
SPLUNK_HEC_TOKEN="123-123-123-1231-123"
```

## Running it in docker compose
```
docker compose --env-file .env --env-file .env.override up --force-recreate --remove-orphans --detach
```

## Stopping it
```
docker compose down --remove-orphans --volumes
```