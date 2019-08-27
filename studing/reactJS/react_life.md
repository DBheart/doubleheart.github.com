## 리액트 라이프 사이클

라이프 사이클에는 아래와 같이 8개의 라이프사이클이 있다. 
* render(){...} 함수
* constructor(props){}
* getDervedStateFromProps(nextProps, prevState) {...}
* componentDidMount(){...}
* shouldComponentUpdate(nextProps, nextState){...}
* getSnapshotBeforeUpdate(preProps,prevState){...}
* componentDidUpdate(prevProps,prevState,snapsshot){...}
* componentWillUnmount(){...}

주로 쓰는것은 component로 시작하는 것을 많이 쓴다.
render은 필수이므로 말할필요 없고 constructor은 생성자와 같은것이다.

---

## 리액트파일의 구성

리액트의 파일은 대부분 js의 확장자를 가지게 된다.
> 예전에는 jsx확장자명을 썼다고 한다.

리액트 파일 하나를 보통은 컴포넌트라고 한다. 리액트 파일은 두가지 방식으로 정의할수 있다.
1. 클래스 선언방법
    - react의 Componet를 상속받아서 만들게 된다. 
    - 컨테이너 컴포넌트는 클래스 방식으로 정의한다.
2. 함수형 선언방식
    - 프리젠테이셔널 컴포넌트를 보통 함수형만든다.
    (하지만, 클래스방식으로 정의해도 상관없다.)

* 클래스 방식이라하면 react라이브러리의 Componet를 상속받는 것을 말한다. 

다른 파일에서 이 리액트 파일을 사용하기 위해서는 export를 해주어야한다. 
* 하나의 파일에 여러개의 export를 주어도 상관은 없다.
> 클래스방식에서는 보통 export default export로 하나의 export만을 준다.(우선은 내생각이다. 증명을 해야겠지? 자료를 찾자)

* [js와 jsx파일의 차이점](https://stackoverflow.com/questions/46169472/reactjs-js-vs-jsx/46169614)
> 별상관없지만, js파일을 쓰는게 일반적이다.
>> 때로는 리액트파일을 jsx로만 읽는 편집기(툴)가 있는데 요즘은 대부분 js로 써도 리액트 문법을 해석해준다.

---

## 컴포넌트 구분
프리젠테이셔널 컴포넌트와 컨테이너 컴포넌트
* 프리젠테이셔널 컴포넌트 : DOM과 스타일이 있다. 
> UI를 그리는데 집중, 오직 props로만 데이터를 가져올 수 있고 대부분 state가 없다. 주로 함수형 컴포넌트로 작성한다.
* 컨테이너 컴포넌트 : 내부에 DOM 엘리먼트를 직접적으로 사용하지 않고 감싸는 용도로 사용한다. 상태를 가지고 있을때가 많으며, 리덕스에 직접 접근 할수 있다.
* 이 구조의 장점 : UI와 데이터가 분리되며 컴포넌트의 재사용율이 높다.

이게~ 컴포넌트를 선택하는 기준이 었나보다... 어떤것에 따라서 컴포넌트를 사용할수 있는 기준..

connec([mapStateToProps],[mapDispatchToProps],[mergeProps])

* mapStateToProps : store.getState() 결과 값인 state를 파라미터로 받아 컴포넌트의 props로 사용할 객체를 반환합니다.
* mapDispatchToProps : dispatch를 파라미터로 받아 액션을 디스패치하는 함수들을 객체 안에 넣어서 반환합니다.
* mergeProps : state와 dispatch가 동시에 필요한 함수를 props로 전달해야 할때 사용한느데, 일반적으로는 잘 사용하지 않습니다.

