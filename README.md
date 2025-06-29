# My Awesome Home Server

Just a personal docker compose that deploys all my personal projects
under one large reverse proxy, with SSL.

## Interface

Exposes:

- HTTP :80 forwarding to :443 with HTTPS
- :8080 for traefik dashboard
    - Only accepts local addresses
- twai.ealovega.dev - Transferwareai senior design project
- ealovega.dev - Primary personal website
- qalert.ealovega.dev - Ride wait time webapp
- mealie.ealovega.dev - Proxy to another local server that hosts a mealie instance

## Setup

1. Clone with submodules
2. Add CloudFlare DNS API token to `./secrets/cf_dns_token.txt` for DNS challenges
3. Add Transferware.ai model assets to `./assets/transferware`
4. Generate qalert PK in `./assets/qalert` with `openssl ecparam -genkey -name prime256v1 -out private_key.pem`
4. Run ``` mkdir lets_encrypt && touch lets_encrypt/acme.json && chmod 600 lets_encrypt/acme.json``` to create the file
   SSL certs will go into.

## Updating

To update a container, just pull the submodule and then delete the image, then restart.