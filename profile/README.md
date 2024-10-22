# Simple Code Runner

## 소개

간단히 코드를 실행해볼 수 있는 웹 서비스

유저로부터 실행할 코드를 전달받고, 이를 실행해서 그 출력 결과를 유저에게 전달해준다.

## 목적

규모가 있는, 확장성있는 시스템을 설계하고, 구현하고, 배포해보는 경험을 통해 더 멋진 개발자가 되고자 한다!

가급적 설계, 배포에 집중할 수 있도록 비즈니스 로직은 상대적으로 간단한, 이런 주제를 선정해보았다.

## 대략적인 설계

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

