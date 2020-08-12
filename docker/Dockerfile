FROM ubuntu:18.04

ARG release=v3.00

# Install required packages
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y \
    transmission-daemon && \
    service transmission-daemon stop && \
    cp -R /etc/transmission-daemon / && \
    mv /transmission-daemon /transmission && \
    chmod -R 777 /transmission && \
    rm -rf /var/lib/apt/lists/*

COPY ["settings.json", "done.sh", "/transmission/"]

RUN mkdir /watch && mkdir /incomplete && mkdir /download && \
    chmod -R 777 /watch && chmod -R 777 /incomplete && chmod -R 777 /download

#      rpc-port   peer-port
EXPOSE 9091       51413

VOLUME ["/transmission", "/watch", "/incomplete", "/download"]

RUN /usr/bin/transmission-daemon -f --config-dir /transmission
