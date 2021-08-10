# Quickstart

In this page, we will show you how to initialize [[ds-stack](https://github.com/DougTrajano/ds-stack)]{A data science docker compose with machine learning tools|top-right} and start using it.

## Prerequisites

- [Docker](https://www.docker.com/products/docker-desktop)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Clone the repository

In your local machine, clone the repository:

```bash
git clone https://github.com/DougTrajano/ds-stack
```

Open the directory:

```bash
cd ds-stack
```

## Start the stack

Customize your environment variables in the `.env` file.

```properties
# MLflow server
MLFLOW_PORT=5000


# Backend store
MLFLOW_DB_USERNAME=mlflow
MLFLOW_DB_PASSWORD=mlflow
MLFLOW_DB_DATABASE=mlflow
MLFLOW_DB_PORT=5432


# Artifact store
MINIO_ACCESS_KEY=minio
MINIO_SECRET_KEY=minio123


# JupyterLab
JUPYTERLAB_PORT=8888
JUPYTERLAB_TOKEN=''
JUPYTERLAB_PASSWORD=''
```

Finally, start the stack:

```bash
docker-compose up
```

You can now access the following endpoints:

| Endpoint | Description |
| - | - |
| [http://localhost:8888/](http://localhost:8888/) | JupyterLab |
| [http://localhost:5000/](http://localhost:5000/) | MLflow UI |