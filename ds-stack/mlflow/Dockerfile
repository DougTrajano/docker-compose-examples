FROM python:3.8-slim

ARG MLFLOW_PORT=5000
ARG MLFLOW_DB_DIALECT=postgresql
ARG MLFLOW_DB_USERNAME=mlflow
ARG MLFLOW_DB_PASSWORD=mlflow
ARG MLFLOW_DB_DATABASE=mlflow
ARG MLFLOW_DB_HOST=mlflow-backend
ARG MLFLOW_DB_PORT=5432

# Create app directory
RUN mkdir /app
WORKDIR /app
COPY . /app/

# Update packages
RUN apt-get update -y \
    && apt-get upgrade -y

# Install pip then packages
RUN pip install --upgrade pip \
    && pip install -r requirements.txt --upgrade

EXPOSE ${MLFLOW_PORT}

CMD mlflow server \
    --host 0.0.0.0 \
    --port ${MLFLOW_PORT} \
    --default-artifact-root ${MLFLOW_S3_ENDPOINT_URL} \
    --backend-store-uri ${MLFLOW_DB_DIALECT}://${MLFLOW_DB_USERNAME}:${MLFLOW_DB_PASSWORD}@${MLFLOW_DB_HOST}:${MLFLOW_DB_PORT}/${MLFLOW_DB_DATABASE}
    