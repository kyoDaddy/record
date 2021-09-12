
- AMQP (Advanced Message Queuing Protocol) : 메시지 지향 미들웨어를 위한 개방형 표준 응용 계층 프로토콜
                - 메시지 지햐으 큐잉, 라우팅(p2p, publisher-subscriber), 신뢰성, 보안
                - 가벼운 프로세스가 장점

    - 예시
        - docker run -d --name rabbitmq --network ecommerce-network -p 15672:15672 -p 5672:5672 -p 15671:15671 -p 5671:5671 -p 4369:4369  -e RABBITMQ_DEFAULT_USER=guest  -e RABBITMQ_DEFAULT_PASS=guest rabbitmq:management

        - docker network inspect ecommerce-network

        - 관리자 : http://127.0.0.1:15672/