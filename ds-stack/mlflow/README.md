# MLflow Tracking Server

This is a server that can be used to track MLflow runs.

## Environment variables

The MLflow Tracking Server can be configured with the following environment variables:

| Variable | Description | Default |
| - | - | - |
| MLFLOW_PORT | The port that MLflow will be exposed | 5000 |
| MLFLOW_S3_ENDPOINT_URL | The S3 endpoint to use for storing artifacts | `None` |
| MLFLOW_DB_DIALECT | The database dialect to use | `postgresql` |
| MLFLOW_DB_USERNAME | The database username | `mlflow` |
| MLFLOW_DB_PASSWORD | The database password | `mlflow` |
| MLFLOW_DB_DATABASE | The database name | `mlflow` |
| MLFLOW_DB_HOST | The database host | `mlflow-backend` |
| MLFLOW_DB_PORT | The database port | `5432` |
