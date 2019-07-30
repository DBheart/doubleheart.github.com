## git log/show/blame로 비교하는 방법
### log : 이력보기의 기본
- 숫자 : 최신것에서 몇 개까지 커밋내용을 보여줄지 선택
- stat : 커밋별로 파일단위로 변경된 내역으로 요약해서 보여주기
- p : 소스변경 내용 보여주기
- 브랜치...브랜치 : 브랜치별로 변경사항보기
> 꼭 ... 3개의 점으로 되어야 한다. 
>> 3개의 점은 양쪽모두의 변경사항
>>> 두개의 점을 쓰면 왼쪽에는 없고 오른쪽에만 있는것을 보여준다.
- oneline : 안쓰면 커밋내용을 상세하게 보여준다.

* 결과를 그만 볼려면 "q 엔터"를 치면 된다.

```    
- git log : 현재 브랜치의 커밋내용을 보여준다.
- git log --oneline : 현재  브랜치의 모든 커밋내용을 보기
- git log --oneline -1 : 현재 브랜치의 제일 최근 커밋내용보기(파일X, 내용X)
- git log --oneline -1 feature/DEITY : 선택한 브랜치의 커밋내용보기(파일X, 내용X)
- git log --oneline -5 --stat : 최근 5개의 커밋을 한줄로 수정된 파일 표시,통계추가(파일의 줄단위 수정건수 표시)
- git log -1 -p               : 최신 커밋 1개 상세 확인(내용, 코드단위로 보여준다.)
- git log -번호 --stat --oneline 비교브랜치..현재브랜치 : 현재브랜치에있고 비교브랜치에 없는 내역을 확인한다.
```
> git log -2 --stat --oneline develop..feature/DEITY 
>> 이것으로 원격내역을 확인해 볼수도 있다. origin은 원격의 브랜치를 의미하므로..
>>> git log --stat --oneline origin/develop..feature/DEITY

### show : 지정해서 보기
- 커밋해쉬코드로 볼려면 log대신에 show를 쓰면 된다. 
    > log와의 차이점 : log는 커밋을 지정해서 볼수 없다.
- git show 커밋번호 --name-only : 커밋번호 지정해서 수정된 파일 내역보기
    > git show 06789629 --name-only
- git show 커밋:파일명 : 커밋번호의 파일내용을 본다.
    > 와 파일명을 풀네임으로 쳐야해서 참 불편하다. 

### diff : 파일간 비교
diff는 두개를 비교할때 쓰는것이다. 브랜치단위로 하면 log가 겹친다.
> 파일과 파일간의 비료를 위해 쓰도록 하자.
1. add하기 전과 add한것과 비교, 
2. 특정 커밋버전과 현재커밋버전과 비교, 파일한개만도 가능
2. 특정 커밋버전과 비교, 파일한개만도 가능
3. 특정 태그버전과 비교, 파일한개만도 가능
4. 특정 커밋버전 2개와 비교, 파일한개만도 가능
    - blame는 파일의 수정이력을 볼수 있게 해준다. 누가 수정했는지 알수 있다.
	> 누가 수정했다는 것만 나왔으면 좋겠는데 그런건 없네? 아웃붙에해서 줄여야하나?
	>> 그런데 소스단위가 아니라 파일단위로 누가 수정했는지만  알고 싶은데 그런것은 없는것 같다. 어느라인을 누가 수정했는지만 알수 있다. 

파일비교
- git diff : add하기 전과 add한 후의 파일일 비교
- git diff --color-words : 두줄로 나오지 않고 공백을 구분자로 한라인에 표시한다.
- git diff 브랜치 파일 : 브랜치에 있는 파일과 현재 파일과 비교
    > git diff b9c502ae public/src/deity/pages/testMainPage.js

브랜치 비교
- 원격 branch와 local branch의 파일을 비교 (이름만 비교)
    > git diff --name-only MERA-1 origin/DEV
- 원격 branch와 local branch의 파일을 비교 (이름, 변경된 총 line 수(insertions, deletions))
    > git diff --stat MERA-1 origin/DEV
- 원격 branch와 local branch의 파일을 비교 (이름, 내용 모두 비교)
    > git diff MERA-1 origin/DEV

- 현재 unstaged 된 수정사항만 확인
    > git diff
- 마지막 커밋과 현재 수정사항 확인
    > git diff HEAD 
- 마지막 커밋과 그 이전 커밋 비교
    > git diff HEAD HEAD^ 
- 로컬과 리모트의 내용 비교
    > git diff <branch명> origin/<branch명> 
- git diff <branch명> <다른 branch명> 

* 뒤에 파일명만 붙이거나 검색어 형식으로 붙이면 해당 파일들만 비교한다.
    - 응용으로 위의것에 파일명을 쓰면 해당 파일만을 비교한다.(검색어 가능, *)

    - 파라미터가 0개일때 : 기본이 modify상태인것만 확인
    - 파라미터가 1개일때 : 마지막 커밋과 파리미터와 비교
    - 파라미터가 2개일때 : 두개의 대상을 비교(파일, 브랜치, 버전, 스냅샷-해쉬)
    - 파라미터가 3개일때 : 마지막 3번째것은 파일이나 디렉토리를 쓰면된다.

* [git diff 더 알아보기](http://hochulshin.com/git-diff/)  

### blame : 한개의 파일 이력보기
한개의 파일에 대해서 수정 이력을 볼수 있다.
> 지정한 한개의 파일에 엮여있는 커밋들을 볼수 있다.

- git blame 파일명 : 해당 파일의 수정 이력을 볼수 있다. 
> 보는 내용 : 커밋해시값, 수정한 사람, 수정 이려깅 남겨진 시간, 커밋 메세지를 확인
- git blame -L 4,10 public/src/deity/pages/testMainPage.js : 4~10 라인만을 이력확인

---

* 참조 : https://git-scm.com/book/ko/v1/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EC%BB%A4%EB%B0%8B-%ED%9E%88%EC%8A%A4%ED%86%A0%EB%A6%AC-%EC%A1%B0%ED%9A%8C%ED%95%98%EA%B8%B0
* diff 좀더 쉽게 보기 : https://blog.outsider.ne.kr/1011
* git diff의 비교 : https://wani.kr/posts/2014/07/15/git-2-git-diff/

---    


