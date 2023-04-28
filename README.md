# dokku-swarm

A dokku plugin to deploy Docker Swarm stacks.

## Installation

```shell
dokku plugin:install https://github.com/launchpad-hu/dokku-swarm.git
```

The recommended way is to set these globally, but you can choose to set them per application:

```shell
dokku scheduler:set --global selected swarm
```

If you are building your own images, you need a registry to distribute the built image to the
other nodes. Deploy a registry on the node where dokku is running, and configure Dokku to
push the images to the registry:

```shell
docker run --name registry -d --restart=unless-stopped -p 127.0.0.1:5000:5000 registry:2
dokku registry:set --global server 127.0.0.1:5000
dokku registry:set --global push-on-release true
```

## Usage

1. Add a `docker-compose.yml` to the root of your repo.
2. Set the scheduler to `swarm`

```shell
dokku scheduler:set myapp selected swarm
```

3. push to Dokku

## Configuration

All config variables set with `dokku:config` are available in the compose file as substitutions.

```
dokku config:set myapp DOMAIN=example.com
```

```
    labels:
      - "traefik.http.routers.portainer.rule=Host(`${DOMAIN}`)"
```

## Roadmap

- [ ] support for dokku-managed domains
- [ ] support for horizontal scaling
- [ ] support for building the app from the repo
- [ ] support for traefik

## Changelog

### 1.2.0

- push the tag `$IMAGE_TAG` to the registry

### 1.1.0

- provide `$IMAGE_TAG` for compose file

### 1.0.0

- implement support for config vars

## License

MIT
