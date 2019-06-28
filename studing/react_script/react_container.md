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
