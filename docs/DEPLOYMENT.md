# Deployment

## Local

Create a virtual environment, install `requirements.txt`, set `REDTEAM_ALLOWED_HOSTS` to the exact authorized target hosts, then run:

```sh
uvicorn app.main:app --host 127.0.0.1 --port 8000
```

The host allowlist is mandatory; an empty allowlist rejects every campaign. HTTP is accepted only for localhost addresses. Set the optional `REDTEAM_REPORT_DIR` to a protected local directory.

## Docker Compose

```sh
export REDTEAM_ALLOWED_HOSTS=agent.example.internal
docker compose up --build
```

The published API binds to `127.0.0.1:8081`. Keep the target bearer token in the campaign request from a secret-aware client; do not save it in the repo or shell history. Reports are mounted at `./reports`.

## Production requirements

Before exposing the API, add operator authentication and authorization, campaign-level rate limits, a managed secret path, report retention/deletion, audit events, egress controls, and a reviewed probe approval workflow. The process-local concurrency limit does not coordinate multiple replicas.
