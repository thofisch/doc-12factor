# Concurrency

{==Cloud-native/Kubernetes/"cloud-friendly"==} applications should scale out using the process model.

Instead of making a single big process even larger, you create multiple processes, and then distribute the load of the application among those processes.

{==Cloud providers/PaaS/Kubernetes==} have perfected this capability to the point where you can even configure rules that will dynamically scale the number of instances of your application based on load or other runtime telemetry available in a system.

Take advantage of applications build as [disposable](/disposability) and [stateless, share-nothing processes](/stateless-processes) to take full advantage of horizontal scaling.

!!! warning "Avoid vertical scaling"
    There was a time when, if an application reached the limit of its capacity, the solution was to increase its size.

    Adding CPUs, RAM, and other resources (virtual or physical) to a single monolithic application is typically frowned upon in civilized society these days.

## Kubernetes

* Horizontal scaling is a key capability of Kubernetes

