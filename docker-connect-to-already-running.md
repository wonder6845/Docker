# **이미 실행 중인 컨테이너에 연결하기**

디폴트로 '`-d`' 없이 컨테이너를 실행하면, "attached모드"로 실행됩니다.

detached 모드(예: `-d`)로 컨테이너를 시작한 경우에는 다음 명령을 사용하여 컨테이너를 다시 시작하지 않고도 컨테이너에 연결할 수 있습니다.

`1. docker attach CONTAINER`

이는 `CONTAINER`라는 ID 또는 이름으로 실행 중인 컨테이너에 연결합니다.

# interactive mode로 들어가기

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cb74239e-116a-4fb1-8f1a-9dc2628236ec/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220824%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220824T074251Z&X-Amz-Expires=86400&X-Amz-Signature=a9993386c725fbbbe7ee7d0d8e7ba5ed1fdd4acd12199f839c390351befa7eb6&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

위의 파이썬을 컨테이너화 하는 작업을 실행합니다.

```docker
FROM python

WORKDIR /app

COPY . /app

CMD ["python", "rng.py"]
```

1. 도커허브에서 파이썬이 있는지 확인
2. FROM ⇒ 파이썬을 베이스이미지로 사용 가능 
3. WORKDIR 을 지정
4. 코드 파일을 복사 ⇒ COPY 명령어 사용 : rng.py이 있는 현재 모든 파일을 /app에 복사
5. CMD ⇒ 컨테이너가 실행될 때 실행되어야하는 명령어를 입력 
6. docker build . 커맨드를 사용하여 도커파일 빌드

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f516cd74-185b-44e2-b5be-a4fcaef24db6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220824%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220824T074321Z&X-Amz-Expires=86400&X-Amz-Signature=8c764f0894fe46808b585477987ff633517e0cde71c22fddf01b1cea283116de&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

빌드 후 docker run 명령어를 실행시 에러 

- docker run을 사용하면 연결되지만 컨테이너나 컨테이너로 실행되는 애플리케이션에선 어떠한 것도 입력이 불가
- 입력 가능하도록 하려면 -i or --interactive를 사용 → 컨테이너는 입력을 수신하게됨
- attache모드가 아니더라도 컨테이너에 무언가를 입력할 수 있음
- -t 모드 (--tty) 는 수도 TTY가 할당되어 터미널을 생성
- 결과적으로 -it를 입력하면 입력가능한 터미널을 생성

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/9af0785e-6f39-458b-82d9-df199e3c5185/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220824%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220824T074355Z&X-Amz-Expires=86400&X-Amz-Signature=b4077c1335c1b118c8d7c2cd4ac603f0064bb76eaaed292a3c49d0ddbeff4f56&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

- -it 플래그를 추가하면 터미널과 입력을 수신하여 파이썬 파일을 실행 후 결과값을 터미널로 출력하게 해준다.

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c1963be3-424b-499c-8e91-c0b9e28749b4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220824%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220824T074430Z&X-Amz-Expires=86400&X-Amz-Signature=bf469dd647d155387431e56daf888bd54784c9cc502a4c1e53d3c01dd3bf2a99&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

- 실행 후 docker ps를 치면 컨테이너가 종료된것을 확인 할 수 있다.

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/77a3777d-c378-42b7-ba88-57c2d69d7024/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220824%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220824T074452Z&X-Amz-Expires=86400&X-Amz-Signature=931c0f36fad46252631b31287568c4f3110eba2135685a7e98f0ef1e097e20da&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

- docker start <컨테이너이름> 실행시 디폴트는 detach 모드이기 떄문에 컨테이너와 통신을 할수 없다.

방법

1. docker stop 후에 attach 모드에서 컨테이너를 실행

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/80f15f3a-0c2a-4a6e-9686-13fdc2d6359c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220824%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220824T074553Z&X-Amz-Expires=86400&X-Amz-Signature=cb7278100d12d14d98acfdbbc627585fc61bb9a22783dd3ffe7db4d2a4c1875b&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

- 그러나 이 방법은 숫자를 입력 후 다음 명령어를 출력하지 않음

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b344c564-2bbb-4797-a207-d88082e1c500/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220824%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220824T074618Z&X-Amz-Expires=86400&X-Amz-Signature=de97cb4e9a7b265cd73e686b6222402c66ecc68bb207039addf819d74c195d3a&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

- docker -i 옵션은 무언가를 입력할 수 있게 함

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1f6e7360-be37-4092-bf40-568245b7b120/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220824%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220824T074638Z&X-Amz-Expires=86400&X-Amz-Signature=3776f773dec147ca2b7062bb2288021632ef8eaddd43176557ac9323fe2dc650&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b9e6cfeb-bec8-471f-915c-bd67881156bc/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220824%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220824T074654Z&X-Amz-Expires=86400&X-Amz-Signature=9b788d72b924d0ecc0085215e923e66bd31c69ba9ea4bf438e400c91ebbe20e0&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

컨테이너 종료 후 더이상 실행되지 않음