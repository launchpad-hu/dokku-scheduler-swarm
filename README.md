# dokku-swarm

A dokku plugin to deploy Docker Swarm stacks.

## Installation

```shell
dokku plugin:install https://github.com/launchpad-hu/dokku-scheduler-swarm.git
```

## Usage

1. Add a `docker-compose.yml` to the root of your repo.
2. Set the scheduler to `swarm`

```shell
dokku scheduler:set myapp selected swarm
```

3. push to Dokku

## Limitations

Currently does not work together with builders.

## License

MIT
