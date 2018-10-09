# Administrative Processes

[Stateless processes](/stateless-processes) runs regular business applications (such as handling web requests).

Separately, developers will often wish to do one-off administrative or maintenance tasks for the application, such as:

* Database migrations
* Running timed scripts, such as a nightly batch job or hourly import
* Running a one-off job that executes custom code only once

All of which should probably not be a part of the regular business application. Always consider whether an administrative process is what you want, or whether a different design or architecture would better suit your needs.

- **Avoid timers**

    Internalized timers that perform batch operations may look appealing on the surface, but it might not scale when there are multiple instances of the application running. If they’re all performing the same batch operation, this might also lead to corrupt or duplicate data.

- **Use telemetry**

    Do not rely on interactive shells, remote desktop, ssh, and even kubectl for in-process introspection, instead use [Telemetry](/telemetry) to cover more aspects of application monitoring.

- **Timed administrative batch processes**

    Consider exposing a RESTful endpoint that can be used to invoke ad hoc functionality, or alternatively, extract the batch-related code from the main application and create a separate application.

    Either will allow at-will invocation of timed functionality, but it moves the stimuli outside the application, while also solving the at most once execution problem that internal timers have on dynamically scaled instances.
    
## Kubernetes

* Jobs
* Cron Jobs
* Container Patterns
* AWS Lambda
