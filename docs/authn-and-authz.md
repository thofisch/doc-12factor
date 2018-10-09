# Authentication and Authorization

Security is a vital part of any application and environment, and should never be an afterthought. A {==cloud-native/Kubernetes/"cloud-friendly"==} application is a secure application, and with tools like OAuth2, OpenID Connect, various SSO servers and standards, as well as a near infinite supply of language-specific authentication and authorization libraries, security should be something that is baked into the application’s development from day one, and not added as a bolt-on project after an application is running in production.

Even if the only reason you implement security in your application is so you have an audit trail of which user made which data change, that alone is benefit enough to justify the relatively small amount of time and effort it takes to secure your application’s endpoints.

In an ideal world, all applications would secure all of their endpoints with RBAC (role-based access control). Every request for an application’s resources should know who is making the request, and the roles to which that consumer belongs. These roles dictate whether the calling client has sufficient permission for the application to honor the request. {>>Or is ABAC a better answer?<<}

* Kubernetes
* Certificates
* HTTPS
* API Keys
* API Management Gateway
