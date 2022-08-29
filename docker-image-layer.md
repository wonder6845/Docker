# Image Layer

Dockerfile

```docker
FROM node

WORKDIR /app

COPY . /app

RUN npm install

EXPOSE 80

CMD ["node", "server.js"]
```

이미지를 빌드시 이미지를 빌드하고 닫는다.

무언가를 업데이트를 해야할 경우 다시 빌드해야함.

도커는 레이어 기반이다.이미지를 빌드하거나 다시 빌드할 때 모든 코드들은 다시 재검토된다.

```jsx
[+] Building 0.1s (9/9) FINISHED
 => [internal] load build definition from Dockerfile                                                  0.0s 
 => => transferring dockerfile: 31B                                                                   0.0s 
 => [internal] load .dockerignore                                                                     0.0s 
 => => transferring context: 2B                                                                       0.0s 
 => [internal] load metadata for docker.io/library/node:latest                                        0.0s 
 => [internal] load build context                                                                     0.0s 
 => => transferring context: 184B                                                                     0.0s 
 => [1/4] FROM docker.io/library/node                                                                 0.0s 
 => CACHED [2/4] WORKDIR /app                                                                         0.0s 
 => CACHED [3/4] COPY . /app                                                                          0.0s 
 => CACHED [4/4] RUN npm install                                                                      0.0s 
 => exporting to image                                                                                0.0s 
 => => exporting layers                                                                               0.0s 
 => => writing image sha256:1b81e20c0f344e734bf408220d5d833ecdff351914c2e9ac0617a7015d6bcab6          0.0s 

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
```

캐시를 사용하여 명령어가 동일할 경우 명령을 재실행하지 않음.

대신 매 빌드시 모든 명령을 캐시하여 재사용할지 검토한다.

모든 명령은 도커파일의 **레이어**