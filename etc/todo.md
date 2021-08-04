##뭘해볼까?

* 매일 leetcode 2~3문제 풀기..
    * easy 풀긴 푸는데... 풀고나서 다른 사람 답보면 접근하는 법이 다름 자괴감 생김.....ㅠ
    * 포기하지말고 꾸준히 하자....
    
* spring*boot*reactive slackbot
    * slack 사용 연습



* 몰인몰 만들기

    * 사용자 정보
        * 사용자
            * 가입 후 포인트 부여받고 해당 포인트로 웹툰,웹소설등을 대여해서 볼 수 있는 쿠폰을 구매하는 사이트 구성
        * 관리자
            * 슈퍼 관리자 (개발자 : 서브 관리자 권한 부여)
            * 서브 관리자 (운영자 : 포인트 신청에 대한 승인 및 이력 관리)

    * 상품 정보
    * 주문 정보, 발송 정보
    * 회원 정보, 포인트 정보


    * MSA
        * API GATEWAY (SPRING CLOUD NIGNX PROXY)
        * 사용자 API (restful api)    * mysql
        * 상품 정보 API (restful api) * mysql
        * AUTH 정보 api (restful api) * mysql

        * 포인트 정보 API (webplux api) * postgresql
            * create table Point.point (poi_id int, mem_id int, poi_dtm timestamp, poi_content varchar(100), poi_point int, poi_type varchar(10), poi_action varchar(10));
            * select * from postgres.public.point p ;
            * truncate table postgres.public.point;
            * CREATE SEQUENCE seq_point_id START 1;
            * select currval('seq_point_id');
            * select nextval('seq_point_id');
            * select setval('seq_point_id', 1);

INSERT INTO public.point
(poi_id, mem_id, poi_dtm, poi_content, poi_point, poi_type, poi_action)
VALUES(nextval('public.seq_point_id'), 0, now(), '', 1000, 'DEFAULT', 'PLUS');





        * 주문 정보 (webplux api) * postgresql
        * 발송 정보 (webplux api) * postgresql
            
        * 캐싱 (redis cluster)

        * 메시지 큐 (kafka cluster)
            * insert 토픽별로 처리할 구독자 app 필요
                * 실패 재처리 필요
                * db 입력 또는 유형(이메일/slack) 발송 처리

        * 검색엔진 (elastic search)
            * 전체 검색이 가능하도록 처리
            * kibina 사용 (로깅, 데이터 시각화)

        * 화면 (vue ? react ?)
        