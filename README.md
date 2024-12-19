# PearceBin (from Mystbin)

Easily share code and text.

This is a fork of Mystbin with some changes to the frontend and backend made by Aiden Pearce.
If you are looking for the original/true MystBin, you can find it [here](https://github.com/PythonistaGuild/MystBin).

[Website](https://bin.aidenpearce.space)

[API Documentation](https://bin.aidenpearce.space/api/documentation)


### Running without Docker
**Requirements:**
- Postgres

**Setup:**
- Clone
- Copy `config.template.toml` into `config.toml`
 - Set Database connection DSN.
 - Optionally set URLs to a running Redis Instance.
- ! If you haven't already: Create a Database in `postgres` (Default `mystbin`)
- Install dependencies (Preferably to a `venv`): `pip install -Ur requirements.txt`
- Optionally in `core/server.py` set `ignore_localhost=` to `False` in the RateLimit Middleware for testing.
- Run: `python launcher.py`

### Running with Docker
**Requirements**
- Docker
- Docker Compose

**Setup:**
- Clone
- Copy `config.template.toml` into `config.toml`
  - The default config for database (and redis) should work Out of Box.
- Optionally in `core/server.py` set `ignore_localhost=` to `False` in the RateLimit Middleware for testing.
- Run `docker compose up -d` to start the services.
  - If you want to use redis for session/limit handling, run with the redis profile: `docker compose --profile redis up -d`
  - The redis container doesn't expose connections outside of the network, but for added security edit `redis.conf` and change the password.
