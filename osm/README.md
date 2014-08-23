OSM docker
==========

OSM utilities [Docker](https://docker.io) image

For more information about the software included, see [Imposm3](https://github.com/omniscale/imposm3) and [Osmosis](https://github.com/openstreetmap/osmosis)

To build the Docker image, run the following:

```bash
docker build --rm --tag=jmarin/osm
```

To start a container from this image, run the following:

```bash
docker run -t -i --rm jmarin/osm /bin/bash
```
