리액트를 쓰면서 왜 리액트를 쓰는가에 대해서 언급한다면 감히 말해보겠다. ES5의 문법을 쓸수 있어서라고.. 비슷하게 많이 쓰는 앵귤러나 Vue에서도 쓸수도 있겠지만 아직 안써봐서 실제로 ES5의 문법을 쓸수 있는지는 모른다. 하지만 ES5문법을 쓸수있는 리액트는 정말 마음에 들었다.

* 개발을 위한 배경을 설명하기 위해서는 한참 걸리겠고 우선 유의할것 부터 살펴보도록 하겠다.

알아두어야 할 순서는 아래와 같다.
# [개념익히기](react_introduce.md)
# 첫번째 주제
1. [컴포넌트](react_life.md) 
2. [상태관리](react_data.md)
    - [redux](react_redux.md)
3. API호출
    - [api와 state의 연계](react_request.md)
4. [테스트](react_test.md)
# 두번째 주제
1. [맛보기](react_code.md)
2. [상세](react_replay.md)

아래는 간단히 개념을 익힌다고 생각하고 자세한것은 따로 빼서 보도록 하자.
> react_introduce.md는 정리를 할필요가 있다. 너무 어지럽다.
>> react_replay.md는 중복된 내용이 있을수도 있다. 수정하도록 하자.

---

## 컴포넌트 방식으로 UI 구현
우선은 컴포넌트를 사용한 개발방법을 가지자. 컴포넌트는 다음의 단계로 다시 나누어 생각하자. 

`Template` > `Container Compoent` > `Presentational Compent` 로 각 포함관계를 정리할수 있다. 
- Template : 컴포넌트를 감싸는 전체 레이아웃
- Component
    - 컨테이너 컴포넌트 : State를 관리하는 컴포넌트
    - 프리젠테이셔널 컴포넌트 : State가 없는 컴포넌트

* 컴포넌트를 분리한다는 것은 파일로 분리한다는 말과 같다.
> 그렇지만 하나의 파일에 두개이상의 컴포넌트가 있을수도 있다. 내부 클래스를 쓴다는 느낌으로..

---

## 데이터 관리 : Props와 State

컴포넌트 내부에는 state라는 데이터값을 가질수 있다. 
state가 변경됨에 따라서 화면이 변동된다. 
prop는 컴포넌트를 정의할때 넣는 속성을 말한다. 함수와 값을 줄수있다.

* props를 받아서 state에 넣는 경우가 많다.
* state가 수정될경우 화면을 다시 그리게 된다.이것때문에 state가 중요하다.
* state관리를 간단하게 할수도 있지만.. 리덕스라는 것으로 관리를 하게 된다.
> 하지만 리덕스를 씀으로서 더 난해해 질수도 있다.
>> 리덕스의 왔다갔다함에 왜 이걸쓰나 그냥 this.state로 선언해서 쓰면 안되나하고 생각하게 된다.
>>> 하지만 라이브러리는 진화할 것이고, 좀더 편한 라이브러리로 관리할수 있는 방법이 있을것이다. 내가 모르는것뿐..
>>>> 실제로 현재 프로젝트에서는 dispatch명령으로 쉽게 state를 업데이트하고 있다. 이걸 분석해보고, 실제 써봐야한다.

그외에 화면을 다시 그리는 방법은
1. 사용자가 이벤트를 발생시키게하여 elemet의 속성을 변경시키는 방법이 있다.
2. 컴포넌트를 분리하여서 Ref를 호출하여서 변경하는 방법이 있다.
> 음... 자세한 방법을 까먹었네? 분명 구현했었는데.. 이것도 알아보자.

state 정의
```
this.state = {number:0,test:'test'}
수정 : this.setState({number: 2});
읽기 : this.state.number
```
props 정의
```
onHandlerClick = () =>{
    console.log('click');
}
<Count name={'1'} testHandle={onHandlerClick}/>
수정 : props는 수정은 되지 않는다.
읽기 : Count 컴포넌트내에서 읽기
    let name = this.props.name //1;  
    <button onClick={this.props.testHandler}>
```

---

## API호출
API의 호출은 비동기방식으로 호출되게 되며, axio라이브러리를 이용하게 된다.

axio방식으로 가져온 데이터를 state로 넣어서 관리를 하게 된다.
> 현재 내가 하는 프로젝트에서는 state로 넣는것은 세션부분이고 사용자가 호출하는 api의 데이터는 jqx에서 생성하는 object에 넣어서 관리하게 한다.
>> 사용자가 호출하는 api데이터는 그리드라는 오브젝트에 바인딩형식으로 넣게 된다.
>>> response 아래에 데이터를 그대로 쓸수도 있다.

* axio는 ajax와 비슷한 라이브러리라고 생각하면 된다.

---

## 테스트케이스
>테스트케이스는 중요성을 위해서는 제일 처음 언급해야 할게 아닐까 하는데.. 우선은 개념을 익히기 위해서 제외되면서 마지막 부분에 언급을 하게 되고 그러면서 잊혀지는게 아닐까 한다. 
하지만 실제 개발을 하면서 무척 답답하게 느껴지게 된다. 바꿀때마다 브라우저로 매번 확인하는 것은 정말 시간소요도 많이 되고, 답답함을 느끼게 된다.

junit성격을 띄는 'jest'와 html내부의 element를 확인해주는 라이브러리만 잘 기억해 두어도 좋다.

* jest : junit과 비슷하다고 할수 있다.

* 라이브러리 추가
> create-react-app으로 만든것은 jest를 또 깔지 말자. 버전 충돌이 일어난다.
```
yarn add jest @testing-library/jest-dom @testing-library/react @types/jest axios axios-mock-adapter
```

sum.js
```
function sum(a, b) {
  return a + b;
}
module.exports = sum;
```

sum.test.js
```
const sum = require('./sum');

test('adds 1 + 2 to equal 3', () => {
  expect(sum(1, 2)).toBe(3);
});
```

