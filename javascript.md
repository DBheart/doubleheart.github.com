https://d2.naver.com/helloworld/7495331

2017 ECMAScript의 동향 , https://d2.naver.com/helloworld/7495331, 작성일 : 2018.03

명칭 개요 : 표준 자바스크립트의 명세이름은 ECMAScript이며, 줄여서 ES로 부르곤 했다. 그러다가 ES6부터는 풀네임으로 ECMAScript 2015로 부른다. 그런데 했갈린게 줄임말과 년도가 일치하지 않는다는것이다. (맞추면 얼마나 좋은가.)
ES6를 넘어 ES8이 나올 예정이지만 브라우저에서 ES6 조차도 


* ECMAScript의 종류 : https://ko.wikipedia.org/wiki/ECMA%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8
 ES3 : function으로 정의해서 쓰는 형태로 많이 쓰임.
 ES5 : ES4는 버러짐, 이때부터 본격적인 객체의 개념이 도입된다.
  - jQuery로 많이 쓴 버전이다. (dom 파싱)
  - Strict Mode라고 "use strict"를 페이지 제일 위에 넣어서 엄격한 검사를 한다. 하지만... 몇가지 문제점때문에 권하지 않는다. 아마 ES5를 모두 지원하지 않기 때문일 것이다.
  - prototype로 객체개념은 사용할만 하지만 상속의 개념은 비추할 것 같다.
 ES6 : ECMAScript 2015 
  - var대신 사용할 변수선언문 let/ const 지원, 
  - 본격적인 클래스의 설정이 가능, 하지만 순수 자바스크립트로 구현하는것은 권하지 않는다. 최소 Node를 사용하자. reactJS를 쓰던가~
  - ES6 정리글(한글) : https://medium.com/sjk5766/ecma-script-es-%EC%A0%95%EB%A6%AC%EC%99%80-%EB%B2%84%EC%A0%84%EB%B3%84-%ED%8A%B9%EC%A7%95-77715f696dcb
 ES7 : ECMAScript 2016 
 ES8 : ECMAScript 2017, 아직 미정

 