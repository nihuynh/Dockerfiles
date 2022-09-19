FROM debian:latest
LABEL maintainer="nihuynh@student.42.fr"
EXPOSE 34197/udp
ENV FACTORIO_VERSION 1.1.69
WORKDIR /opt
RUN apt-get update && apt-get dist-upgrade -y && \
    apt-get install -y wget tar gzip xz-utils && \
    wget --no-check-certificate -O ./factorio.tar.gz https://www.factorio.com/get-download/`echo $FACTORIO_VERSION`/headless/linux64 && \
    tar xvf ./factorio.tar.gz && \
    rm -rf ./factorio.tar.gz
COPY server-settings.json /opt/factorio/data