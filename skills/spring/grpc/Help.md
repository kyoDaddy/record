* grpc (google Remote Procedure Call) 왜 쓸까?

    1. rpc (Remote Procedure Call)
        - 네트워크로 연결된 서버 상의 프로시저(함수, 메서드등)을 원격으로 호출할 수 있는 프로세스 간 통신 기술
        - RPC를 이용하면 프로그래머는 원격지의 자원을 내 것처럼 사용
        - IDL(Interface Definition Language) 기반으로 다양한 언어를 가진 환경에서도 쉽게 확장이 가능
        - 인터페이스 협업에도 용이

    2. stub
        - RPC의 핵심 개념
        - 서버와 클라이언트는 서로 다른 주소 공간을 사용하므로, 함수 호출에 사용된 매개 변수를 변환 시 stub 사용

        
    3. HTTP/2를 사용
        - Proto fILE만 배포하면 환경과 프로그램 언어에 구애받지 않고 서로간의 데이터 통신이 가능 
        - HTTP/1은 클라이언트의 요청이 올때마다 connection을 생성해야 하지만 HTTP/2는 한 conection으로 통신이 가능하며 서버와 클라이언트가 서로 동시에 데이터를 주고 받을 수 있음
        - 높은 Header 압축률을 보장하고 중복을 제거 하기에 HTTP/1에 비해 훨씬 효율적
        - 클라이언트 요청 없이도 서버가 리소스를 전달 할 수 도있기 때문에 클라이언트 요청을 최소화

    4. ProtoBuf (protocol buffer)
        - Protocol Buffer는 google 사에서 개발한 구조화된 데이터 직렬화(데이터 표현을 바이트 단위로 변환하는 작업)
        - 결론은 JSON 기반의 통신보다 더 가볍다~
    
    5. ProtoFile
        - Message and Field 
            - ProtoBuf를 통해 주고받는 데이터들은 message를 통해 정의됨
            - 이 메시지는 여러 타입의 Field로 구성
        - Pacakge
            - messge 충돌 방지를 위해 설정 필요
            - 자바는 option java_package"; 를 지정하지 않으면 자바패키지로 사용
        - Service
            - Service는 RPC를 통해 서버가 클라이언트에게 제공할 함수의 형태를 정의
            - camelCase 권장
            - stream 옵션 주면 양방향 stream rpc 구현 가능


* 어디에 쓰는게 좋을까?

    1. MAS 구조에서의 private 통신간 사용하여 고객에게 응답하는 시간을 최소화하기 위해 사용할 듯.... (이것말고는 당장 생각나느게 없음;)






* 참고
    1. https://velog.io/@ypo09/%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C-%EC%84%9C%EB%B9%84%EC%8A%A4%EC%99%80-gRPC%EB%A5%BC-%ED%99%9C%EC%9A%A9%ED%95%9C-%EC%84%9C%EB%B2%84-%EA%B0%84-%ED%86%B5%EC%8B%A0-%EC%A0%81%EC%9A%A9%EA%B8%B0-2
    2. https://middlewares.files.wordpress.com/2008/04/17.jpg
    3. https://blog.banksalad.com/tech/production-ready-grpc-in-golang/?gclid=Cj0KCQjw0emHBhC1ARIsAL1QGNfVT7Wbbve-kxYmI2I5bMdYElTP1661Bs1TNFSD5Wfwe8z_CKUvyxYaAv0HEALw_wcB
    4. https://coding-start.tistory.com/367
