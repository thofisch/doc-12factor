# Logs

Treat logs as event streams, i.e., a time-ordered sequence of events emitted from the application.

A {==cloud-native/Kubernetes/"cloud-friendly"==} application never concerns itself with routing or storage of its output stream, but simply writes all of its log entries to `stdout` and `stderr`.

Decoupling the knowledge of log storage, processing, and analysis from the code, simplifies the codebase, allows changing the way in which logs are store and processed without modifying the application, and helps with elastic scalability.

The aggregation, processing, and storage of logs is a non-functional requirement that is handled by the {==cloud provider/PaaS/Kubernetes==}, or some other tool running in concert with the platform. 

We rely on industry-standard tools and stacks to deal with logs, such as FluentD, ElasticSearch, and Kibana.

