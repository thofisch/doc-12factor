# Port Binding

{==Cloud-native/Kubernetes/"cloud-friendly"==} applications export services via port binding.

We cannot relying on some kind of application server, like Microsoft Internet Information Server (IIS), to host our application. We must bundle an embedded server, because a {==cloud-native/Kubernetes/"cloud-friendly"==} application is self-contained (see [Depedency Management](/dependency-management)), and never injected into any kind of external application server.

Using externalized [configuration](/configuration) allow applications to do port binding at runtime, making it easy to act as a backing service for other applications, and supports environment-specific port binding without having to change any code.

## Kubernetes

{==Anything specific we need to mention in regards to Kubernetes?==}
