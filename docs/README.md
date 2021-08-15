# Overview

This project contains a set of examples of using [Docker Compose](https://docs.docker.com/compose/) to deploy a variety of applications.

## Examples

- [DS Stack](examples/ds-stack.md) - JupyterLab + MLflow
- [MinIO STS](examples/minio-sts.md) - MinIO S3 Gateway + Keycloak + MinIO Console + Etcd
- [JaCaMo](examples/jacamo.md) -  Framework for Multi-Agent Programming

## Data Privacy

We are committed to protecting your privacy. We do not collect any data on these examples as the purpose of this project is to demonstrate the use of Docker Compose.

### Docker volumes

These examples use Docker volumes to share data between containers. All Docker volumes are saved to the `/data_*` directory in each stack. The `.gitignore` file in the root of this project contains a pattern that will ignore all directories that inlcude `data_*`.

## License

The project is licensed under the [Apache 2.0 License](../LICENSE).

> The applications used in the examples can have their own license.