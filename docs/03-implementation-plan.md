# Implementation Plan

## Overall Functionalities

### Version 1
- Implement basic registration, login
- Code execution only, without sending result to client

### Version 2
- Send code execution result to client

## Web Client & Server

### Version 1
- Basic webpage with plain textarea input and submit button.
- Simple registration, without any verification.
- Authentication with JWT:
  - use only access token, without refresh token
 
### Version 2
- Server dequeue code execution result from Kafka
- Client retrieve code execution result from `Code Runner`

### Further Enhancements
- Improve web client using React
- More reliable registration with email verification or OAuth
- Implement refresh token for security
- Scale out server

## Code Runner

### Version 1
- Single process, single threaded code runner
- Support Python only

### Version 2
- Send code execution result to client

### Further Enhancements
- Compose with containers, scale out easily with AWS ECS
- Support many languages

## Kafka

### Version 1
- Learn how to use Kafka
- Start with single queue for code execution request

### Version 2
- Add queue for code execution result
