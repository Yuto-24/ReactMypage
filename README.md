# README

## Dockerfile

you need to change

- services.hp_react.build.args.REACT_APP_DIR_NAME
- services.hp_react.volumes.source

## ONLY first time

it might take few minutes

```bash
# docker compose run --rm [service name] sh -c 'yarn create react-app [app name] --template typescript'
docker compose run --rm react sh -c 'yarn create react-app my_page --template typescript'
```

Run for developing

```bash
docker compose up -d --build --force-recreate --remove-orphans && docker com
pose logs -f
```
