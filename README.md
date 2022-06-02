# [프로젝트 만들기](./pratice_coding)
# [개발을 위한 로드맵](./loadmap_temp.md)
## [Git](tools/git/)
## React.js

---
github와 로컬에 있는 것을 연결하는 방법(로컬에서는 이미 개발중인것)
1. github에서 깡통 레파지토리를 만듭니다.
2. 로컬에서 `git init`를 한후에 `git remote add origin "https://깃허브주소"`를 합니다.
3. 로컬에서 `git branch -M main`으로 메인을 주 브랜치로 만듭니다.
4. 로컬에서 `git push -u origin main`으로 소스를 올립니다.

* 위에 것은 깡통 레파지토리를 만들면 나옵니다. 처음에는 어떻게하지 당황했는데, 깡통 레파지토리를 만들면 간단하게 해결되네요.

```
echo "# html_css_test_202007" >> README.md
git init
git add README.md -> 'git add .'
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/DBheart/html_css_test_202007.git
git push -u origin main

## git add하기전에 .gitignore파일을 만들어서 툴관련된것을 없앤다.
```




---

현재 정리
1. React.js
   - atomic 패턴 : 다음으로 변형해서 쓰는게 맞는것 같다. 앞에 3개는 너무 이름이 어렵다. 쉽고 많이 쓰는것으로 바꾸는게 맞는것 같다.
     - atoms -> elements 
     - molecules -> fields
     - organisms -> layers
     -  templates 그래로 쓴다.
     -  pages 그대로 쓴다.
   -  hooks와 redux, context, mobx에 대해서 고민(2020) : https://github.com/DBheart/react_test_202001
   -  UI 라이브러리 : antD, materialUI grid, tree
2. html, css
   - html, css, javascript 공부한 내용(2020) : https://github.com/DBheart/html_css_test_202007
3. Git
4. 파이썬과 장고

---

관심사
1. 패턴 : 진행중, 코딩.. 할때마다 느낌이 다르다.
   - 웹 element의 사용에 대한 패턴 적용
   - api콜에 따른 패턴
   - 값 전달에 대한 패턴
   - 화면 초기화할때 api콜 이후에 초기화하는 방법에 대해서 : 결국은 리덕스로...
3. 알고리즘 : 진행중, 백준
4. 리액트, 프론트엔드
   - css , html5
   - 다른 프론트 엔드 : vue, Svelte
5. 파이썬과 장고 
6. 통합 : 배포, 개발자 환경
* 스프링은 리액트 정리되면 진행예정

---

레파지토리가 너무 많아서 정리했다.
- 23개 -> 13개 10개 줄었다. 
- 그래도 필요없고, 중복된게 꽤 많다.
- 아직도... 미련이 남은게 꽤 있네

>  나의 아집으로 남게되었다. 쥐뿔도 모르고 나도 할수 있다고 시도했던것들... 나쁘지 않았지만 끈기가 없었다. 
>> 라이브러리, 프레임워크를 가져다쓰면 해결되었겠지만, 그러지 않았다. 그게 아집이었다. 하지만 그런 실행이 있었기때문에 내가 있는게 아닐까?
>>> Life is Simple

## 스터디 포크
- DBheart/cloud(우리 팀들)
- DBheart/Interview_Question_for_Beginner(인터뷰용)
- DBheart/study(코딩-인터뷰용)

### [나의 발자취](./traces_me.md)
