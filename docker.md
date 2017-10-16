# Using custom Docker registry

# Overriding security settings for non-SSL Docker registries

Our Docker registry is at `devartifactory.domain.lan:6050`. Unfortunately, we don't have a legitimate SSL certificate configured yet. We need to bypass our Docker client's security check.

Edit `/etc/docker/daemon.json` and add/create an `insecure-registries` entry containing `devartifactory.domain.lan:6050`, for example:

```json
{
    "insecure-registries": ["devartifactory.domain.lan:6050"]
}
```

# Get list of images on Docker registry

```bash
curl -k -X GET https://devartifactory.domain.lan:6050/v2/_catalog
curl -k -X GET https://devartifactory.domain.lan:6050/v2/docker-local/tags/list
```

# Tag and push Docker image to alternative repository

```bash
docker tag postgres devartifactory.domain.lan:6050/docker-local:postgres
docker login --username=rcook https://devartifactory.domain.lan:6050
docker push devartifactory.domain.lan:6050/docker-local:postgres
```
