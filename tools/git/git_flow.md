## 1. git 혼자 쓰기
혼자쓰는데 별다른게 있을까? 그냥 master에서 개발하고 마일스톤 왔을때 태그하고 하는게 좋을것 같다. 아래와 같은 명령어면 충분할듯하다.

	- git add .
	- git commit -m "commit message"
	- git push 로컬브랜치 리모트브랜치
	- git pull : 다른곳에서 수정하였을때 코드 받아오기

## 2. [git flow](https://danielkummer.github.io/git-flow-cheatsheet/index.ko_KR.html) 사용법
> git으로 프로젝트를 하는 이상적인 방법
>> git의 브랜치를 master, develop, feature로 크게 나누고 개발하는 방법

[우아한 형제들의 글](http://woowabros.github.io/experience/2017/10/30/baemin-mobile-git-branch-strategy.html)이 잘 정리되어 있다. 하지만 혼자 썼을때는 저글이 이해가 되지 않는데 직접 git을 쓰는 프로젝트에 들어와서 적용할것을 보고는 무엇인가 살펴보니까 이해가 되었다.

* git의 branch와 repository전략은 참 다양한것 같다. 여기서 다 언급하기는 나의 지식이 짧고, 다 알수 있는것이 아니므로 [중앙집중식에 대해서 설명한 글](https://git-scm.com/book/ko/v2/%EB%B6%84%EC%82%B0-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C%EC%9D%98-Git-%EB%B6%84%EC%82%B0-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C%EC%9D%98-%EC%9B%8C%ED%81%AC%ED%94%8C%EB%A1%9C#_%EC%A4%91%EC%95%99%EC%A7%91%EC%A4%91%EC%8B%9D_%EC%9B%8C%ED%81%AC%ED%94%8C%EB%A1%9C)을 보도록하자.

* 우아한형제들은 중앙집중방식에서 좀더 확장한 개념으로 보인다. fork까지 활용하는 것을 보니 말이다.

### 2.1. 개발 흐름
git flow는 협업을 위해 단계별로 branch를 나누는 것이라고 할수 있다.
단계는 아래와 같다. 
1. master, develop으로 나눈다
2. 개발할 이슈(작업, 보통은 1개의 화면)가 들어올때 마다 feature브랜치를 따서 개발한다.
    - 개발자는 remote의 develop를 local develop에 pull	받은다. 
    - 개발한 것은 리모트 feature브랜치에 push한다.
3. pull request로 remote의 develop과 merge를 요청한다.
    - 이때 코드 리뷰를 실시 합니다.
    - pull reuquest에서 통과된것은 개발서버에 반영됩니다.
4. develop에 merge한 것을 테스터가 테스트를 한뒤에 확인한다. 
    - 덜 된것은 수정 요청
    - feature브랜치 별로 테스터가 받아서 로컬에서 확인해 볼수도 있습니다.
5. 기능간에 보여줄정도가 되면 master에 반영
    - 마일스톤 단위로 하는게 좋을 것으로 보입니다.
    - master가 변할때마다 tag를 찍는것 같다.
   (아직은 여기까지 안해봐서 상상해 본다.)
6. real server에 반영하기 위해서 realese브랜치에 반영
    - real server에서 오류가 난 사항은 hotfixes 브랜치에서 개발하여서 반영한다.(여기도 잘모른다. 상상해볼 뿐)

> git flow이라는 도구를 사용해서 flow을 초기에 만들어서 사용하는 것같다. 굿이 이렇게까지 해야하나? 싶은데 직접해보면 다를지도 모르겠다.

> 협업을 위해서 온라인(클라우드)를 적극 활용하는 것이 좋다. 회사에서 직접 도입하는 것보다는 외부에서 개발한것을 사용할 것을 권장한다. 배보다 배꼽이 커지는 경우가 있다. 
>>협업을 위해 사용법만 익히는 것도 어려운데 그것을 운영까지 하다니 생각만으로 덜덜하다.

* 도구로는 source tree가 있다.
* 이크립스와 비주얼스튜디오에서도 git을 쓸수 있게 해준다.
* source tree도 그렇고 개발툴들에서도 사용할수 있지만 무척느리다. 그냥 git bash나 명령문으로 하는 게 좋지 않을까 한다.

### 2.2 브랜치의 구조
브랜치를 상하 구조로 보면 master가 제일 최상위 보스이다. develop이 중간 보스이다. feature 브랜치는 말단들이다. 그래서 feature가 가장 많다. 보통 기능단위로 나오며 "feature/기능명"이다. realese는 일종의 바지 사장이다. 보여주기 위한 것이라고 나할까? hotfixes는 감사라고 보면 되겠다. 
1. 감사라 그런지 hotfixes로 수정한것은 master와 develop에만 반영되는 것을 볼수 있다.
2. 소비자가 보는 버전은 realese와 master가 대부분이며, fork로 받는것은 대부분 master로 알고 있다.

* 개발자는 feature만을 관리하며, develop는 읽기 권한이 있다.
* 테스터는 develop를 개발서버에 반영된것을 가지고 보면 될것 같다.

### git flow를 위해서 필요한 준비
1. 개발자 - develop관리자 - 테스터 구조로 이루어져야 한다. 
   1. 소스관리를 위한 아키텍쳐나 중간관리자가 있어야 한다는 말이다.
   2. 여기에 fork까지 들어가면 fork관리자도 있어야하겠지?
2. 서버는 local과 test서버 real서버로 구성되어야 한다.
3. realese와 master관리자는 따로 있어야 할것이다.

* develop관리자는 중간보스급의 권한을 가져야하고, 코드를 관리해야 한다. 코드리뷰의 책임이 있다.(그냥 내 생각)
* 서버 반영을 위한 realese와 master관리자는 CI툴을 써야지 편할 것으로 보인다. master관리자는 아키텍쳐가 되겠지?
* 테스터는 때로는 PL이나 PM이 될수도 있을것 같다.

## git flow에 이어서 fork 전략
> 우아한 형제들이 도입한 방법
> fork해서 따로 분리해서 개발한 뒤에 정말~ 필요한것 같으면 원문 소스에 가서 pull request를 요청하면 되지 않을까 싶다.
>> 같은 소스이지만 다른 url을 가질때 이렇게 fork해서 개발하면 되지 않을까? 자기 자신이 fork하는 것은 이상할까? 안될까?
---

우아한형제들 git flow이해하기 

정리하고 보니 우아한형제글이 더 잘 이해가 되는 것 같다.
제일 이해가 안되었던것은 레파지토리의 이름들이었다. 우아한 형제들 글(용어)을 정리 해보면

1. Upstream Remote Repository
	- fork의 최상위. 회장님 정도 되겠다.
2. Origin Remote Repository
   1. 회장님것을 나의 github아이디로 가져온 원격 버전, 사장님이다.
3. Local Repository 
   1. github에 있는것을 나의 컴퓨터에 설치한 버전, 클론받은것이다.
   2. 실제 개발자가 작업하는 곳

fork단계를 도입하므로써 좀더 복잡한 repository를 가지고 있는 것 같다. 

몇가지 의문사항(티켓어리 부분)
1. "upstream/feature-user 브랜치에서 작업 브랜치(bfm-100_login_layout)를 생성"이라고 써있는가?
2. feature-user라는게 있는데 이건 그냥 develop과 비슷한것 같다.
   1. develop을 하나만 유지하는게 아니라 기능별로 나누는 것인가?
   2. 기능을 2단계로 관리한다고 말로 해석될것 같다.
      1. feature브랜치 밑에 브랜치가 한단계 더있다는 것이다.

우아한 형제들이 한다는 것을 풀어보면
1. 이슈처리(개발)
develop에서 파생된 기능브랜치가 있으며, 기능 브랜치 밑에 이슈브랜치가 있어서 실제 작업은 이슈 브랜치에서 진행한다. 그리고 이슈브랜치를 기능 브랜치로 merge하는 pull reuqest를 요청한다.

2. QA
후에 릴리즈하기위해서 기능브랜치를 develop로 merger하는 작업을 실시한다. QA를 위해서 develop에서 realese 브랜치를 생성하여서 QA를 진행한다. QA중에 버그가 나온것은 hotfixs 브랜치를 만들어서 수정한후에 release버전에 merge하기 위한 pull request를 요청한다.

3. 배포
QA가 끝난 release 브랜치를 develop에 merge
develop를 master에 merge를 한다.
master에서 태그를 만든후에 배포한다. 

* 중간에 rebase로 커밋이라던가 파일을 정리하는 것 같다.

> 용감한 형제는 앱 출시기준으로 만들어져서 그런것 같다. 웹은 중간에 개발서버에 배포하는 단계가 있어야 한다. 아마 QA버전인 realse 브랜치에서 개발에 배포하지 않을까 싶다.

> 기능별 브랜치와 그 밑으로 이슈 브랜치까지 두는지 아직 이해가 안된다.
> clone라는 단계를 이야기 하지 않아서 말이 꼬인것인가? 무언가 중간단계가 빠진 느낌이 든다. 웹이 아니라 앱이어서 그런걸까? 왜 origin에서 clone단계를 거치는 것이 아닐까?

* 왜 remote는 origin이라는 이름을 일괄적으로 쓸까? 내생각에는 github에서 일괄적으로 저렇게 만드는것 같다. git init으로 만들지 않고 github에서 레파지토리 만드는 이상은 저렇게 되는것 같다. 그리고 origin이라는 것은 내 컴퓨터에 등록되는 이름이다. 그냥 클론 받으면 그렇게 되는건가?.. 다시 알아봐야겠다.

---

수정해본 처리 단계
1. upstream에서 fork받아서 origin을 생성한다. 
2. origin에서 clone 받아서 로컬에 다운로드 받는다. 
3. 로컬에서 기능 브랜치를 생성한다. 그리고 개발...
4. 로컬에서 origin에 push한다.
5. origin의 기능 브랜치에서 upstream의 develop로 으로 pull request를 요청한다. 
   1. 소스 리뷰
6. 디벨롭을 개발서버에 배포해서 QA를 진행한다. 
   1. 기존소스에 영향을 주는 요소가 있는지도 찾아본다.
7. realse버전으로 사용자에게 배포한다.
   1. develop에서 realse로 merge
   2. QA나 사용자가 발견한 오류는 hotfixs 브랜치로 만들어서 수정후에 realse에 반영

* 다시 살펴보자. realse와 hotfixes와 master, develop간의 관계가 애매하네?
