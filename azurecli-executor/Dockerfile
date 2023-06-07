FROM library/docker:18.09.9
ENV AZURE_CLI_VERSION 2.49.0
RUN apk update \
 && apk add --no-cache \
    bash \
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
