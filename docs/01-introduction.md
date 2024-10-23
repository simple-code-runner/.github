# Introduction

## Core Objectives

- Enable users to run code in many programming languages directly from a web browser, with no setup required.
- Ensure each code execution request is executed fast enough to be 'useful'.
    - Currently, the term 'useful' is intentionally ambiguous but will be clarified as the system is implemented. In the short term, the goal is to minimize response time as much as possible.
- Build a scalable, fault-tolerant system using containerization and distributed messaging to handle increasing demand without performance degradation.


## Key Features

### User Authentication

via OAuth

#### Why?

- Rely on external user authentication to reduce system complexity.
- Applying rate limits for each user prevents exploitation of the service.

### Message Queue

with Kafka

#### Why?

- Decouples execution requests from the execution layer, allowing code runners to scale independently.
- Kafka's high-throughput capabilities ensure that the system can handle large volumes of requests efficiently and without bottlenecks.

### Infrastructure as Code (IaC)

with Terraform

#### Why?

- Ensures that deployments are consistent, reproducible, and automated.
- Avoids reliance on platform-specific tools, ensuring portability across various cloud providers.

### Containerized Code Runners

containerize code runners, and manage them with Kubernetes (k8s)

#### Why?

- Improves scalability and makes it easier to monitor and manage resources.
- Allows for language-specific code runners, where each instance can be dedicated to a specific programming language, potentially leading to better reuse and optimization.
