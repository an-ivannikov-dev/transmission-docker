# Build `ivannikovdev/transmission` Docker image
> https://hub.docker.com/r/ivannikovdev/transmission

```bash
VERSION=v3.00

docker build --no-cache --tag ivannikovdev/transmission:temp .
docker tag ivannikovdev/transmission:temp ivannikovdev/transmission:$VERSION
docker tag ivannikovdev/transmission:temp ivannikovdev/transmission:latest
docker push ivannikovdev/transmission:$VERSION
docker push ivannikovdev/transmission:latest
```


## Examples
```bash
docker run --rm \
  --name transmission \
  --volume "$PWD/data/transmission/transmission-daemon:/transmission" \
  --volume "$PWD/settings.json:/transmission/settings.json" \
  --volume "$PWD/done.sh:/transmission/done.sh" \
  --volume "$PWD/data/transmission/watch:/watch" \
  --volume "$PWD/data/transmission/incomplete:/incomplete" \
  --volume "$PWD/data/transmission/download:/download" \
  ivannikovdev/transmissiont:latest \
  /bin/bash -c "/usr/bin/transmission-daemon -f --config-dir /transmission"
```
