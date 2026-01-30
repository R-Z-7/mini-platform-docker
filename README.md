# Mini Platform Lab (Docker + CI)

A small infrastructure lab demonstrating how to run and support core services on Ubuntu using Docker Compose, with automated validation and smoke tests via GitHub Actions.

## What this includes
- **Nginx** container serving a static page (web service)
- **PostgreSQL** container with persistent storage (database)
- **Docker Compose** for repeatable deployments
- **GitHub Actions (CI)** to validate config and run smoke tests on every push

## Architecture (high level)
Ubuntu host runs Docker → Docker Compose starts:
- `lab_nginx` exposed on `8080`
- `lab_postgres` not exposed publicly (internal only)

## Run locally
```bash
docker-compose up -d
docker ps
curl -I http://localhost:8080

Troubleshooting
	•	Containers: docker ps
	•	Nginx logs: docker logs lab_nginx --tail 50
	•	Postgres logs: docker logs lab_postgres --tail 50
	•	Port check: sudo ss -lntp | grep 8080
