# 리덕스와 http request의 연계
> 부제 : API와 리덕스의 연계

리액트에서 API에서 가져온 데이터를 다루는 기본적인 전략은 서버에 요청한 데이터를 리액트의 state에 넣는 것이다.

그것을 위해서 미들웨어라는 방식을 채택한다.
미들웨어는 액션과 리듀서 사이의 중간자. 액션을 디스패치했을때 리듀서에서 이를 처리하기 전에 사전에 지정된 작업을 실행하게 함으로써 state에 넣는다.

ES6의 Promise 기반으로 통신을 하게 만든 라이브러리인 axios를 사용하여서 API를 호출하고, 그것을 받아서 리덕스로 받게 하면된다ㅏ. 
그것의 비동기 처리를 위해서 미들웨어를 쓴다.

* 근데 나는 미들웨어를 안써ㅗ 될것 같은데... 왜쓰는지 모르겠다.
* Promise는 ajax처럼 API호출을 위한것이 아니다. 콜백처리를 위한 라이브러리라고 하는게 더 맞다. 콜백을 좀더 심플하게 처리할수 있도록 한것이다.
아마 비동기를 위한 미들웨어사용은 웹호출에 의한 시간이 있을때를 대비해서 사용하는 것 같다.


메뉴와 관련해서는 react-router를 가장 많이 사용한다. 주소에 따라서 화면 그리는것을 다르게 한다.

화면내에서 읻동은 Link 컴포넌트를 사용
NavLink컴포넌트도 있다.


import할때 상대경로를 불러오는데 package.json파일을 통해서 start와 build를 수정하면 금방해결할수 있다.
webpack의 resolve기능을 사용, create-react-app으로 만든 프로젝트는 노드패스를 자동으로 resolve하기 때문에 따로 설정을 변경할 필요가 없다.

-> 시작지점을 src로 해결
> "start": "NODE_PATH=src react-scripts start",
> "build": "NODE_PATH=src react-scripts build",

윈도우 사용자라면 위의 사항이 작동하지 않는다. 윈도우 사용자는 cross-env를 설치하여서 "NODE_PATH=src"로 설정한다.
> "start": "cross-env NODE_PATH=src react-scripts start",
> "build": "cross-env NODE_PATH=src react-scripts build",