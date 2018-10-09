# Introduction

These guidelines are based on the [Twelve-Factor App](https://12factor.net), and adapted to how we recommend building services and applications that {==are ready for the cloud/Kubernetes/cloud-native/"cloud-friendly"==}.

## {==Cloud-Native/Kubernetes/"Cloud-Friendly"==} Applications

A {==cloud-native/"cloud-friendly"/Kubernetes==} application is designed and implemented to run on a Platform-as-a-Service (PaaS) installation and to embrace horizontal elastic scaling. The platform hides infrastructure details from the application developer.

Adhering to the following guidelines will help embrace elastic scalability, statelessness, and treating everything as a service, enabling development teams to built applications that can scale and be deployed rapidly:

1. One Codebase, One Application &mdash; one codebase tracked in a version control system, many deploys.
1. API First &mdash; recognizing APIs as a first-class artifact of the development process, will gives teams the ability to work against each other’s public contracts without interfering with internal development processes.
1. Dependencies &mdash; explicitly declare and isolate dependencies.
1. Build, Release, Run &mdash; strictly separate build and run stages.
1. Config &mdash; store config in the environment.
1. Logs &mdash; treat logs as event streams.
1. Disposability &mdash; maximize robustness with fast startup and graceful shutdown.
1. Backing Services &mdash; treat backing services as attached resources.
1. Environment Parity &mdash; keep all environments (development, staging, and production) as similar as possible.
1. Admin Processes &mdash; run admin/management tasks as one-off processes.
1. Port Binding &mdash; export services via port binding.
1. Stateless Processes &mdash; execute the application as one or more stateless processes.
1. Concurrency &mdash; scale out via the process model.
1. Telemetry &mdash; you cannot control what you cannot measure
1. Authentication and Authorization &mdash; security should never be an afterthought

As many of these factors feed into each other, following one factor makes it easier to follow another, and so on.

Don't think about these guidelines as an all-or-nothing approach, but rather learn where and when to compromise when planning and implementing {==cloud-native/kubernetes/"cloud-friendly"==} applications. {>>should we allow for thought?<<}

When you’re building a new application, force a decision as to why you should not build your application in a cloud-native way.
