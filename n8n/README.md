# n8n - Docker Compose example

In this example, we will set up [n8n](https://n8n.io/) with a PostgreSQL database using [Docker Compose](https://docs.docker.com/compose/).

- [Prerequisites](#prerequisites)
- [Services](#services)
- [Project Setup](#project-setup)
   - [Environment variables](#environment-variables)
   - [Docker Compose up](#docker-compose-up)
- [Known issues](#known-issues)
- [Related Links](#related-links)

## Prerequisites

- [Docker](https://www.docker.com/products/docker-desktop)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Services

### [n8n](https://n8n.io/)

n8n is a fair-code workflow automation platform with a visual editor, 400+ integrations and native AI capabilities. The editor is available at [http://localhost:5678](http://localhost:5678).

### [Postgres](https://www.postgresql.org/) - n8n Database

PostgreSQL stores workflows, credentials and execution data (instead of the default SQLite).

## Project setup

### Environment variables

You can set the following [environment variables](https://docs.docker.com/compose/environment-variables/) to customize this [Docker Compose](https://docs.docker.com/compose/).

| Variable name  |  Description  | Default value |
| - | - | - |
| POSTGRES_DB | Database name | `"n8n"` |
| POSTGRES_USER | Database user | `"n8n"` |
| POSTGRES_PASSWORD | Database password | `"n8n"` |
| N8N_ENCRYPTION_KEY | Key used to encrypt stored credentials | `"change-me-n8n-encryption-key"` |
| N8N_HOST | Host name n8n is reachable at | `"localhost"` |
| N8N_PROTOCOL | Protocol n8n is reachable at | `"http"` |
| N8N_SECURE_COOKIE | Require HTTPS for the session cookie | `"false"` |
| WEBHOOK_URL | Public URL used to build webhook URLs | `"http://localhost:5678/"` |
| GENERIC_TIMEZONE | Timezone for schedule triggers | `"UTC"` |

The best way to do this is to add them to a `.env` file in the same directory as `docker-compose.yml`.

<details><summary>.env</summary>
<p>

```properties
POSTGRES_DB=n8n
POSTGRES_USER=n8n
POSTGRES_PASSWORD=change-me
N8N_ENCRYPTION_KEY=change-me-too
GENERIC_TIMEZONE=America/Sao_Paulo
```

</p>
</details>

> The defaults are for local testing only. Set your own `POSTGRES_PASSWORD` and `N8N_ENCRYPTION_KEY` before exposing n8n anywhere else. The encryption key must stay the same for the lifetime of the data volume, otherwise stored credentials can no longer be decrypted.

### Docker Compose up

To run all the required services, execute the following command:

```bash
docker compose up
```

Then open [http://localhost:5678](http://localhost:5678) and create the owner account on first access.

## Known issues

- `N8N_SECURE_COOKIE` is `false` so you can log in over plain HTTP on localhost. Put n8n behind HTTPS and set it to `true` for anything beyond local use.

## Related Links

- [n8n | Docker installation](https://docs.n8n.io/hosting/installation/docker/)
- [n8n | Environment variables](https://docs.n8n.io/hosting/configuration/environment-variables/)
