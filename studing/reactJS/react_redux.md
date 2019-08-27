리덕스는 상태를 좀더 효율적으로 관리하는데 사용하는 상태 관리 라이브러리이다. 상태관리를 위해서 리덕스뿐아니라.. 한가지를 더사용하는 것으로 알고 있다. 좀더 살펴보자.

리듀서는 상태값을 제어하는 것으로 컴포넌트를 그때 그때 바꾸지는 아니한다.

리덕스의 세가지 규칙 
1. 스토어는 단 한개만 사용한다. 그 대신 리듀서를 여러개 만들어서 관리
2. state는 읽기 전용이다. 절대로 직접수정하면 안된다.
3. 변화는 순수 함수로 구성해서 쓴다.(리듀서)

* 스토어(store) : 애플리케이션의 상태 값들을 객체 내부에 저장
* 액션(action) : 상태 변화를 일으킬때 참조하는 객체
> 액션은 파라미터 값을 나타내며, 액션 생성함수로 주로 만든다. 속성값으로 type를 꼭 주어야한다. 이 type으로 리듀서가 구분하는 것 같다.
* 디스패치(dispatch) : 액션을 스토어 전달하는 것을 의미합니다.
* 리듀서(reducer) : 상태를 변화시키는 로직이 있는 함수
> 액션의 type에따라서 객체를 변경해서 넘겨주는 함수
>> 두개의 파라미터를 가지고 있다. 첫번째는 혅재의 상태, 두번째는 액션객체이다.
* 구독(subscribe) : 스토어 값이 필요한 컴포넌트는 스토어를 구독합니다. 
> 실제로는 react-redux의 connect가 대신 한다.

리덕스의 원리 : 비지터 패턴
> 리듀서가 visitor패턴과 비슷하다. 액션에 따라서 해야할 로직을 정해 놓는 패턴이 말이다. 
>> 액션의 type값이 어떤 방문자인지 구분을 하는 것이고, 리듀서는 어떤것을 선택하는 로직이다. type에 따라서 클래스를 선택하는 것은 없어서 완벽한 비지터 패턴은 아닌듯하다.

<액션생성 함수>
```
const INCREMENT = 'INCREMENT';

const increment = (diff) =>({
    type:INCREMENT,
    diff:diff
})
```

<리듀서>
```
(...)
const initialState ={
    number:0
}
(...)

//state의 속성값이 여러개일때를 위해서 Object.assign이나 전개연산자를 사용한다.
function counter(state = initialState, action){
    switch(action.type){
        case INCREMENT:
            return {number:state.number + action.diff};
        case DECREMENT:
            return {number:state.number - action.diff};
        default: return state;    
    }
}
```

리덕스의 사용
```
import {createStor} from 'redux';

//스토어 생성
const store = createStore(counter);

//구독 : 현재 상태 확인, 실제로는 subscribe를 쓸일은 없으며 connect함수로 현재 상태를 확인한다.
const unsubscribe = store.subscribe(() =>{
    console.log(store.getState());//getState는 현재 스토어 상태를 반환한다.
});

//액션전달
store.dispatch(increment(1));
store.dispatch(increment(5));
store.dispatch(increment(10));

```