# `ivannikovdev/transmission` Docker image
> [https://hub.docker.com/r/ivannikovdev/transmission](https://hub.docker.com/r/ivannikovdev/transmission)

## Transmission
  - [https://transmissionbt.com/](https://transmissionbt.com/).
  - [https://github.com/transmission/transmission](https://github.com/transmission/transmission).


## Examples
```bash
docker run --rm \
  --name transmission \
  --volume "$PWD/data/transmission/transmission:/transmission" \
  --volume "$PWD/settings.json:/transmission/settings.json" \
  --volume "$PWD/done.sh:/transmission/done.sh" \
  --volume "$PWD/data/transmission/watch:/watch" \
  --volume "$PWD/data/transmission/incomplete:/incomplete" \
  --volume "$PWD/data/transmission/download:/download" \
  ivannikovdev/transmission:latest \
  /bin/bash -c "/usr/bin/transmission-daemon -f --config-dir /transmission"
```

> Copy the *.torrent file to the 'data/transmission/watch' folder which is mounted to the '/watch' folder inside the docker container.
