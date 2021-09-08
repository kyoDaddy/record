- apache kafka
    - message broker(server)
        - 실행된 kafka 어플리케이션 서버 (메시지를 주고 받을때 저장되는 공간으로 사용)
        - 3대 이상의 broker cluster 구성 (권장)
        - zookeeper 연동
            - 역할 : 메타데이터 (broker ID, Controller ID등) 저장
            - Controller 정보 저장
        - n개 broker 중 1대는 controller 기능 수행
            - controller 역할
                - 각 broker 에게 담당 파티션 할당 수행
                - broker 정상 동작 모니터링 관리

    - 실시간 데이터 피드를 관리하기 위해 통일된 높은 처리량, 낮은 지연 시간을 지닌 플랫폼 제공

    - 모든 시스템으로 데이터를 실시간으로 전송하여 처리할 수 있는 시스템
    - 데이터가 많아지더라도 확장이 용이한 시스템

    - 아래 문제점을 카프카로 해결 가능
        - end-to-end 연결 방식의 아키텍처
        - 데이터 연동의 복잡성 증가 (HW, 운영체제, 장애 등)
        - 서로 다른 데이터 pipeline 연결 구조
        - 확장이 어려운 구조
 


- 설치 관련    
    - 컨플루언스
        - https://cwiki.apache.org/confluence/display/KAFKA/Clients

    - Kafka 홈페이지
        - http://kafka.apache.org
        -  tar xvf .\kafka_2.13-2.8.0.tgz 

    - Kafka와 데이터를 주고받기 위해 사용하는 Java Library
        - https://mvnrepository.com/artifact/org.apache.kafka/kafka-clients


    - Topic 생성
        - $KAFKA_HOME/bin/kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092 --partitions 1

    - Topic 목록 확인
        - $KAFKA_HOME/bin/kafka-topics.sh --bootstrap-server localhost:9092 --list

    - Topic 정보 확인
        - $KAFKA_HOME/bin/kafka-topics.sh --describe --topic quickstart-events --bootstrap-server localhost:9092

    - Windows에서 기동
        - 모든 명령어는 $KAFKA_HOME\bin\windows 폴더에 저장
        - .\bin\windows\zookeeper-server-start.bat  .\config\zookeeper.properties



- 기동

    - Zookeeper 및 kafka 서버 구동
        - linux
            - %KAFKA_HOME%\bin\zookeeper-server-start.sh %KAFKA_HOME%/config/zookeeper.properties
            - %KAFKA_HOME%\bin\kafka-server-start.sh %KAFKA_HOME%/config/server.properties

        - windows
            - . %KAFKA_HOME%\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
            - %KAFKA_HOME%\bin\windows\kafka-server-start.bat %KAFKA_HOME%\config/server.properties

    - Topic 생성
        - linux
            - %KAFKA_HOME%\bin/kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092 -- partitions 1

        - windows
            - %KAFKA_HOME%\bin\windows/kafka-topics.bat --create --topic quickstart-events --bootstrap-server localhost:9092 -- partitions 1

    - Topic 목록 확인
        - linux
            - %KAFKA_HOME%\bin\kafka-topics.sh --bootstrap-server localhost:9092 --list

        - windows
            - %KAFKA_HOME%\bin\windows\kafka-topics.bat --bootstrap-server localhost:9092 --list


    - Topic 정보 확인
        - linux
            - %KAFKA_HOME%\bin/kafka-topics.sh --describe --topic quickstart-events --bootstrap-server localhost:9092

        - windows
            - %KAFKA_HOME%\bin\windows/kafka-topics.bat --describe --topic quickstart-events --bootstrap-server localhost:9092

    - 메시지 생산
        - linux
            - %KAFKA_HOME%/bin/kafka-console-producer.sh --broker-list localhost:9092 --topic quickstart-events

        - windows
            - %KAFKA_HOME%\bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic quickstart-events

    - 메시지 소비
        - linux
            - %KAFKA_HOME%/bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic quickstart-events 
               -- from-beginning

        - windows
            - %KAFKA_HOME%\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic quickstart-events 
               -- from-beginning


