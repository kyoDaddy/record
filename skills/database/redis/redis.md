- 참고 url : https://littleshark.tistory.com/68
    - 다운로드
        - docker pull redis
        - docker images

    - docker network를 구성
        - docker network create redis-net
    
    - 실행
        - docker run --name kyo-redis -p 6379:6379 --network redis-net -d redis redis-server --appendonly yes

    - 접근
        - docker run -it --network redis-net --rm redis redis-cli -h kyo-redis
        /*
            select 1      # 1번 데이터 베이스 선택
            select 0      # 0번 데이터 베이스 선택
            keys *        # 모든 키 보여줘!
            keys *index*  # index가 포함된 키 보여줘!
            del abce      # abcd 키 지워줘!
        */


    - redis 명령어 참고
        - https://littleshark.tistory.com/69        

    - redis docker 접근이 안될 경우 참고
        - ifconfig 
        - redis-cli -h 172.17.0.1 (windows docker redis 경우)
        - redis-cli (mac docker redis 경우)
        - https://hyunki1019.tistory.com/138