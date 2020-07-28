# tailscale-relay

This is a docker image based on `alpine:3.12` for setting up a [tailscale](https://tailscale.com) instance in relay mode.

## Prerequisites

- Defined docker network via `docker network create -d bridge <network name>`
- Subnet network via `docker inspect <NETWORK ID> | grep Subnet`
- Auth key from https://login.tailscale.com/admin/authkeys (e.g. `tskey-123abc...`)

## Requirements

- `--cap-add=NET_ADMIN`
- Volume for persistent storage `/tailscale`

## Use

Run the following `docker run` command.

- `AUTHKEY=tskey-123abc...`
- `ROUTES=172.31.0.0/16`

```bash
docker run -d \
    -v /tailscale \
    --cap-add=NET_ADMIN \
    --network=<docker_net> \
    -e "ROUTES=<docker_network>" \
    -e "AUTHKEY=<your_auth_key>" \
    xumr0x/tailscale-relay:latest
```

Find this image on [Docker Hub](https://hub.docker.com/r/xumr0x/tailscale-relay)
