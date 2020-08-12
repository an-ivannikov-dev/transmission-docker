FROM ubuntu:18.04

ARG release=latest

# Install required packages
#    openssl ca-certificates curl wget && \
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y \
    transmission-daemon && \
    service transmission-daemon stop && \
    rm -rf /var/lib/apt/lists/*

COPY ["settings.json", "/etc/transmission-daemon"]

RUN mkdir /watch && mkdir /incomplete && mkdir /downloads && \
    chmod -R 777 /watch && chmod -R 777 /incomplete && chmod -R 777 /download

#      rpc-port   peer-port
EXPOSE 9091       51413

VOLUME ["/etc/transmission-daemonsettings.json", "/watch", "/incomplete", "/download"]

RUN transmission-daemon
