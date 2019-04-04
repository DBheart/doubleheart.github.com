https://git-scm.com/book/ko/v2

깃은 파일을 수정을 하면 add를 해준후에 commit를 해서 자기 자신의 repository에 완료했다고 알려주어야 한다.
	- 자세한 메커니즘은 따로 보도록 한다.
	- add한것을 되돌릴 방법은 없는것같다. commit한것도 되돌릴 방법은 없다. 
		add하기전에 파일을 이전것으로 되돌리면 add대상이 아닌것 같다.
	- 삭제는 반드시 git rm 파일로 삭제하도록 한다. 
	- 히스토리는 커밋별로 볼수가 있는것 같다. 
		이크립스에서는 프로젝트별로 볼수 있는것 같다. 
		되돌리기 : https://git-scm.com/book/ko/v1/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EB%90%98%EB%8F%8C%EB%A6%AC%EA%B8%B0
			- 되돌리는 방법을 각 상태를 업데이트할때 CMD라인에서는 보여준다. 하지만 되돌리기는 하지말도록 하자. 
			- 차라리 BRANCH 변경을 하도록 하자.
	- 대신 이전 커밋한것과 비교를 해주는게 있었으면 좋겠는데 없는것 같다. 
		-> 이크립스 툴에서는 history로 볼수 있는것 같다.
		-> 어차피 기능별로 브랜치를 따야하므로 브랜치 별로 비교하면 될것 같다.
	- 수정전과 비교하는 것은 GUI 프로그램을 사용하여서 보도록 하자.
		> 이크립스의 history, source tree, git gui	
	- git은 파일을 삭제할때와 브랜치별 merge할때 조심해야한다.

리모트 이름은 보통 origin으로 되어있다. 이것은 주로 git init후 연결하거나 git서버에서 생성할때 정한다.
	- https://git-scm.com/book/ko/v1/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EB%A6%AC%EB%AA%A8%ED%8A%B8-%EC%A0%80%EC%9E%A5%EC%86%8C
	- 원격저장소 확인 : git remote
	- clone 명령으로 복제하면 원격 저장소를 추적하도록 자동으로 설정됩니다. 따라서 이후의 push 및 fetch / pull 명령으로 저장소를 생략 한 경우에도 제대로 변경 내용을 반영하고 검색 할 수 있습니다.


많이 쓰는 명령어
	- git add .
	- git commit -m "commit message"
	- git pull
	- git push 로컬브랜치 리모트브랜치
	- git checkout branch
	- git checkout -b branch

깃에서 살펴볼 이론	
	다른 버전관리시스템과 다른점
		Git으로 무얼 하든 데이터를 추가한다. 되돌리거나 데이터를 삭제할 방법이 없다.
		그러므로 branch를 따서 작업을 해야한다.
	상태확인의 중요성(파일 상태라는 조금 다르다)
		Committed, Modified, Staged
		각 상태별 디렉토리와 그것을 어떻게 옮기는 방법에 대해서는 알아두도록 하자
			https://git-scm.com/book/ko/v1/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EA%B8%B0%EC%B4%88
	파일 상태 확인 : git status : untracked, unmodified, modified, staged		
		- https://git-scm.com/book/ko/v1/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EC%88%98%EC%A0%95%ED%95%98%EA%B3%A0-%EC%A0%80%EC%9E%A5%EC%86%8C%EC%97%90-%EC%A0%80%EC%9E%A5%ED%95%98%EA%B8%B0

깃은 주로 요즘 깃허브를 이용한다. 그리고 git flow을 쓰는게 좋다.
	깃을 로컬에서 init하는 방법이 있지만 주로 레파지토리에서 생성한후에 clone받는것이 좋다.
	초기화면에 README.md파일을 만들어서 개요를 만드는게 좋다.
	- 리모트의 develop나 master에 넣을때는 full request를 사용하여서 merge하도록 한다.

파일무시하기 
	.gitignore파일을 만들어서 추가하도록 한다.
		- 

* 태그하기 
	- https://git-scm.com/book/ko/v1/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%ED%83%9C%EA%B7%B8

* 깃 branch merge 충돌
	- https://git-scm.com/book/ko/v1/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EB%B8%8C%EB%9E%9C%EC%B9%98%EC%99%80-Merge%EC%9D%98-%EA%B8%B0%EC%B4%88

* 깃 브랜치 전략 : git flow

reset : https://git-scm.com/book/ko/v1/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EB%90%98%EB%8F%8C%EB%A6%AC%EA%B8%B0
	- 이전파일로 되돌리는 것 , add한 파일을 이전 상태로 되돌리는 것
	- 파일이 state상태가 된것을 unstate상태로 되돌리는 명령어	

