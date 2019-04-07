git hub project와 이슈와 위키를 복합적쓰는 방법

git에서 관리 요소 : 프로젝트, 마일스톤, 이슈, Label, Assignee, Wiki

> 이 관리 요소들은 스크럼이나 칸반과 같은 방법론을 쓸때 알맞을 것 같다.
깃 쓰는것 자체가 그런 것을 생각하는 것이겠지?

# 요소 정의
- 프로젝트 : 최종 목표
- 마일스톤 : 중간 목표
  - 한달정도씩 쪼개자.프로젝트가 1년과 같이 길경우 3~4개월정도가 적당할것 같다.
  - 외부에 공개할 정도
  - 기간으로 하지 말고, 목표로 하는 것이 좋다.
  - 마일 스톤을 통해서 프로젝트의 전체 일정 대략적으로 정해질수도 있다.
- 이슈 : 작업단위
- Label : 일의 성격
- Assigness : 담당자
- Wiki : 프로젝트에 대한 조사
  - 쓸일이 있을까? 글자체가 공부 정리를 위한 글인데?
  - 긴 사설을 쓸때 쓰도록 하자.

* 라벨과 위키의 위치가 애매하다. 

# 각 요소간의 사용법
프로젝트에 카드를 직접 만들지 말고, 이슈를 만든뒤에 연결하도록 하자. 마일스톤은 중간에 만들도록 하자. 프로젝트를 짧게 할 경우에 마일스톤은 필요없을 것같다. 프로젝트를 짧게 하는것도 좋은 방법인것 같다.
1. 프로젝트 생성 -> 마일스톤생성 -> 이슈생성
2. 이슈에서 마일스톤과 프로젝트 연결
3. 소스와 이슈 연결방법 찾기

* 코드와 이슈의 연결 방법을 모르겠다.
* 구지~ 연결할 필요는 없는 것일까?


# 사용 사례
- [git project사용 사례](https://medium.com/returnvalues/%EC%9A%B0%EB%A6%AC%EB%8A%94-github%EB%A5%BC-%EC%9D%B4%EB%A0%87%EA%B2%8C-%EC%82%AC%EC%9A%A9%ED%95%9C%EB%8B%A4-83789075e5b6) 2018.01
- [git project에서 pull request까지 사용사례](https://www.popit.kr/github%EB%A1%9C-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EA%B4%80%EB%A6%AC%ED%95%98%EA%B8%B0-part1-%EC%9D%B4%EC%8A%88-%EB%B0%9C%EA%B8%89-%EB%B6%80%ED%84%B0-%EC%BD%94%EB%93%9C%EB%A6%AC%EB%B7%B0%EA%B9%8C/) 2018.07
- [gitlab에서 커밋과 이슈의 연동 사례](https://www.lesstif.com/pages/viewpage.action?pageId=20775379) 2018.05
- [github에서 커밋메세지로 이슈닫기](http://minsone.github.io/git/github-commits-closing-issues-via-commit-messages) 2014.01

사용사례를 보면서 몇가지 생각하지못한게 나왔다. 
1. 우선은 git template라는게 있다는 것. 
2. git flow를 git hub를 통해서하는 방법
   - 이슈와 개발 툴간에 연동해서 사용하는 것을 권장
   - 이슈 기반으로 branch를 만들것
   - pull request를 요청을 가지게 해서 code review시간을 가질수 있다는 것이다.
     - 그러기 위헤서는 remote      의 merge권한을 안주는 것도 중요할 것같다. 
3. 이슈닫기 기능
   - 커밋 메세지를 통해서 이슈닫기, 또는 pull request 메세지를 통해서 이슈닫는 기능이 있다.

* 소스와 이슈를 연동시키는 것은 의미가 없는 것 같다.
  * 소스 커밋시에 이슈를 닫을수는 있다는데 의미가 없는 것같다. 같이 PMS에서 관리하는게 나을지도 모르겠다. 이슈를 닫는게 아니라. 

# 번외
- 커밋 메세지 잘쓰기 : https://meetup.toast.com/posts/106

