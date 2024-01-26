# azurecli-executor

Circleci executor installed azure cli

## Usage

Define executor in `.circleci/config.yml` like this:

```yaml
executors:
  azurecli-executor:
    docker:
      - image: horidaisuke/azurecli-executor:latest
    shell: /bin/bash -leo pipefail
    environment:
      - BASH_ENV: /etc/profile

# Use orbs command directly in azurecli-executor executor
orbs:
  azure-acr: circleci/azure-acr@0.2.1
jobs:
  docker-push-example:
    executor:
      name: azurecli-executor
    steps:
      - run:
          command: |
            echo 'export ARM_SUBSCRIPTION_ID="${SUBSCRIPTION_ID}"' >> $BASH_ENV
            echo 'export AZURE_SP_TENANT="${TENANT_ID}"' >> $BASH_ENV
            echo 'export AZURE_SP="${SERVICE_PRINCIPAL_APPLICATION_ID}"' >> $BASH_ENV
            echo 'export AZURE_SP_PASSWORD="${SERVICE_PRINCIPAL_CLIENT_SECRET}"' >> $BASH_ENV
      - azure-acr/build-and-push-image:
          login-server-name: example.azurecr.io
          registry-name: example
          tag: latest
          repo: something
```

## Tags

Tags name is made from join of [simple tags of docker](https://hub.docker.com/_/docker) and [tags of azure-cli](https://github.com/Azure/azure-cli/tags).

* `24.0.7-azurecli-2.56.0`, `latest`

## License

View [license information](https://github.com/horidaisuke/azurecli-executor/blob/main/LICENSE) for the software contained in this image.

This license is inherited or included from licenses of [library/docker](https://hub.docker.com/_/docker) and [azure-cli](https://github.com/Azure/azure-cli/blob/main/LICENSE).
