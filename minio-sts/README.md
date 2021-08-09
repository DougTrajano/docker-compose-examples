# Minio STS - Docker Compose example

In this example, we will set up a MinIO Gateway S3 with STS using [Docker Compose](https://docs.docker.com/compose/).

## Components

### [MinIO Server](https://min.io/) - S3 Gateway

MinIO is a High Performance Object Storage released under Apache License v2.0. It is API compatible with Amazon S3 cloud storage service. Use MinIO to build high performance infrastructure for machine learning, analytics and application data workloads.

### [Etcd](https://coreos.com/etcd/) 

etcd is a distributed key-value store designed to securely store data across a cluster. etcd is widely used in production on account of its reliability, fault-tolerance and ease of use.

### [Keycloak](https://www.keycloak.org/)

Keycloak is an Open Source Identity and Access Management solution for modern Applications and Services.

### [Postgres](https://www.postgresql.org/) - Keycloak Database

PostgreSQL is a powerful, open source object-relational database.

### [MinIO Console](https://github.com/minio/console)

A graphical user interface for [MinIO](https://github.com/minio/minio)

## Keycloak integration setup

You need to make some changes to the Keycloak Realm in order to use MinIO.

I'll describe it later. :)

## Known issues

- As Keycloak takes a long time to start up, you may need to restart the Minio's container after Keycloak is ready.

## Related Links

- [MinIO | Learn how to deploy MinIO with Amazon S3](https://docs.min.io/docs/minio-gateway-for-s3.html)
- [MinIO | Learn how to configure MinIO for Security Token Service](https://docs.min.io/docs/minio-sts-quickstart-guide.html)