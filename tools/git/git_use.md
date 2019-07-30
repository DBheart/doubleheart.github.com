## 1. Git 개요
Git는 Branch를 이용하여서 소스를 관리를 하는 시스템이다.
Git은 SVN과 같이 중앙집중이 아니라 분산시스템을 기반으로 만든 시스템이다.
> 내 컴퓨터에도 있고(local), 중앙에도 있다(Remote). 그리고 로컬과 중앙의 동기화(push,pull)를 하여서 관리한다.
> 기본적으로 내 컴퓨터에서 소스를 관리하므로 작업이 완료될때마다 중앙에 접속할 필요가 없어진다.
>> 로컬만 봐서는 단순하지만 하지만 Git branch 전략을 써야하므로 실제로는 조금 더 복잡하다. 잘못 쓰면 원성을 더 들을수 있다.

git의 상태를 다음과 같이 3단계로 통일해서 생각하자.
1. modify  : add하기전 상태, 표기는 no stage로 표기된다.
2. add     : add하고 난후, stage로 표기되고, commit 대상으로 된다.
3. commit  : commit 완료된 상태, working디렉토리에 있는 상태이다.(정말?) 

* git에 stash라는 단계가 임시 단계가 있다. 써본결과 참 편리하다. 브랜치는 바꿔야하는데 체크아웃할수 없어서 브랜치를 바꾸지 못했을때 쓸수 있는 임시 저장소에 넣어 놓고, checkout할수 있게 모두 바꾸어 준다.

## 2. Git 사용법
여기서는 git bash에서 의 사용법을 주로 이야기 한다. tools에서의 사용법은 따로 다루도록 하겠다.

> 주로 사용하는 방법은 remote에 있는것을 내 컴퓨터에 복제하기위해서 "git clone 저장소 변경디렉토리"를 한다. 
"git checkout -b 작업브랜치명"으로 작업할 branch를 새로 생성후에 생성한 브랜치로 이동한다. 이동한 브랜치에서 작업을 시작한다.
그런 뒤에 소스를 변경한다. 변경한 소스는 commit할 대상이라고 'git add 파일명'으로 지정한후 "git commit -m '메세지'"로 커밋을 한다.
몇개의 작업을 처리한뒤에 "git push origin 보낼브랜치명"로 remote에 반영한다.

svn을 쓰다가 git을 쓰면서 어려웠던(했갈렸던?) 몇가지가 있다.
1. commit전에 내가 수정사항한 사항 비교
    > svn에서 synchronize로 해서 수정사항을 한번 더 체크를 했었는데 여기서는 어떻게 체크하는지 모르겠다. 
    >> 아래와 같은사항을 나중에 찾아봐야겠다. 어딘가에 있을것도 같은데..
    - 로컬의 브랜치까리 비교
    - remote와 같은 브랜치끼리 비교 
2. 히스토리 보기
    > 파일별로 이전에는 어떻게 했는지 남이 수정한 것은 어떻게 
3. overwrite update와 overwrite commit 기능
    > 어제 드디어 찾았다. merge의 -X 옵션과 reset checkout의 독특한 기능을 통해서 찾아내었다. 밑에서 소개하도록 하겠다.
4. 이전 내역과 비교하는 방법
    > 방법이 있을까나? 히스토리 보는 방법

### 2.1 [Git에서 자주사용하는 명령어](https://rogerdudler.github.io/git-guide/index.ko.html)
1. **git status** : 현재 상태알아보기
2. git init 
3. git clone 저장소
4. git add 파일|디렉토리 
    - 주로 'git add .'로 전체를 반영한다. 하지만 예외를 할때는 'git add *검색어*'로 몇개만 찾아서 추가한다.
5. git commit -m 'commit 메세지'
6. git checkout -b 브랜치 : 브랜치 생성하고 브랜치 변경
7. git checkout 브랜치 : 브랜치 변경
8. **git branch -vv** : 브랜치 정보보기, 어떤 브랜치로 이동할지 찾기가 쉽지 않다.
9. git push origin master
10. git pull
11. git merge 병합대상브랜치
12. git log --all --decorate --oneline --graph : commit단위로 브랜치별 변동사항 그래프로 보기

