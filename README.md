# tailscale-relay

This is a docker image based on `alpine:3.12` for setting up a [tailscale](https://tailscale.com) instance in relay mode.

## Prerequisites

- Defined docker network via `docker network create -d bridge <network name>`
- Subnet prefix of network via `docker inspect <NETWORK ID> | grep Subnet`
- Auth key from https://login.tailscale.com/admin/authkeys (e.g. `tskey-123abc...`)

## Requirements

- `--cap-add=NET_ADMIN`
- `--device=/dev/net/tun`

## Use

```bash
docker run -d \
    --cap-add=NET_ADMIN \
    --device=/dev/net/tun \
    --network=<docker_net> \
    -e "ROUTES=<docker_net_prefix>" \
    -e "AUTHKEY=<your_auth_key>" \
    xumr0x/tailscale-relay:latest
```

Find this image on [Docker Hub](https://hub.docker.com/r/xumr0x/tailscale-relay)
