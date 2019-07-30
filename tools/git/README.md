# GitHub을 이용한 개발

## 1. [Git 사용방법](git_use.md)
## 2. [Git Flow](git_flow.md)
## 3. [Git Tools 사용법](git_tools.md)

## 번외 1. [GitHub로 프로젝트 관리하기](./github/github_issueManager.md)
## 번외 2. [Git Page 사용방법](./github/github_page.md)
## 번외 3. [git 레퍼런스](https://git-scm.com/book/ko/v2)

* current use git ㅅㅏㄹㅖ 

---

> GitHub, Git Flow을 이용한 Git사용 정리
>> 번뇌인 GitHub Page는 깃을 통해 만드는 블로그이다.
>>> 테마를 정하며, 에디터 언어는 마크다운 이다.

git을 잘쓰기 위해서는 위해서는 status와 branch전략을 종합적으로 이해하여야 한다. 
요즘 유행하면서 내가 공감하고 있는  branch전략은 git flow이다.
우아한 형제들 글이 제일 잘 정리되어있는것 같아 많은 참조를 하였다.

여기서 언급하지 않는것은 fork전략인데 이것도 그렇게 다르지 않을 것이라고 본다. fork를 하여서 내 github로 가져오는 과정이 추가되며, pull request도 범위가 한단계 늘어서 내 remote에서 다른 사람의 remote로 범위를 넓혀가는 것뿐인것으로 보인다. 그전에 rebase를 해서 이력을 정리할 필요는 있어 보인다.

그외에 조금 약한것이 master에 태그를 다는 것인데.. 아직 경험을 해볼 기회가 없어서 하지를 못했다. tag가 다음에 개발할것하고 비교하는 단위로 쓰일것인데... 소스가 많을수록 의미가 있을까 싶기도 하다. fork까지 브랜치전략에 포함되는 버전에서 유용하지 않을까 싶기도 하고

