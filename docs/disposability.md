# Disposability

When a cloud-native application is disposable, it means they can be started or stopped rapidly.

An application cannot scale, deploy, release, or recover rapidly, if it cannot start rapidly and shut down gracefully.

To take full advantage of the platform, build applications that not only are aware of this, but also embrace it.

!!! warning "Slow startup time"
    Bringing up an application that takes minutes to get into a steady state:
    
    * could mean hundreds or thousands of requests potentially getting denied
    * might trigger alerts or warnings as the application fails its health checks
    * even prevent the application from starting at all

!!! warning "Graceful shut down"
    When shut down is not done quickly and gracefully:

    * can fail bringing the application back up again after failure
    * runs the risk of failing to dispose of resources, which could corrupt data

!!! tip
    Long-running activities during application startup (populating a cache or preparing other runtime dependencies) must find another way of dealing with these activities. E.g., the cache could be externalized into a backing service so that your application can go up and down rapidly without performing front-loaded operations.

## Kubernetes

It seems like this principle was tailor made for containers and Kubernetes-based applications. The idea that processes should be disposable means that at any time, an application can die and the user won’t be affected, either because there are others to take its place, because it’ll start right up again, or both.

Containers are built on this principle, of course, and Kubernetes structures that manage multiple instances and maintain a certain level of availability even in the face of problems, such as ReplicaSets, complete the picture.