* git commit상황을 그래프로 보기 [참조](https://stackoverflow.com/questions/1057564/pretty-git-branch-graphs)
** 11번만 같이 보여도 충분하지 않을까한다. 아니면 source tree를 쓰는것도 좋은 대체방안 같다.

* merge의 뒤에 있는 브랜치명은 현재브랜치에 반영할 대상브랜치를 쓰도록한다.
** 그러니까 내가 feature/1 브랜치에 있고 develop의 소스를 가져오려면 'git merge develop'라고 쓰면 된다.

## 3. 생각하지도 못한 기초 상식
* git의 branch는 초기생성시에 master로 만들어 진다.
** 그래서 아무 파일이 없을때 브랜치를 만들면 master라는 브랜치명이 새로 만든 브랜치명으로 바뀐다. 즉 1개의 master브랜치를 바뀐다.
* 파일단위로 관리를 한다. 폴더만 만들면 add와 commit이 되지 않는다. 또한 폴더는 겹쳐도 충돌이 나지 않는다.
* 충돌은 commit한것이 있을때만 난다. branch끼리 병합은 commit한 것끼리만 가능하다.
> git bash에서 상태가 [현재브랜치|merging]라고 뒤에 merging가 나오면 일부가 진행하다가 충돌난 상태인것이다.
> git status를 하면 몇가지 해결방법이 나온다.
>> 파일의 라인별로 충돌이 나지 않으면 충돌나지 않고 라인을 자동으로 합쳐 버린다. 그러므로 마지막줄에 추가하면 충돌나지 않고 합쳐질것이다.

* 중간에 rebase로 커밋이라던가 파일을 정리하는 것 같다.
* 왜 remote는 origin이라는 이름을 일괄적으로 쓸까? 내생각에는 github에서 일괄적으로 저렇게 만드는것 같다. git init으로 만들지 않고 github에서 레파지토리 만드는 이상은 저렇게 되는것 같다. 그리고 origin이라는 것은 내 컴퓨터에 등록되는 이름이다. 그냥 클론 받으면 그렇게 되는건가?
    - 명칭을 바꾸는 방법이 있는걸로 알고 있다. 하지만 굳이 바꿀필요가 있을까?

---

## 소스간 병합할때 나오는 이슈 해결방안
아래는 git flow을 따라했을때 나오는 사항에 대한 해결방안이다.
master, develop, feature(작업브랜치)로 진행된다는 가정하에서 보아야한다.

1. 로컬에서 환경설정 파일을 수정했다. 개발서버에는 같은 환경파일을 쓰고 있어서 remote에서는 반영 되면 안된다.
2. 내가 작업브랜치에서 작업을 있었다. 그런데 develop의 공통 소스가 추가되어서 받으라고 한다. 

위에것에서 위험요소는 있는것 같다.
1번은 내가 수정하였던것도 수정하면 어떻게 되는가이다. 그것의 위험성 방지는 임시저장으로 진행해야할 것같다.
2번은 받은 소스가 내가 수정한 소스랑 겹치면 안된다는 것이다. 


> 1번 해결방안 : 
> 처음에는 modify한것은 놔두고 merge하는 방법을 찾으려고 했다. 하지만 찾지를 못했다. 모든 해결방안은 소스를 모두 commit한 상황에서 해결을 할수 있었다. add도 하지 않는 modify상황에서는 진행할수 없었다. 그래서 합의본사항이 commit를 한후에 develop것으로 모두 바꾼후에 환경파일만 이전버전으로 돌리고 modify 상태로 돌리는 방법이다.

    1번 해결법 : 작업브랜치는 'feature/1'이라고 가정
        1. git add .
        2. git commit -m "commit"
        3. git checkout develop
        4. git pull
        5. git checkout feature/1
        6. git merge -Xtheirs develop
        7. git reset HEAD^ 환경파일
        8. git checkout 환경파일
        9. git reset 환경파일
    7~9번의 파일이 여러개 이면 해당 파일을 해준다.검색어를 써주어도 좋다.
    7번은 현재이전버전으로 돌리는 것이다. 8번은 환경파일을 add 상태로 돌리는 것이고 9번은 modify상태로 돌리는 것이다.
    3번을 하기전에 git stash로 임시저장을 해놓아서 기존파일과 어떻게 차이나는지 확인해보아도 될것 같다.

> 2번 해결방안 : git stash로 임시저장을 해놓은다음에 git stash pop으로 임시저장을 받은것을 되돌린다음에 merge하는 것이다.
>> 받는 파일이 내가 작업하지 않는 파일이어야 한다. 폴더는 겹쳐도 상관이 없다.

    2번 해결법 : 작업브랜치는 'feature/1'이라고 가정
        1. git stash --all
        2. git checkout develop
        3. git pull
        4. git checkout feature/1
        5. git merge develop
        6. git stash pop

* all 옵션을 주지 않으면 untracked라는 상태는 없어지지 않는다.
* Stash save를 해서 환경파일을 미리 저장해 두는 방법도 있다.
* [파일을 무시하게 하는 방법](https://blog.outsider.ne.kr/817)도 있다. 
    * .gitignore와는 또 다르다. Assume라는 방식
```
git update-index --assume-unchanged 파일명
```

## 충돌에 대한 해결방법
### 무시하기 설정
1. [.gitignore](https://gmlwjd9405.github.io/2017/10/06/make-gitignore-file.html) 설정
    - 로컬에서만 적용가능한지 확인 필요 
2. [Assume](https://blog.outsider.ne.kr/817) 설정
    - Pull받을때 수정되어야한다. 수정되는데 확인 필요
    - 이건 관리 대상에서 제외 하는 방법이다.
### commit 이전에 [취소하기](https://gmlwjd9405.github.io/2018/05/25/git-add-cancle.html)
1. Add한것 취소: git reset HEAD 파일
2. 수정할것 되돌리기 : git checkout -- 파일
3. [커밋한것 수정하기](https://backlog.com/git-tutorial/kr/reference/log.html) : amend옵션
    - 커밋 메세지 수정 : git commit --amend
    - 커밋한것에 파일 추가 : add로 추가후 1번과 같은 a
4. 커밋취소
### 커밋버전끼리 되돌리기
- merge conflict시에 일반적인 해결법 : https://blog.outsider.ne.kr/805
- merge할때 충돌나면 일방적으로 한쪽의 branch내용으로 바꾸기
    - 충돌난 파일은 내것으로 바꾸기 : git merge -Xours develop
    - 충돌난 파일은 지정된 branch로 바꾸기 : git merge -Xtheirs develop

- merge 이전 파일로 되돌리기(modify 상태로 되돌리기)
    1. 이전버전의 상태로 되돌리기 : git reset HEAD^ 파일/디렉토리
    2. 이전버전의 파일로 되돌리기 : git checkout 파일/디렉토리
    3. 파일의 상태를 add에서 add하기 전으로 되돌리기 : git reset 파일/디렉토리
    - one.txt로 진행
        - 이전버전의 상태로 되돌리기 : git reset HEAD^ one.txt
        - 이전버전의 파일로 되돌리기 : git checkout one.txt
        - 파일의 상태를 add에서 add하기 전으로 되돌리기 : git reset one.txt

    - 추가로 merge conflict가 발생했을 때 일일이 파일을 수정하는 대신 checkout 옵션을 주어 처리할 수 있습니다.
    (아직 안해 봄)
        - git checkout --ours CONFLICT_FILE
        - git checkout --theirs CONFLICT_FILE

        --ours 옵션을 내것으로 바꾸는 것이고, --theirs 옵션을 사용하면 외부의 것으로 바꾸는 것이다. 이렇게 파일들을 checkout해서 충돌을 해결한 다음 커밋을 해서 merge하면 됩니다.

- 강제로 브랜치것으로 바꾸기 : git reset --hard develop

### 리모트와  로컬
- remote와 local끼리 강제 집행
    - 강제 push : git push --force
    - 강제 pull
	    1. git reset --hard HEAD
	    2. git clean -f -d
	    3. git pull
-push한 것 되돌리기https://gmlwjd9405.github.io/2018/05/17/git-delete-incorrect-files.html
-[리모트의 브랜치 리스트 가져오기](https://cjh5414.github.io/get-git-remote-branch/)
- 원격리모트 브랜치 확인 : git branch -r
- 원격리모트 브랜치 가져오기 : git remote update

* 참조 : [여러상태에서 수정 이전으로 되돌리는 방법](http://hochulshin.com/git-revert-changes/)

—-

### Assume에 대한 약간의 정리

assum 
> git update-index --assume-unchanged 파일명
다시 변경내역에 추가하고 싶으면 다음 명령어를 사용하면 다시 git status에서 변경파일로 나옵니다. 

assum cancle
> git update-index --no-assume-unchanged 파일명 
너무 장기간 사용하면 잊어먹을수도 있다. 

assum all cancle
아래 명령어로 워킹트리 인덱스를 갱신할수 있다.
git update-index --really-refresh

* 내가 원하는 것 같기는 한데... 다시 pull받을때는 수정되어야하는데 그런것은 안될것 같다. 


팁 : unchanged 로 지정된 파일을 보려면 아래 명령을 실행해보세요.
git ls-files -v | grep ^h
> ㅇㅇ? 언체인지? assume를 말하는 거겠지?
>> 그런것 같다.
 > 즉, 내가 원하는 상태가 아니다.