rebase : https://git-scm.com/book/ko/v1/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-Rebase%ED%95%98%EA%B8%B0
	- 브랜치를 특정 브랜치로 바꾸는것 같다... 아닌가? 더 자세히 봐야할것 같다.
	- rebase는 공통으로 사용하는 branch에는 적용하지 말자. master나 develop같은것. 자신이 개발하는 곳만 사용하도록 한다.

* 사용하지 않는 브랜치는 정리하는게 옮다.	
* 깃서버에 많은 시간을 들이지 말자. 그냥... 깃허브를 쓰는게 옮은것 같다.
* 깃허브에서 원격저장소 이름이 origin인 이유는?
	- https://blog.outsider.ne.kr/866
	- 아마.. 자신의 컴퓨터에서 원격저장소를 origin으로 등록하는 것일것이다. 어딘가에 설정되어있다. git setting하는 곳에...
	-  로컬 저장소에 등록된 원격저장소 목록을 보면 clone을 받아온 대상인 원격 저장소가 origin이라는 이름으로 등록되어 있다. github에서 저장소를 새로 생성하면(fork로 생성하는 경우외에) git remote add origin git@github.com:outsideris/jquery.git와 같이 저장소를 추가하도록 안내를 하는데 이는 관례에 따라 메인 원격저장소를 origin으로 등록한 것이다.

* 깃허브 fork 전략 
	- https://git-scm.com/book/ko/v1/Git-%EC%84%9C%EB%B2%84-Hosted-Git
	- 자신에게 보는 권한만 있다면 fork해서 수정하여 사용할수 있다.
	- 또한 자신의 것이 원본에 반영되기를 원한다면 full request를 해주면 된다.

* 좋은 커밋 메세지 
마지막으로 명심해야 할 점은 커밋 메시지 자체다. 좋은 커밋 메시지를 작성하는 습관은 Git을 사용하는 데 도움이 많이 된다. 일반적으로 커밋 메시지를 작성할 때 사용하는 규칙이 있다. 메시지의 첫 줄에 50자가 넘지 않는 아주 간략한 메시지를 적어 해당 커밋을 요약한다. 다음 한 줄은 비우고 그다음 줄부터 커밋을 자세히 설명한다. 예를 들어 Git 개발 프로젝트에서는 개발 동기와 구현 상황의 제약조건이나 상황 등을 자세하게 요구한다. 이런 점은 따를 만한 좋은 가이드라인이다. 그리고 현재형 표현을 사용하는 것이 좋다. 예를 들어 "I added tests for (테스트를 추가함)" 보다는 "Add tests for (테스트 추가)" 와 같은 메시지를 작성한다. 아래 예제는 Pope at tpope.net이 작성한 커밋 메시지이다.
 - https://git-scm.com/book/ko/v1/%EB%B6%84%EC%82%B0-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C%EC%9D%98-Git-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%97%90-%EA%B8%B0%EC%97%AC%ED%95%98%EA%B8%B0

* 태그 전략 
	- https://git-scm.com/book/ko/v1/%EB%B6%84%EC%82%B0-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C%EC%9D%98-Git-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EC%9A%B4%EC%98%81%ED%95%98%EA%B8%B0

* stash : 임시 저장
	- https://git-scm.com/book/ko/v1/Git-%EB%8F%84%EA%B5%AC-Stashing

* 커밋전략 : ?
	- https://git-scm.com/book/ko/v1/Git-%EB%8F%84%EA%B5%AC-%ED%9E%88%EC%8A%A4%ED%86%A0%EB%A6%AC-%EB%8B%A8%EC%9E%A5%ED%95%98%EA%B8%B0#%EC%BB%A4%EB%B0%8B-%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A5%BC-%EC%97%AC%EB%9F%AC-%EA%B0%9C-%EC%88%98%EC%A0%95%ED%95%98%EA%B8%B0








참조 
https://blog.outsider.ne.kr/865
https://blog.outsider.ne.kr/866


깃 레퍼런스 : https://git-scm.com/book/ko/v2



---

https://blog.naver.com/manhwamani/220571967289

develop을 중점으로 개발하고, 리뷰한뒤에 master로 반영한 다음에 배포한다. 중간에 feature로 수정을 가한뒤에 develop로 반영한다.
   - 미라콤의 경우에는 개발자별로 feature를 가는것 같다. release는 안정화버전.. 이고 hotfix는 반영했다가 버그나온것을 패치한 버전이다. 
  - reset이 있는데.. 이것은 로컬에 있는것을 강제로 받는것같다. 
   - remote의 develop와 feature와 맞추는 방법은 없는가?
      -> remote develop와 local develop을 맞춘후에 reset을 해서 develop한걸로 강제로 맞추었다. reset도 hard로 해야지 강제로 된다.
      -> 커맨드창으로 하는 방법을 물어보자.

* 그런데... develop를 feature로 넣는 방법은 무엇인가?


tag는 어떻게 되는 것인가?