- kafka connect
    - kafka connect를 통해 data를 inport/export 가능
    - 코드없이 configuration으로 데이터를 이동
    - standalone monde, distribution mode 지원
        - restful api 통해 지원
        - stream or batch 형태로 데이터 전송 가능
        - 커스텀 connector를 통한 다양한 plugin 제공 (file, s3, hive, mysql, etc...)

    - Kafka Connect 설치
        - curl -O http://packages.confluent.io/archive/5.5/confluent-community-5.5.2-2.12.tar.gz

        - curl -O http://packages.confluent.io/archive/6.2/confluent-community-6.2.0.tar.gz

        - tar xvf confluent-community-6.2.0.tar.gz

        - cd  $KAFKA_CONNECT_HOME

    - Kafka Connect 설정 (기본으로 사용)
        - %KAFKA_HOME%\config\connect-distributed.properties

    - Kafka Connect 실행 
        - linux
            - ./bin/connect-distributed ./etc/kafka/connect-distributed.properties

        - window
            - .\bin\windows\connect-distributed.bat .\etc\kafka\connect-distributed.properties

            - classpath is empty. please build the project first e.g. by running gradlew jarAll 
                --> C:\Work\confluent-6.2.0\bin\windows\kafka-run-class.bat 파일 내 rem Classpath addtion for core 부분 위에 아래 내용 삽입

                rem Classpath addition for LSB style path
                if exist %BASE_DIR%\share\java\kafka\* (
                    call :concat %BASE_DIR%\share\java\kafka\*
                )

    - Topic 목록 확인
        - linux
            - ./bin/kafka-topics.sh --bootstrap-server localhost:9092 --list

        - windows
            - .\bin\windows\kafka-topics.bat --bootstrap-server localhost:9092 --list

    - JDBC Connector 설치
        - https://docs.confluent.io/5.5.1/connect/kafka-connect-jdbc/index.html
            - confluentinc-kafka-connect-jdbc-10.0.1.zip 

        - etc/kafka/connect-distributed.properties 파일 마지막에 아래 plugin 정보 추가
            - linux
                - plugin.path=[confluentinc-kafka-connect-jdbc-10.0.1 폴더]
            - window
                - plugin.path=\C:\\Work\\confluentinc-kafka-connect-jdbc-10.2.2\\lib

        - JdbcSourceConnector에서 MariaDB 사용하기 위해 mariadb 드라이버 복사
            - ./share/java/kafka/ 폴더에 mariadb-java-client-2.7.2.jar  파일 복사



    - 오류 시
        Kafka Connect에서 설정 관련 디렉토리는 config가 아닌 etc 입니다.

        하지만 connect-distributed.bat에서는 log4j의 경로를 존재하지 않는 BASE_DIR%/config/connect-log4j.properties으로 잡고 있습니다.

        따라서 connect-distributed.bat의 log4j 경로를 %BASE_DIR%/config/connect-log4j.properties에서 %BASE_DIR%/etc/kafka/connect-log4j.properties로 바꾸어주면 해결 가능합니다.


        -> 총 수정한 파일은 3개
            - C:\Work\confluent-6.2.0\etc\kafka\connect-distributed.properties
            - C:\Work\confluent-6.2.0\bin\windows\connect-distributed.bat
            - C:\Work\confluent-6.2.0\bin\windows\kafka-run-class.bat

    - connector-source 생산
        - windows
            - %KAFKA_HOME%\bin\windows\kafka-console-producer.bat --bootstrap-server localhost:9092 --topic my_topic_users

    - connector-sink 소비
        - windows
            - %KAFKA_HOME%\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic my_topic_users
               -- from-beginning


    - kafka-sink-connector
        - kafka-source-connector -> topic ->  kafka-sink-connector (토픽에 쌓인 데이터 사용)  -> mariaDB에 추가 


{"schema":{"type":"struct","fields":[{"type":"int32","optional":false,"field":"id"},{"type":"string","optional":true,"field":"user_id"},{"type":"string","optional":true,"field":"pwd"},{"type":"string","optional":true,"field":"name"},{"type":"int64","optional":true,"name":"org.apache.kafka.connect.data.Timestamp","version":1,"field":"created_at"}],"optional":false,"name":"users"},"payload":{"id":11,"user_id":"my_id","pwd":"my_password","name":"myyyy","created_at":1631073846000}}




    -  파일 동기화 시 참고
        - https://kth12.github.io/kafka-connect-action/


    - kafka-topic 삭제하기 참고
        - https://hyojaedev.tistory.com/38

        - zookeeper-shell 접근
            - .\bin\windows\zookeeper-shell.bat localhost:2181
        - topic list 확인
            - ls /brokers/topics

        - topic 삭제
            - deleteall /brokers/topics/kyo_topic_users
            - deleteall /brokers/topics/my_topic_users
            - deleteall /brokers/topics/my_topic_users2



    - 최종 local에서 zookeper -> kafka boroker -> kafka-connector -> producer -> consumer 순으로 실행하면 됨
        1. .\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
        2. .\bin\windows\kafka-server-start.bat .\config\server.properties
        3. .\bin\windows\connect-distributed.bat .\etc\kafka\connect-distributed.properties
        4. .\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic my_topic_users --from-beginning
        5. .\bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic my_topic_users