FROM        --platform=$TARGETOS/$TARGETARCH debian:bullseye-slim

LABEL       author="Harumi" maintainer="ntncar311@gmail.com"

ENV     DEBIAN_FRONTEND noninteractive

## Update base packages
SHELL        ["/bin/bash","-c"]
RUN          apt update \
             && apt upgrade -y
RUN          apt install -y curl lsof ca-certificates openssl git tar sqlite3 fontconfig tzdata iproute2 libfreetype6 zip unzip curl
## Install dependencies

##Install graalVM
RUN         curl -s "https://get.sdkman.io" | bash
RUN         source $HOME/.sdkman/bin/sdkman-init.sh && sdk install java 17.0.9-graal
RUN		useradd -d /home/container -m container
USER    container
ENV     USER=container HOME=/home/container
WORKDIR /home/container

COPY    ../entrypoint.sh /entrypoint.sh
CMD     ["/bin/bash", "/entrypoint.sh"]
