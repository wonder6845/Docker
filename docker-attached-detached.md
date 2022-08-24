# Attached & Detached 모드

docker start → Detached 모드가 디폴트

docker start <container name>

docker run → attached 모드

docker run -p 3000:80 <image name>

attached 모드는 단순히 그 컨테이너와 직접 통신하여 그 컨테이너의 출력결과를 수신하는 것을 의미

**run 커맨드로 detached 모드로 접속하기 (백그라운드 실행)**

docker run -p 8000:80 -d <image name>  

**반대로 start 커맨드로 attached 모드로 실행하기**

docker start -a <컨테이너 name>

detached 모드는 출력결과를 출력하지 않는다.

→다른 작업이 수행 가능

> 분리된 컨테이너를 다시 연결할 때는 docker container attach <컨테이너 이름>
>