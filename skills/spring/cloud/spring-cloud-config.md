- 분산 시스템에서 서버, 클라이언트 구성에 필요한 설정 정보(application.yml)를 외부 시스템에서 관리

- 하나의 중앙화 된 저장소에서 구성요소 관리 가능
- 각 서비스를 다시 빌드하지 않고, 바로 적응 가능
- 애플리케이션 배포 파이프라인을 통해 dev-stage-live 환경에 맞는 구성 정보 사용


- config 파일 변경시 재적용 방법
    - 1. 서버 재기동
    - 2. Spring Actuator refresh
        - docs : https://docs.spring.io/spring-boot/docs/current/reference/html/actuator.html
        - Application 상태, 모니터링
        - Metric 수집을 위한 http end point 제공

    - 3. spring cloud bus 사용 (제일 효율적)
        - 분산 시스템의 노드(message queue)를 경량 메시지 브로커(rabbitMq)와 연결
            - AMQP (Advanced Message Queuing Protocol) : 메시지 지향 미들웨어를 위한 개방형 표준 응용 계층 프로토콜
                - 메시지 지햐으 큐잉, 라우팅(p2p, publisher-subscriber), 신뢰성, 보안
                - 가벼운 프로세스가 장점
                - Erlang, RabbitMQ에서 사용
                - 윈도우 설치시 erlang 먼저 설치 후 rabbitMq 설치 필요
                    - erlang 설치 후 환경변수 C:\Program Files\erl-23.1 추가
                    - rabbitMq local 설치 후 C:\Program Files\RabbitMQ Server, 서비스(로컬) RabbitMQ 확인 후 환경변수 C:\Program Files\RabbitMQ Server\rabbitmq_server-3.9.5\sbin 추가
                    - rabbitMQ management plugin 설치 (https://www.rabbitmq.com/management.html) -> rabbitmq-plugins enable rabbitmq_management -> http://127.0.0.1:15672 ( guest/guest)

                    -> 윈도우 설치 삽질 좀 하다가 이건 아닌거 같아서 도커 이미지 받아서 실행함...
                    1) rqbbitmq 이미지 설치
                        docker pull rabbitmq:3-management
                    2) rabbitmq 컨테이너 실행
                        docker run -d -p 15672:15672 -p 5672:5672 --name  msa-rabbitmq rabbitmq:3-management
                    3) 접속 확인
                        localhost:15672
                        ID: guest
                        PWD : guest




                    



            - Kafka 프로젝트
                - Apache Software Foundation이 Scalar 언어로 개발한 오픈 소스 메시지 브로커 프로젝트
                - 분상형 스트리밍 플랫폼
                - 대용량의 데이터를 처리 가능한 메시징 시스템
        - 상태 및 구성에 대한 변경 사항을 연결된 노드에게 전달 (Broadcast)



- git 
    - git remote -v
    - git push --set-upstream origin master (처음 push 에서만)
    - spring-cloud-config-token : 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





C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem;C:\Windows\System32\WindowsPowerShell\v1.0\;C:\Windows\System32\OpenSSH\;C:\Program Files (x86)\Intel\Intel(R) Management Engine Components\DAL;C:\Program Files\Intel\Intel(R) Management Engine Components\DAL;C:\Program Files (x86)\NVIDIA Corporation\PhysX\Common;C:\Program Files\NVIDIA Corporation\NVIDIA NvDLISR;C:\WINDOWS\system32;C:\WINDOWS;C:\WINDOWS\System32\Wbem;C:\WINDOWS\System32\WindowsPowerShell\v1.0\;C:\WINDOWS\System32\OpenSSH\;C:\Program Files (x86)\Pulse Secure\VC142.CRT\X64\;C:\Program Files (x86)\Pulse Secure\VC142.CRT\X86\;C:\Program Files\nodejs\;C:\Program Files\Git\cmd;C:\Program Files\Docker\Docker\resources\bin;C:\ProgramData\DockerDesktop\version-bin;C:\Program Files\erl-23.1;C:\Program Files\RabbitMQ Server\rabbitmq_server-3.9.5\sbin;C:\Users\user\AppData\Local\Microsoft\WindowsApps;C:\Users\user\AppData\Local\Programs\Microsoft VS Code\bin;C:\Users\user\AppData\Roaming\npm;C:\Program Files\OpenJDK\jdk-11\bin;;C:\Program Files\JetBrains\IntelliJ IDEA Community Edition 2020.3.2\bin;