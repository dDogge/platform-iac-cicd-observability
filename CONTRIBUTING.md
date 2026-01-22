# Contributing

Thanks for contributing to **platform-iac-cicd-observability**!

This repository wires services together for local development (docker-compose) and evolves toward IaC (Terraform) and observability (Prometheus/Grafana/Loki).

## Changelog and decisions (required)
- **Update `CHANGELOG.md` on every push** (at minimum the `Unreleased` section).
- For major decisions (stack components, ports, provisioning strategy, IaC layout), **add/update an ADR** in `docs/decisions/`.

## Prerequisites
- Docker + Docker Compose v2
- (Optional, later) Terraform

## Local development
```bash
cp .env.example .env
docker compose config
docker compose up -d
docker compose ps
docker compose logs -f
```

## Suggested structure
- `compose/` — compose files (optional; root compose also ok)
- `monitoring/` — Prometheus config, Grafana provisioning/dashboards
- `terraform/` — Terraform code (later)

## Terraform conventions (when added)
- Do not commit state files (`*.tfstate`).
- Always format:
```bash
terraform fmt -recursive
```
- Validate (after init):
```bash
terraform init -backend=false
terraform validate
```

## Observability conventions
- Keep Prometheus scrape configs minimal and readable.
- Prefer provisioning Grafana datasources/dashboards under version control.
- Document ports and access points in README.

## CI expectations
CI should remain fast:
- docker compose config validation
- terraform fmt/validate when terraform exists
- basic repo sanity checks

## Commit message guidelines
Use clear, imperative messages:
- "Add Prometheus scrape config for ingest API"
- "Provision Grafana datasource"
- "Add compose service for analytics"

## Pull requests
- Include summary + how to test locally.
- Keep changes scoped (compose vs monitoring vs terraform when possible).
- Update docs/architecture.md if wiring or data flow changes.
