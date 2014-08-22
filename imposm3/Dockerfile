# Docker image for Imposm3
# To build, run docker build --rm --tag=jmarin/imposm3
# A container with a shell including Imposm3 can be started by running docker run -t- i jmarin/imposm3

FROM centos:centos7
MAINTAINER Juan Marin Otero <juan.marin.otero@gmail.com>

RUN yum -y update; yum clean all
RUN yum -y install git mercurial snappy boost-devel gcc gcc-c++ flex wget protobuf protobuf-devel; yum clean all

WORKDIR /tmp
RUN wget http://dl.fedoraproject.org/pub/epel/beta/7/x86_64/epel-release-7-0.2.noarch.rpm 
RUN rpm -ivh epel-release-7-0.2.noarch.rpm
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
 

CMD ["/bin/bash"]
