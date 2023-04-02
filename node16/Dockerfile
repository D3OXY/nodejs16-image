FROM node:16.16.0-bullseye-slim

LABEL author="D3OXY" maintainer="deoxy@deoxy.dev"
LABEL org.opencontainers.image.source="https://github.com/D3OXY/nodejs16-image"
LABEL org.opencontainers.image.licenses="MIT"

RUN apt-get update \
    && apt-get -y install --no-install-recommends curl ffmpeg iproute2 git sqlite3 python3 tzdata ca-certificates dnsutils build-essential locales libcairo2-dev libpango1.0-dev libjpeg-dev libgif-dev librsvg2-dev \
    && npm -g install npm@latest \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && useradd -m -d /home/container container \
    && locale-gen en_US.UTF-8

ENV LC_ALL=en_US.UTF-8
ENV LANG=en_US.UTF-8
ENV LANGUAGE=en_US.UTF-8

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ./entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]
