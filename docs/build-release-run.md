# Build, Release, Run

Going from {==design/code==} to running in production, could take as little as a few minutes, when a mature CI/CD pipeline is in place. Each of the following deployment stages is isolated and occurs separately:

* A single codebase is taken through the build process to produce a **{==compiled/binary==} artifact**.
* This artifact is then merged with configuration information that is external to the application to produce an **immutable release**.
* The immutable release is then delivered to an environment (development, QA, production, etc.) and run.

{>>Should we be more Kubernetes specific<<}

## Build

The build stage is where a code repository is converted into a versioned, {==binary artifact/container image==}.

Dependencies are fetched and bundled into the build artifact (a ZIP file or a binary executable or a Docker container image).

Builds are created by a CI server, and there is a one-to-many relationship between builds and deployments, so a single build should be able to be released or deployed to any number of environments, and each of those unmodified builds should work as expected.

The immutability of this artifact coupled with [environment parity](/environment-parity) give you confidence that your applications will work in production if it worked in QA.

## Release

The release is done by pushing to your {==cloud/PaaS/Kubernetes==} environment.

The output of the build stage is combined with environment configuration information to produce another immutable artifact, a release.

Releases must to be unique and identifiable, and every release should ideally be tagged with some kind of unique ID, such as a timestamp or an auto-incrementing number.

{>>Considering the one-to-many relationship between builds and releases, does it makes sense that releases should be tagged with the build ID (build+env)? We "cheat" a bit with our manifests being copied as build artifacts and then "transformed" during the release phase. I don't like that we cannot pull down a complete release without looking through VSTS (are variables versioned, etc)<<}

!!! danger
    A lot of problems can arise from the inability to reproduce a release as it appeared at one point in the past.
    
    Having a separate release phase, and storing those artifacts, enable easy rollback {>>but do we want it?<<} and historical auditing.

## Run

The run phase is done by the {==cloud provider/PaaS/Kubernetes==}.

When an application is running, the platform is responsible for keeping it alive, monitoring its health, aggregating its logs, as well as a lot of other administrative tasks like dynamic scaling and fault tolerance.

!!! info "Run locally"
    In order for developers to feel unhindered while working on {==cloud-native/Kubernetes/"cloud-friendly"==} applications, it is {==almost==} always worth the extra effort of ensuring that developers can run an application locally on their workstations, while still allowing it to be deployed via CD pipeline.

    Using Docker and/or Minikube help create near-clones of production systems.
