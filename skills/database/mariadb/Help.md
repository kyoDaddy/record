* powershell 
    * docker pull mariadb
    * docker run --name mariadb -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=mariadb mariadb
    * docker exec -it mariadb /bin/bash
    * mysql -u root -p


* kitematic
    * setting -> volume 들어가서 로컬 디렉토리 지정 (컨테이너 삭제 후에도 계정 정보 남도록 설정)


* 참고 
    1. https://logical-code.tistory.com/122
    2. https://firework-ham.tistory.com/105
