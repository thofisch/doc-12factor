# Backing Services

A backing service is any service on which your application relies for its functionality that is not part of the core application.

Examples include databases, external storage, message queues, SMTP services, caching services, and any number of other types of service, including services that perform line-of-business functionality or security.

!!! tip "Use configuration"
    The binding of an application to its backing services should be done via [configuration](/configuration).

## Resource Binding

A bound resource is really just a means of connecting your application to a backing service (e.g., a connection string).

The code should make no distinction between local (SQLExpress) and third party services (Amazon RDS)). To the application, both are attached resources, accessed via a URL or other locator/credentials stored in the configuration.

It should be possible to attach and detach backing services from an application at will, without re-deploying the application. This means that there is never a line of code in your application that tightly couples the application to a specific backing service.

!!! tip "Circuit Breakers"
    Is a pattern (supported by libraries and cloud offerings) that will allow the application to simply stop communicating with misbehaving backing services, providing a fallback or failsafe path.

### Kubernetes

Note that when changing configuration, even though no changes are made the code (or even the container image) you will most likely need to replace the Pod.
