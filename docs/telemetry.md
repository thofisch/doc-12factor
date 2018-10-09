# Telemetry

Telemetry should be an essential part of any {==cloud-native/Kubernetes/"cloud-friendly"==} application.

Building applications on your workstation lets you can inspect the inside of your application, execute a debugger, and perform other tasks that give you visibility deep within your applications and its behavior.

This is not possible with a {==cloud-native/Kubernetes/"cloud-friendly"==}, because of a number of reasons:

* Your application instance might move with little or no warning.
* You could start with one instance of your app, and a few minutes later, you might have hundreds of copies of your application running.
* You will not have direct access to the running process.

If you cannot physically touch it or bang it with a hammer to coerce it into behaving, what kind of telemetry would you want?

When it comes to monitoring your application, there are generally a few different categories of data:

* Application Performance M;onitoring (APM)
    * consists of a stream of events that can be used by tools to keep tabs on how well your application is performing.
    * This is something that you are responsible for, specific to your application and standards.
    * The data used to supply APM dashboards is usually fairly generic and can come from multiple applications across multiple lines of business.
    * APM might provide you the average number of HTTP requests per second an application is processing.
* Domain-specific telemetry
    * Is also up to you.
    * This refers to the stream of events and data that makes sense to your business that you can use for your own analytics and reporting.
    * This type of event stream is often fed into a "big data" system for warehousing, analysis, and forecasting.
    * domain-specific telemetry might tell you the number of widgets sold to people on iPads within the last 20 minutes.
* Health and system logs
    * Finally, health and system logs are something that should be provided by your cloud provider.
    * They make up a stream of events, such as application start, shutdown, scaling, web request tracing, and the results of periodic health checks.

When planning your monitoring strategy, you need to take into account how much information you’ll be aggregating, the rate at which it comes in, and how much of it you’re going to store. If your application dynamically scales from 1 instance to 100, that can also result in a hundredfold increase in your log traffic.

Auditing and monitoring cloud applications are often overlooked but are perhaps some of the most important things to plan and do properly for production deployments.

Getting telemetry done right can mean the difference between success and failure in the cloud.

## Kubernetes

* Liveliness/readiness probes
* Prometheus
* RED metrics (+ prebuild dashboards)