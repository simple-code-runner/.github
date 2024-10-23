# Simple Code Runner

## Purpose

The goal is to become a better developer through the experience of designing, implementing, and deploying a scalable and extensible system!

To focus more on design and deployment, I have chosen a relatively simple business logic for this project.

## Overview

The Service that provides a web-based platform where users can submit code for execution. It includes:

- user authentication
- language-specific code runners
- queue-based job distribution system

![structure](https://github.com/user-attachments/assets/9a00fd38-6f4b-4e3c-bcbe-fd10d662a069)

### Client

- React.js를 사용한 SPA
- S3, Netlify 등을 통해 배포 예정

### Server

- 유저 인증
- 유저 별 rate limit 적용

### Message Queue

- 실행할 코드들을 담아두는 Message Queue
- 서버 내의 in-memory queue로 빠르게 구현하고, 추후 Kafka로 확장 예정

### Code Runner

- Message Queue에서 코드를 하나씩 꺼내서 이를 실행하는 서버
- 결과를 Client에게 전달하는 방법은 아직 고민 중이나, Server-Sent Event(SSE)를 사용 해볼 생각

