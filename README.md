# Photon Docker

Run [https://github.com/komoot/photon/releases/download/0.3.4/photon-0.3.4.jar](https://github.com/komoot/photon/releases/download/0.3.4/photon-0.3.4.jar) 0.3.4 in a docker container.

Uses openjdk:8-jdk-alpine. Requires a running nominatim for data import. It is built to work together with https://registry.hub.docker.com/u/helvalius/nominatim-docker-development/ . The embedded ES database is not exposed as volumes and thus data is removed if container is removed.


# Building

To rebuild the image locally execute

```
docker build -t photon .
```

# Running

By default the container exposes port `2322` as web port, links nominatim.

 To run the container execute

```
docker run -p 2322:2322  --link nominatim_container:nominatim -ti photon

```

Connect to the  webserver with curl. If this succeeds, open [http://localhost:2322/](http:/localhost:2322) in a web browser

```
curl "http://localhost:2322/api?q=berlin"
```
