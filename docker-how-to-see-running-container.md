# 실행중인 컨테이너를 보는 법

1. attach 커맨드

![attachmode1](https://user-images.githubusercontent.com/94940412/186358816-27c650bd-2755-4c03-80b1-a73c3e5af486.jpg)


- docker attach <컨테이너 이름>

1. docker logs

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2e6f77a5-12e7-4bfe-8477-cdce97341270/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220824%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220824T073523Z&X-Amz-Expires=86400&X-Amz-Signature=cf97baa92ef468c825cdaf9104cdbd5503c168785ddf77a2bbaae3703aeba61a&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

- docker start elegant_noyce

컨테이너 내부에 있는 로그메시지를 액세스 하는 법

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f225db04-7e34-470f-bc68-f944c22b6b1a/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0be96972-3094-4681-afd1-a24889f8d42b/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f295bb53-0fed-490a-a3fa-a4a5321796cb/Untitled.png)

docker logs <실행 중인 컨테이너 이름>

- 로그 출력

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6866c83e-4bdd-4ed2-9bc0-751acc0f72aa/Untitled.png)

- -f 옵션을 추가하면 follow 모드 → 계속하여 수신대기
- docker logs -f <컨테이너 이름>

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/89d31fe1-ca50-4d55-aae3-6d9981cb0739/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7d956b09-0a7c-40a5-8d30-225e7f10ce92/Untitled.png)
