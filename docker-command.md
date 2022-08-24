# docker 명령어 정리

# run, start, create 차이

**docker create :** 도커 이미지에서 새로운 컨테이너를 생성합니다. 그러나 즉시 실행되지는 않습니다

**docker start :** 중지된 컨테이너를 시작합니다. docker create 명령을 사용하여 컨테이너를 만든 경우 이 명령으로 시작할 수 있습니다.

**docker run :** create와 start의 조합으로 새 컨테이너를 생성하고 시작합니다. docker run 명령은 로컬 시스템에서 이미지를 찾지 못하는 경우 Docker Hub에서 이미지를 가져와서 컨테이너를 생성하고 실행합니다.

- docker create <이미지> → docker start <컨테이너 이름>
- docker run <로컬 이미지 or docker hub의 이미지> 컨테이너를 바로 생성 하고 실행

### **도커 컨테이너 및 이미지 삭제**

**docker rm -f** 명령어로  container-1 컨테이너를 강제 삭제합니다. 즉, 실행중인 컨테이너를 중지하고 컨테이너를 삭제합니다.

**docker rmi** 명령어로 ubuntu 이미지를 삭제합니다. 이제 컨테이너도 이미지도 남아 있지 않습니다.

```
$ docker rm -f container-1
container-1

$  docker rmi ubuntu
Untagged: ubuntu:latest
Deleted: sha256:d13c942271d66cb0954c3ba93e143cd253421fe0772b8bed32c4c0077a546d4d
```

**결론적으로 docker run 명령어는 pull, create, start 를 상황에 따라 수행하는 명령어입니다. 즉, 이미지가 없을 때는 pull, create, start를 이미지가 있을 때는 create, start를 수행하고 컨테이너가 있을 경우에는 start를 수행합니다.**

**docker images**

- 이미지 출력

**docker rm** 컨테이너 이름

**docker rmi**

**docker image prune** → 사용하지 않는 모든 이미지를 가지치기 하는 커맨드

**docker container prune** → 사용하지 않는 모든 컨테이너를 가지치기 하는 커맨드

**docker run -d -p 3000:80 --rm <container_name> →** 실행 후 종료시 자동으로 컨테이너 삭제

**docker cp <local file> <container_name>:/<file_name>
ex)docker cp dummy/. ecstatic_ramanujan:/test**

**docker image inspect <container_ID>**

**docker exec -it [컨테이너ID 또는 컨테이너명] /bin/bash**