* powershell 
    * $ docker run -p 5432:5432 --name postgres -e POSTGRES_PASSWORD=test!1234 -d postgres
    * docker exec -it postgres /bin/bash
    * psql -U postgres
    * CREATE USER kyo PASSWORD 'test!1234' SUPERUSER;
    * psql out command ==> \q

* kitematic
    * setting -> volume 들어가서 로컬 디렉토리 지정 (컨테이너 삭제 후에도 계정 정보 남도록 설정)


* 참고 
    1. https://judo0179.tistory.com/96
    2. https://blog.springboot.kr/2
