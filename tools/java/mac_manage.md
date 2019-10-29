# 맥북에서 관리
brew로 설치한것이 아니라 따로 받아서 설치한것으로 보인다.
brew로 한것은 jenv를 설치한 것 하나이다. 자바를 jenv로 설정

## 현재 나의 상황
1. jenv로 mac관리
    > 언제 이렇게 했지?
2. 아래와 같이 설치되어있다.
    - jdk 2.0 : openjdk
    - jdk 1.8 : adopt openjdk
    > openjdk를 설치한 이유는 아마도~ 오라클 로그인이 싫어서 그랬을것이다. ㅎㅎㅎ
## 사용방법
### 현재 버전확인
  - java -version
  - jenv versions
### cli에서 자바 변환
  - 1.8로 변환 : jenv global 1.8
### tools에 사용
  - java를 1.8과 2.0모두 등록해놓고 설정해서 사용하도록 하자.


* jenv : https://junho85.pe.kr/736
* openjdk : https://findstar.pe.kr/2019/01/20/install-openjdk-by-homebrew/