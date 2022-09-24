# docker build . -t factorio_server --build-arg version_factorio=1.1.69
# docker run -ti -p 34197:34197/udp -v $(pwd)/saves:/opt/factorio/saves -v $(pwd)/mods:/opt/factorio/mods --restart=unless-stopped -w /opt/factorio factorio_server ./bin/x64/factorio --port 34197 --start-server-load-latest --server-settings ./data/server-settings.json
FROM debian:latest
LABEL maintainer="nihuynh@student.42.fr"
EXPOSE 34197/udp
ARG version_factorio
ENV FACTORIO_VERSION $version_factorio
WORKDIR /opt
RUN apt-get update && apt-get dist-upgrade -y && \
    apt-get install -y wget tar gzip xz-utils && \
    wget --no-check-certificate -O ./factorio.tar.gz https://www.factorio.com/get-download/`echo $FACTORIO_VERSION`/headless/linux64 && \
    tar xvf ./factorio.tar.gz && \
    rm -rf ./factorio.tar.gz
COPY server-settings.json /opt/factorio/data