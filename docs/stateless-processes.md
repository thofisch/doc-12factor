# Stateless Processes

Applications should execute as a single, stateless process.

It is not that state cannot exist; it is that it must **not** be maintained within the application, meaning that all *long-lasting* state must be external to the application, provided by backing services.
    
!!! warning "The filesystem is not a backing service"
    You cannot consider files a means by which applications can share data {>>or can you?<<}. Disks in the cloud are ephemeral and, in some cases, even read-only.

## Share-Nothing

Processes are highly [disposable](/disposability), so they may come and go, scale horizontally and vertically. So anything shared among processes could also vanish at a moment's notice and without warning, potentially causing a cascading failure.

If processes need to share data (e.g., session state), again that data should be externalized and made available through a backing service.

!!! danger "Avoid in-memory data caching"
    Be mindful that processes need to start and stop quickly, so taking a long time to fill and in-memory cache during application startup violates this principle ([Disposability](/disposability)).

    Take advantage of third-party caching products (like Redis) that are designed to act as a backing service for your applications.


## Kubernetes

* Should we mention StatefulSets (I'm think no)?
