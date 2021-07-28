---
section: self-hosted/latest
title: Updating Gitpod Self-Hosted
---

<script context="module">
  export const prerender = true;
</script>

# Updating Gitpod Self-Hosted

## Upgrading Gitpod from v0.9.0 to v0.10.0

### default registry now requires password and username

Gitpod by default ships with an in-cluster docker-registry. If you use that one (instead of an external one), add the following to your `values.custom.yaml`:

```yaml
docker-registry:
  authentication:
    username: gitpod
    password: your-registry-password
```

Afterwards, a full redeploy is required (your DB and workspace state is kept in a PV):

```bash
helm del gitpod
helm upgrade --install -f values.custom.yaml gitpod gitpod.io/gitpod --version=0.10.0
```

### Certificate file names changed

The file names we expect in a secret has changed. Before we'd require the default names Let's Encrypt would use. Since 0.10.0 we require a `tls.key` and a `tls.crt`.
To adjust this in your existing installation:

1. execute the following inside your config folder:

```
mv secrets/https-certificates/fullchain.pem secrets/https-certificates/tls.crt
mv secrets/https-certificates/privkey.pem secrets/https-certificates/tls.key
```

2. Upgrade your installation again:

```bash
helm install -f values.custom.yaml gitpod gitpod.io/gitpod --version=0.10.0
```

## Upgrading Gitpod from v0.8.0 to v0.10.0

With version 0.10.0 there is one change that requires user action regarding the rabbitmq messagebus:

### rabbitmq now requires dexplicitly set password and username

Gitpod uses a rabbitmq installation for distributing messages between components. So far that has been using default credentials if not configured otherwise. With v0.10.0 this is now explicitly required.
To do so add the following to your `values.custom.yaml`:

```
rabbitmq:
  auth:
    username: your-rabbitmq-user
    password: your-secret-rabbitmq-password
```

If this is not present, `helm` will fail with the following message:

> rabbitmq username is required, please add a value to your values.yaml or with the helm flag --set rabbitmq.auth.username=xxxxx

## Upgrading Gitpod from v0.6.0 to v0.7.0

With version 0.7.0 there are two major changes that require a user action. Both relate to the remote storage.

### Built-in MinIO is now accessable at minio.your-gitpod-domain.com

When you install Gitpod on your own Kubernetes installation, it brings a built-in MinIO object storage (unless disabled). As of v0.7.0, the built-in MinIO instance is accessable at https://minio.your-gitpod-domain.com. That's the reason that (for security reasons) we do not set a default access and secret key for the built-in MinIO installation anymore. That means, you need to add your own random keys in your values files like this:

```
minio:
  accessKey: add-a-radom-access-key-here
  secretKey: add-a-radom-secret-key-here
```

If you don't do this, `helm` will fail with the following message:

> minio access key is required, please add a value to your values.yaml

### Remote storage config has been moved to a new component

If you have a custom remote storage config (e.g. you use your own MinIO instance or the Google Cloud Storage), you need to move the config from the component `wsDaemon` to the new component `contentService`. See the [Storage Guide](./configuration/storage) for an example.
