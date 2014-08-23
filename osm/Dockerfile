# Docker image for updating OSM
# To build, run docker build --rm --tag=jmarin/osm
# A container with a shell including Imposm3 and Osmosis can be started by running docker run -t -i jmarin/osm /bin/bash

FROM jmarin/jdk8:centos7
MAINTAINER Juan Marin Otero <juan.marin.otero@gmail.com>

RUN yum -y install tar git mercurial snappy boost-devel gcc gcc-c++ flex protobuf protobuf-devel; yum clean all

WORKDIR /tmp
RUN yum -y install golang leveldb leveldb-devel geos geos-devel; yum clean all

ENV GOPATH /usr
ENV PATH $PATH:$GOPATH/bin

# Install GO support for LevelDB, SQLite, Protocol Buffers and PostgreSQL
RUN go get github.com/jmhodges/levigo
RUN go get github.com/mattn/go-sqlite3
RUN go get code.google.com/p/goprotobuf/{proto,protoc-gen-go}
RUN go get github.com/lib/pq

# Install Imposm3
RUN mkdir /opt/imposm
WORKDIR /opt/imposm
RUN git clone https://github.com/omniscale/imposm3 src/imposm3
ENV GOPATH /opt/imposm
RUN go get imposm3
RUN go install imposm3
ENV PATH $PATH:/opt/imposm/bin

# Install Osmosis
RUN mkdir /opt/osmosis
WORKDIR /opt/osmosis
RUN wget http://bretth.dev.openstreetmap.org/osmosis-build/osmosis-latest.tgz
RUN tar zxvf osmosis-latest.tgz
RUN chmod a+x bin/osmosis
ENV PATH $PATH:/opt/osmosis/bin

CMD ["supervisord", "-c", "/etc/supervisor/supervisor.conf"]
