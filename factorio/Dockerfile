# docker build . -t factorio_headless
# docker run -ti -p 34197:34197/udp -v $(pwd)/saves:/opt/factorio/saves --restart=always factorio_headless
# ip for factorio : 192.168.99.100:34197
FROM debian:latest
LABEL maintainer="nihuynh@student.42.fr"
EXPOSE 34197/udp
ENV FACTORIO_VERSION 0.16.51
WORKDIR /opt
RUN apt-get update && apt-get dist-upgrade -y && \
    apt-get install -y wget tar gzip xz-utils && \
    wget --no-check-certificate -O ./factorio.tar.gz https://www.factorio.com/get-download/`echo $FACTORIO_VERSION`/headless/linux64 && \
    tar xvf ./factorio.tar.gz && \
    rm -rf ./factorio.tar.gz
WORKDIR factorio
COPY server-settings.json data
CMD ./bin/x64/factorio --port 34197 --start-server-load-latest --server-settings ./data/server-settings.json