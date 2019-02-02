# One Codebase, One Application

A codebase is a source code repository.

A cloud-native application always consist of a single codebase that is tracked in a version control system.

The single codebase for an application is used to produce [immutable releases](/build-release-run/#release) for different [environments](/environment-parity).

*One codebase, one application* does not mean that it is not allowed to share code across multiple applications; it just means that the shared code is yet another codebase.

## Violations

* If there are multiple codebases, it is not an applications – it is a distributed system.
* Multiple applications sharing the same codebase is a violation of this principle. A solution is to factor shared code into libraries which can be included as depedencies.
* Applications made of up multiple source code repositories, are nearly impossible to automate.

!!! warning "Conway's Law"
    Having multiple applications within a single codebase is often a sign that multiple teams are maintaining a single codebase. 
  
    Take care that poor organization and lack of discipline among teams does not lead to the same dysfunction or lack of discipline in the code.

    When looking at your application and deciding on opportunities to reorganize the codebase and teams onto smaller products, you may find that one or more of the multiple codebases contributing to your application could be split out and converted into a microservice or API that can be reused by multiple applications.

## Kubernetes

* {>>Should we touch upon Container Patterns here?<<}
* {>>Should we discuss Kubernetes manifests/GitOps?<<}

