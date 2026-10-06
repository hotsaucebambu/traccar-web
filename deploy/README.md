# JTrack deployment

This deployment runs the customized Traccar web build with Traccar Server and
MySQL. It joins the existing `wg-easy_wg` Docker network so the shared Caddy
instance can proxy `track.jtrack.co.uk` to `traccar:8082`.

The Teltonika protocol is published publicly on port 5027 over TCP and UDP. No
other device protocol ports are exposed.

The production frontend is built from the repository root with:

```shell
npm ci
npm run build
```

Copy the resulting `build` directory to `/opt/traccar/web`, create a server-only
`.env` from `.env.example`, and start the stack from `/opt/traccar`:

```shell
docker compose up -d
```
