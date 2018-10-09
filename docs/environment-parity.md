# Environment Parity

Keep all of the environments as similar as possible will give the confidence that the application will work everywhere.

When environments differ, we lose our ability to accurately predict how the application is going to behave in production.

!!! warning "Environment drift"
    Environment drift may a occurs  because:

    * the shared development environment has a different scaling and reliability profile than QA, which is also different than production.
    * the database drivers used in dev and QA are different than production.
    * security rules, firewalls, and other configuration settings are also different.
    * some people have the ability to deploy to some environments, but not others.

The opportunities for creating a gap between environments are nearly infinite; *time*, *people*, and *resources*, are the most common culprits. In order to decrease gaps between environments:

- **Reduce the time gap from check-in to production"**

    Every commit should end up in production after the amount of time it takes to run all tests, vet th change against all integration suites, and deploy to pre-production environments.

- **Automate deployments**

    Humans should never be deploying applications, at least not to any environment other than their own workstations or labs.

- **Accept no excuses as to why resource types should differ across environments**

    There is almost an infinite set of tools available, from granting local instances of databases, to using Docker on developer workstations, to provisioning isolated resources in the {==cloud/PaaS/Kubernetes==}.

Every decision that increases the functional gap between environments must be flagged and questioned. Resist the urge to mitigate this problem by allowing environments to differ.

## Kubernetes

* Kubernetes namespaces enables (theoretically) running code on the same actual cluster against the same actual systems while still keeping environments separate.
* Also use tools such as Minikube to create near-clones of production systems.
* rolling updates
