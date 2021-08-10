# Data Science stack

This project contains a [Docker Compose](https://docs.docker.com/compose/) that deploys machine learning tools that you will love to work with! <3

| JupyterLab | MLFlow Server |
| - | - |
| ![](docs/images/JupyterLab.png) | ![](docs/images/mlflow.png) |
|| [Postgres](https://www.postgresql.org/) as backend store \| [Minio](https://min.io/) as artifact store |


## Project setup

### Environment variables

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

## Next features

Add optional [profiles](https://docs.docker.com/compose/profiles/) with more tools such as:

- [Airflow](https://airflow.apache.org/) - Develop, schedule, and monitor workflows
- [Redash](https://redash.io/) - Visualization tool
- [Postgres](https://www.postgresql.org/) - Relational Database
- [Feast](https://feast.dev/) - Feature Store
  
So you can up your stack with optional tools using the same docker-compose.yml file.

```bash
docker-compose --profile airflow --profile feast up
```

The result of this command will launch JupyterLab, MLFlow Server (with its postgres and minio), Kubeflow and Redash.