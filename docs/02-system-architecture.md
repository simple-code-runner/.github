# System Architecture Overview

The system is composed of five main components:

1. **Auth Server**: Validates users using OAuth and generates JWT tokens. It also enqueues jobs in the Message Queue, effectively applying rate limit per users.
2. **Message Queue**: Stores code execution requests, and the code execution results.
3. **Code Runners**: Dedicated workers process code from the queue and sends the result back to the queue.
4. **Result Pusher**: Pushes the execution result to the client.
5. **Client**: The web interface where users can log in, submit code, and view results.

# Component Interaction

## User Authentication

- The **Web Client** sends authentication requests to the **Auth Server**.
- After successful authentication, the client retrieves Access Token.

## Code Submission

- User sends code to the **Auth Server** with Access Token, which enqueues the code in **Message Queue**.
- **Code Runners** listens to the **Message Queue** for execution request, exeuctes the code.

## Send Result to Client

- **Code Runners** enqueues the execution result to **Message Queue**.
- **Result Pusher** listens to the **Message Queue** for execution result, forwards to the appropriate client.
- **Web Client** listens to the **Result Sender** using Server-Sent Events (SSE).