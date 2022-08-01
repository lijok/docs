# Language SDK

## Context
Universally understood good practices such as standardized logging, tracing, metrics etc, can be very complicated to implement.

Due to serious security implications when it comes to work involving encryption, hashing, secret handling, etc, developer autonomy and productivity is impacted as organizations tend to implement excessive processes around these pieces of work such as threat modelling.

Lack of consistency among projects impacts lateral movement of developers within an organization, as onboarding times get heavily extended, due to each project feeling like it was written by another organization, requiring the developer to relearn common patterns.

Lack of consistency among projects with respect to things like logging, metrics and tracing, leads to a heavy work toll on the operations teams. In addition, it hinders adoption of new tooling for processing these contexts, as any such tooling that may require code changes from developers, is prohibitively expensive to adopt.

[Microservice chassis](https://microservices.io/patterns/microservice-chassis.html) is an emerging pattern in the microservice world for reusing cross-cutting concerns.

Adopting new languages in a team is very expensive and fraught with issues. There is no good litmus test to determine whether a team is ready to welcome a new language.

A service must implement:
- Build logic that builds, and tests the application and also packages it into a production-ready format, such as a Docker container image.
- Cross-cutting concerns such as externalized configuration, logging, health checks, metrics, service registration and discovery, circuit breakers.
- Cross-cutting concerns that are specific to the technologies that the microservices uses.

Creating new services should be fast and easy.

It should be fast and straightforward to update existing services when the requirements for build logic and cross-cutting concerns change.

## Decision
We will maintain language specific software development kits.

For any language that we use, we will offload as much reusable code that does not contain business logic, into the aforementioned library.

We will implement, at a minimum, the following API's in these SDK's:
- structured logging
- tracing
- metrics
- configuration
- jwt middleware
- code formatting

## Consequences
Cross-cutting concerns are handled by the SDKs, allowing projects to be spun up and deployed to production quicker.

Contexts such as logging, tracing and metrics are in a standard format, consistent between services, and modifiable by the operations teams, allowing more freedom and unlocking more tooling options for operations to satisfy their observability needs.

Knowledge requirements for a new developer are lowered as some domain specific concerns are handled by the SDKs, which affords us a larger candidate pool.

Extensive domain knowledge is required to develop each of the APIs.

It is faster and easier to keep the dependencies, build logic and cross-cutting concern logic up to date. You simply release a new version of the SDK that contains the needed changes, and update each service to use the new version.

We need an SDK/SDK API for each programming language/framework that we want to use. This can be an obstacle to adopting a new programming language or framework.
