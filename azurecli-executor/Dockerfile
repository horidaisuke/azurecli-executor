FROM library/docker:25.0.1
ENV AZURE_CLI_VERSION 2.56.0
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh \
 && apk update \
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
 && python3 -m venv venv \
 && source venv/bin/activate \
 && pip install --upgrade pip \
 && pip install azure-cli==${AZURE_CLI_VERSION} \
 && rm -rf /root/.cache/pip \
 && apk del .build-deps \
 && rm -rf /var/cache/apk/*
ENTRYPOINT ["/entrypoint.sh"]