Git의 동작원리를 이해하기 위해서는 아래 글을 읽고 보도록하자.
* Git 레퍼런스 
    * [git의 기본](https://git-scm.com/book/ko/v1/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EA%B8%B0%EC%B4%88)
    * [수정하고 저장소에 저장](https://git-scm.com/book/ko/v1/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EC%88%98%EC%A0%95%ED%95%98%EA%B3%A0-%EC%A0%80%EC%9E%A5%EC%86%8C%EC%97%90-%EC%A0%80%EC%9E%A5%ED%95%98%EA%B8%B0)
* outsider님이 들려주는 git 전체흐름 이해하기
    - https://blog.outsider.ne.kr/865
    - https://blog.outsider.ne.kr/866

## 3. ETC
### 3.1 [툴에서 사용하는 법](git_tools.md)은 나중에 따로 정리
* 이크립스에서 git 사용법
* intellJ에서 git 사용법
* visual studio code에서 git 사용법
* source tree에서 git 사용법

### 3.2 GitHub인증
> 두가지 방법이 있다.
1. github에 내컴퓨터를 ssh로 접근할수 있게 등록하는 방법
2. clone후에 로그인아이디와 패스워드를 입력하는 방법
   1. 이게 되는지 했갈린다. 내 컴퓨터는 우선 인증을 받아놔서 말이다.

---
## 용어

* reset : 특정 commit 버전으로 되돌린다. 
	- 3가지 모드가 있다. hard가 가장 강력하다. 얄짧없이 이동하는것.(깔끔하게)
    - 기능
        - 특정 branch로 모두 되돌리거나 특정 commit 버전으로 되돌릴수 있다.
        - add한 파일의 경우 이전상태(modify)상태로 만든다.(stage -> not stage)
* rebase : 브랜치의 commit history 정리하기
	- 필요없는 것 빼는것, commit history가 일부 지워진다.
    - fork한 것을 원본 remote에 pull request로 올릴거 아니면 쓰지 말자.
* 파일 상태 확인 : git status : untracked, unmodified, modified, staged	    
    * unstaged : add하기 전 상태
    * staged : add한 후 상태, working 디렉토리...
    * untracked : 아직 관리되지 않는 파일, 주로 내가 생성한 파일에서 많이 나온다.
    * Committed, Modified, Staged
* cherry-pick : 일부 commit의 스냅샷을 반영할때 사용한다
    * 하지만 너무 많을꺼 같아서 하기 싫으네?
* head : 
	- HEAD^ : 마지막 이전 커밋지점이라는 뜻이다. reset할때 주로 많이 쓴다.
	- HEAD~ : 현재 커밋지점
        - **HEAD~와 HEAD의 차이점은 무엇인가?**
	- head대신에 commit에 해당하는 스냅샷을 써도 된다.
* [merge와 rebase 차이점](https://blog.outsider.ne.kr/666)
    - rebase는 우아한형제들처럼 fork해서 쓸때만 쓰도록 하자.
* [reset과 revert의 차이점](https://www.devpools.kr/2017/02/05/%EC%B4%88%EB%B3%B4%EC%9A%A9-git-%EB%90%98%EB%8F%8C%EB%A6%AC%EA%B8%B0-reset-revert/)
    - revert는 하지 말자.
* git 기초 문제 해결 : https://seongbeom.github.io/2017/02/28/oh-shit-git.html#give-up


* remote이름이 origin으로 되어있는것에 대한 고찰
> 리모트 이름은 보통 origin으로 되어있다. 이 이름은 주로 git init후 원격으로 연결할때 정하고는 하는데, git서버에서 프로젝트를 생성한후 clone으로 할경우 remote이름을 origin으로 정하는 것 같다.([레퍼런스 내용](https://git-scm.com/book/ko/v1/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EB%A6%AC%EB%AA%A8%ED%8A%B8-%EC%A0%80%EC%9E%A5%EC%86%8C))
>> [참조](https://blog.outsider.ne.kr/866) : 로컬 저장소에 등록된 원격저장소 목록을 보면 clone을 받아온 대상인 원격 저장소가 origin이라는 이름으로 등록되어 있다. github에서 저장소를 새로 생성하면(fork로 생성하는 경우외에) git remote add origin git@github.com:outsideris/jquery.git와 같이 저장소를 추가하도록 안내를 하는데 이는 관례에 따라 메인 원격저장소를 origin으로 등록한 것이다.

	- 원격저장소 확인 : git remote
	- clone 명령으로 복제하면 원격 저장소를 추적하도록 자동으로 설정됩니다. 따라서 이후의 push 및 fetch / pull 명령으로 저장소를 생략 한 경우에도 제대로 변경 내용을 반영하고 검색 할 수 있습니다.


---
## 좀더 읽어보기

* [좋은 커밋 메세지](https://git-scm.com/book/ko/v1/%EB%B6%84%EC%82%B0-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C%EC%9D%98-Git-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%97%90-%EA%B8%B0%EC%97%AC%ED%95%98%EA%B8%B0) 
> 마지막으로 명심해야 할 점은 커밋 메시지 자체다. 좋은 커밋 메시지를 작성하는 습관은 Git을 사용하는 데 도움이 많이 된다. 일반적으로 커밋 메시지를 작성할 때 사용하는 규칙이 있다. 메시지의 첫 줄에 50자가 넘지 않는 아주 간략한 메시지를 적어 해당 커밋을 요약한다. 다음 한 줄은 비우고 그다음 줄부터 커밋을 자세히 설명한다. 예를 들어 Git 개발 프로젝트에서는 개발 동기와 구현 상황의 제약조건이나 상황 등을 자세하게 요구한다. 이런 점은 따를 만한 좋은 가이드라인이다. 그리고 현재형 표현을 사용하는 것이 좋다. 예를 들어 "I added tests for (테스트를 추가함)" 보다는 "Add tests for (테스트 추가)" 와 같은 메시지를 작성한다. 아래 예제는 Pope at tpope.net이 작성한 커밋 메시지이다.
* [소스코드관리와 Git](https://blog.naver.com/manhwamani/220571967289)
* [태그 방법](https://git-scm.com/book/ko/v1/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%ED%83%9C%EA%B7%B8)
* [태그 전략](https://git-scm.com/book/ko/v1/%EB%B6%84%EC%82%B0-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C%EC%9D%98-Git-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EC%9A%B4%EC%98%81%ED%95%98%EA%B8%B0) 
* [깃허브 fork 전략](https://git-scm.com/book/ko/v1/Git-%EC%84%9C%EB%B2%84-Hosted-Git)
	- 자신에게 보는 권한만 있다면 fork해서 수정하여 사용할수 있다.
	- 또한 자신의 것이 원본에 반영되기를 원한다면 full request를 해주면 된다.

## 당장 못해볼것들
* intellJ 툴로 실제 프로젝트 실제로 개발해보기
* AWS로 개발 배포해보기
