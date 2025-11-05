# AGENTS: Homelab Repo Guidance

- Build/Test
- - Validate compose: `docker compose config` (fail fast on YAML).
- - Start all: `docker compose up -d`; stop: `docker compose down`.
- - Single service test: `docker compose up -d <service>`; logs: `docker compose logs -f <service>`.
- - Health check: `docker compose ps`, then hit service ports per README.
- - YAML lint (optional): `yamllint .`; Markdown: `npx markdownlint-cli2 README.md`.

- Style & Conventions
- - YAML: 2 spaces, no tabs; keys lower-kebab; service names lowercase-hyphen.
- - Compose order: `version`, `networks`, `volumes`, `services`; keep stable key order.
- - Ports as strings `"8080:8080"`; booleans explicit `true/false`; lists indented 2.
- - Env vars UPPER_SNAKE; do not commit secrets; prefer `.env`/Docker secrets.
- - Images: prefer pinned tags (e.g., `:1.2.x`) over `:latest` in prod notes.
- - Volumes: name volumes; avoid anonymous; mount configs `:ro` where possible.
- - Networks: single `homelab` bridge; explicitly attach services.
- - Errors: fail closed (minimal ports), document required env; surface container errors with `restart: unless-stopped` + logs.
- - Docs: keep README authoritative; use fenced code blocks; wrap at ~100 cols.
- - Filenames/dirs: `configs/`, `compose.yaml`, `scripts/` if added; lowercase-hyphen.
- - Types: prefer strings for URLs/ports/timeouts; avoid implicit casting.
- - Cursor/Copilot rules: none present in repo as of now.
