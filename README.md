# uplift-calculators
Micro-home build planning tools

## Hosting

Served at **https://systems.uplift.us** from `atx-srv-01` — stock nginx with
this repo bind-mounted, behind the company Traefik proxy (see
`docker-compose.yml` and the company-infra repo).

**Deploys are automatic:** a user systemd timer on `atx-srv-01`
(`deploy/systems-site-sync.timer`) polls GitHub every minute and
hard-resets the server checkout to `origin/main` — push to main and the
site updates within ~60s. Corollary: never hand-edit the checkout on the
server; uncommitted tracked changes there are discarded by the next sync.
