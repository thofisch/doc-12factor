# Introduction

These guidelines are based on the [Twelve-Factor App](https://12factor.net), and adapted to how we recommend building services and applications ready for the cloud.

!!! info "Cloud-native = cloud-ready = cloud-friendly"
    Within the context of these guildelines these terms are taking to mean the same, and is all about bringing cloud-centric best practices to software and IT generally, whether that be in the cloud or on premises.

    **The key takeaway: *cloud-native* is more than *cloud-only*.**

## Cloud-native Applications

A cloud-native application is designed and implemented to run on a Platform-as-a-Service (PaaS) installation and to embrace horizontal elastic scaling. The platform hides infrastructure details from the application developer.

Adhering to the following guidelines will help embrace elastic scalability, statelessness, and treating everything as a service, enabling development teams to built applications that can scale and be deployed rapidly:

1. **One Codebase, One Application** &mdash; one codebase tracked in a version control system, many deploys.
1. **API First** &mdash; gives the ability to work against public contracts without interfering with internal development processes.
1. **Dependencies** &mdash; explicitly declare and isolate dependencies.
1. **Build, Release, Run** &mdash; strictly separate build, release and run stages.
1. **Configurarion** &mdash; store configuration in the environment.
1. **Logs** &mdash; treat logs as event streams.
1. **Disposability** &mdash; maximize robustness with fast startup and graceful shutdown.
1. **Backing Services** &mdash; treat backing services as attached resources.
1. **Environment Parity** &mdash; keep all environments (development, staging, and production) as similar as possible.
1. **Admin Processes** &mdash; run admin/management tasks as one-off processes.
1. **Port Binding** &mdash; export services via port binding.
1. **Stateless Processes** &mdash; execute the application as one or more stateless processes.
1. **Concurrency** &mdash; scale out via the process model.
1. **Telemetry** &mdash; you cannot control what you cannot measure.
1. **Authentication and Authorization** &mdash; security should never be an afterthought.

As many of these factors feed into each other, following one factor makes it easier to follow another, and so on.

Don't think about these guidelines as an all-or-nothing approach, but rather learn where and when to compromise when planning and implementing cloud-native applications. {>>should we allow for thought?<<}

When you’re building a new application, force a decision as to why you should not build your application in a cloud-native way.

