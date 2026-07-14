# GoodJob Docker Wrapper

This repository builds Docker images for upstream GoodJob from Gitee:

- Upstream: https://gitee.com/sendoh-huang/GoodJob
- Backend image: `ghcr.io/flyinsz/goodjob-backend:latest`
- Frontend image: `ghcr.io/flyinsz/goodjob-frontend:latest`

No source fork is modified here. Dockerfiles clone upstream during GitHub Actions builds.

## Build

GitHub Actions -> `Build GoodJob Docker Images` -> Run workflow.

Default upstream ref:

```text
master
```

## Deploy

Copy `docker-compose.yml` and create `.env`:

```env
MYSQL_PASSWORD=change_me
MYSQL_ROOT_PASSWORD=change_root_me
JWT_SECRET=replace_with_at_least_32_random_characters
INITIAL_ADMIN_EMAIL=admin@example.com
INITIAL_ADMIN_PASSWORD=replace_with_a_strong_12_plus_character_password
INITIAL_ADMIN_NAME=Super Admin
CORS_ORIGINS=http://127.0.0.1:8080
SESSION_COOKIE_SECURE=false
ENABLE_API_DOCS=true
```

Start:

```bash
docker compose up -d
```

Open:

```text
http://server-ip:8080
```

Health:

```text
http://server-ip:4188/api/health
```
