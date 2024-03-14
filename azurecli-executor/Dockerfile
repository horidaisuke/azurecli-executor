FROM library/docker:19.03.15
ENV AZURE_CLI_VERSION 2.58.0
RUN apk update \
 && apk add --no-cache \
    bash \
    curl \
    py3-pip \
 && apk add --virtual .build-deps \
    cargo \
    gcc \
    libffi-dev \
    make \
    musl-dev \
    openssl-dev \
    python3-dev \
 && pip3 install --upgrade pip \
 && pip3 install azure-cli==${AZURE_CLI_VERSION} \
 && apk del .build-deps \
 && rm -rf /var/cache/apk/*
