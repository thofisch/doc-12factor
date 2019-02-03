# Configuration

An application should be completely independent from its configuration, allowing it to move to another environment without having to touch the source code.

Configuration refers to any value that can vary across deployments/environments (e.g., developer workstation, QA, and production), and may could include:

* URLs and other information about [backing services](/backing-services).
* Connection strings.
* Credentials.
* Information that might normally be bundled in configuration files (.NET applications traditionally get configuration from XML-based config files).

Configuration does not include internal information that is part of the application itself, so values that remains the same across all deployments is not considered configuration.

**Credentials are extremely sensitive information and have absolutely no business in a codebase.**

## Externalizing Configuration

External configuration allows deploying [immutable builds](/build-release-run) to multiple environments via CD pipelines and helps maintain [environment parity](/environment-parity).

The easiest and preferred options is to use environment variables to externalize configuration. As this works well both locally as well as {==for most cloud providers/PaaS/Kubernetes==}.

Another option for externalizing configuration is to use a server product designed to expose configuration.

When externalizing configuration, it should be possible to secure data changes as well as obtain a history of who made what changes and when.

## Kubernetes

Kubernetes enables you to specify environment variables in manifests, but as these manifests are part of the codebase, that is not a complete solution.

One options is to transform the manifests during build/release. {>>hmm, don't like this now I have to describe it...<<}

Another option is to specify the environment variables using ConfigMaps and Secrets, which can be kept separate from the application. For example, you might define:

```yaml
...
spec:
  containers:
  - name: container
    image: image:tag
    env:
    - name: SECRET_USERNAME
      valueFrom:
        secretKeyRef:
          name: mysecret
          key: username
    - name: SECRET_PASSWORD
      valueFrom:
        secretKeyRef:
          name: mysecret
          key: password
    - name: EXTERNAL_SERVICE_URL
      valueFrom:
        configMapKeyRef:
          name: myconfig
          key: external.service
...
```

The Pod then receives the environment variables, `SECRET_USERNAME`, `SECRET_PASSWORD`, and `EXTERNAL_SERVICE_URL`, the first two from the referenced Kubernetes Secrets, and the third from a Kubernetes ConfigMap.

!!! danger "Environment Variables"
    Environment variables are not necessarily safe for their own reasons. For example, if an app crashes, it may save all of the environment variables to a log or even transmit them to another service. [https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/). Consider a server product then.
