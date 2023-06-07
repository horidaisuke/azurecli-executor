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
```

## Tags

Tags name is made from join of [simple tags of docker](https://hub.docker.com/_/docker) and [tags of azure-cli](https://github.com/Azure/azure-cli/tags).

* `23.0.6-azurecli-2.49.0`, `latest`

## License

View [license information](https://github.com/horidaisuke/azurecli-executor/blob/main/LICENSE) for the software contained in this image.

This license is inherited or included from licenses of [library/docker](https://hub.docker.com/_/docker) and [azure-cli](https://github.com/Azure/azure-cli/blob/main/LICENSE).
