# Codema Data Explorer

A [datasette](https://datasette.io) web application to enable exploration of:

- Residential Buildings
    - Building Energy Ratings (BER) @ Small Area Level [05/2021] - `closed-access`
    - + Census [2016]
    - + Archetypes (typical buildings for zone pulled from BERs)

- Commercial Buildings
    - Valuation Office Floor Areas - `closed-access`
    - + CIBSE Guide F - `closed-access`
    - + CIBSE TM46 - `closed-access`

## Setup

Install:

```bash
pip install datasette datasette-auth-passwords
```

Run locally:

```bash
USER_PASSWORD_HASH='pbkdf2_sha256$260000$...' datasette -m metadata.yaml buildings.db
```

Publish to heroku:

```bash
datasette publish heroku \
    -m metadata.yaml \
    -n codema-data-explorer \
    --install datasette-auth-passwords \
    --plugin-secret datasette-auth-passwords user_password_hash 'pbkdf2_sha256$...' \
    buildings.db 
```