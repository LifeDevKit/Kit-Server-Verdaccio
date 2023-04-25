# Kit-Server-Verdaccio 

# Install
 - 종속성을 위해 서버설정 및 클라이언트측 로그인이 되어있어야한다.
 - [Verdaccio](https://shlifedev.tistory.com/69) 서버가 열려 있어야한다. 

## CDN Install
 - 이 부분 계획해야함. 현재 서버 로컬에 패키지가 올라가는 구조인데 이걸 반드시 cdn을 지정해주어야함


## 개인 패키지 서버에 로그인
```
   > openupm login -r http://package.shlife.dev:4873 -u id -p password -e email --always-auth=true
   > npm 으로도 똑같이 로그인 해준다.
```

## 개인 패키지 서버에서 검색하기
```
   > npm -r http://package.shlife.dev:4873 search 검색어
```


 
# 프로젝트에서 사용하기
스코프 레지스트리를 등록해야한다. 하지 않으면 종속성을 다운로드 할 수 없음.
 ```
"scopedRegistries": [
    {
      "name": "package.openupm.com",
      "url": "https://package.openupm.com",
      "scopes": [
        "com.openupm
      ]
    },
    {
     "name": "custom server",
      "url": "http://package.shlife.dev:4873",
      "scopes": [
        "com",
        "com.shlifedev"
      ]
    }
  ]
```

# 향후 계획
 현재는 클라우드 디스크에 파일이 저장되는데 storage를 백업해두어야 할듯 
 
### 백업플랜
 ``` 
 Publish : publish -> storage middleware [작성필요] -> aws s3
 ```
 
### 패키지 퍼블리시 플랜
```
 현재는 npm -r [ip] publish 로 퍼블리시 해야함
 앞으로도 그냥 그렇게 하는게 맞을듯 다만 레지스트리 설정이 좀 불편해서
 전역 npm 명령어를 만들고 환경에 적용 가능한지 알아봐야 할듯
```
