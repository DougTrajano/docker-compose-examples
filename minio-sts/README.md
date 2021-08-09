# Minio STS - Docker Compose example

In this example, we will set up a MinIO Gateway S3 with STS (Security Token Service) using [Docker Compose](https://docs.docker.com/compose/).

## Index

- [Prerequisites](#prerequisites)
- [Environment variables](#environment-variables)
- [How to run](#how-to-run)
- [Services](#services)
- [Keycloak configuration](#keycloak-configuration)
- [Known issues](#known-issues)
- [Related Links](#related-links)

## Prerequisites

- [Docker](https://www.docker.com/products/docker-desktop)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Environment variables

You need to set the following [environment variables](https://docs.docker.com/compose/environment-variables/) to use this [Docker Compose](https://docs.docker.com/compose/).

| Variable name  |  Description  | Default value |
| - | - | - |
| MINIO_ACCESS_KEY | MinIO access key | `"minio"` |
| MINIO_SECRET_KEY | MinIO secret key | `"minio123"` |
| MINIO_ROOT_USER | AWS Access Key | `None` |
| MINIO_ROOT_PASSWORD | AWS Secret Key | `None` |

The best way to do this is to add them to a `.env` file in the same directory as `docker-compose.yml`.

<details><summary>.env</summary>
<p>

```env
MINIO_ACCESS_KEY=minio
MINIO_SECRET_KEY=minio123
MINIO_ROOT_USER=YOUR-AWS-ACCESS-KEY
MINIO_ROOT_PASSWORD=YOUR-AWS-SECRET-KEY
```

</p>
</details>

## How to run

To run all the required services, execute the following command:

```bash
docker-compose up
```

[MinIO Console](#minio-console) is an optional service. To run the stack with it, execute the following command:

```bash
docker-compose --profile console up
```

## Services

### [MinIO Server](https://min.io/) - S3 Gateway

MinIO is a High Performance Object Storage released under Apache License v2.0. It is API compatible with Amazon S3 cloud storage service. Use MinIO to build high performance infrastructure for machine learning, analytics and application data workloads.

### [Etcd](https://coreos.com/etcd/) 

etcd is a distributed key-value store designed to securely store data across a cluster. etcd is widely used in production on account of its reliability, fault-tolerance and ease of use.

### [Keycloak](https://www.keycloak.org/)

Keycloak is an Open Source Identity and Access Management solution for modern Applications and Services.

### [Postgres](https://www.postgresql.org/) - Keycloak Database

PostgreSQL is a powerful, open source object-relational database.

### [MinIO Console](https://github.com/minio/console) - Optional

A graphical user interface for [MinIO](https://github.com/minio/minio).

## Keycloak configuration

You need to make some changes to the Keycloak Realm in order to use MinIO.

- Navigate to the Keycloak UI: [http://localhost:8080/auth/](http://localhost:8080/auth/).
- In the left menu, click on **Clients**.
   - Click on **Edit** for account client.
   - Turn on **Implicit Flow Enabled**.
   - Add "*" to the **Valid Redirect URIs** field.
   - Click on **Save**.
- Also in the account client, click on **Mappers**.
   - Click on **Create**.
   - Fill in the **Name** field with "policy".
   - Change the **Mapper Type** to "User Attribute".
   - Fill in the "User Attribute" field with "policy".
   - Fill in the "Token Claim Name" field with "policy".
   - Click on **Save**.
- In the left menu, click on **Users**.
   - Click on **View all users**.
   - Click on **Edit** for user "admin".
   - Go to **Attributes** tab.
   - Fill in the **Key** field with "policy" and **Value** field with "readwrite".
   - Click on **Add** and then **Save**.

Right now, you should be able to log in to MinIO using the policies that you created in Keycloak.

There's a lot more configuration that you can do. Please refer to the [related links](#related-links) for more information.

## Known issues

- As Keycloak takes a long time to start up, you may need to restart the MinIO container after Keycloak is ready.

## Related Links

- [MinIO | Learn how to deploy MinIO with Amazon S3](https://docs.min.io/docs/minio-gateway-for-s3.html)
- [MinIO | Learn how to configure MinIO for Security Token Service](https://docs.min.io/docs/minio-sts-quickstart-guide.html)