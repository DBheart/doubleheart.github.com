# 리덕스 배운것 정리 및 이해하기

우선은 여태까지것 정리

> 리액트 개발에서 처음으로 할것은 컴포넌트 단위로  쪼개는 거다. 그 다음이 상태를 관리하는 거다. prop와 status를 관리하는 것. prop는 부모창에서 받은 것들이고, state는 현재의 클래스의 값이라고 생각하면 쉽다.

이제부터는 그 값들을 리덕스라는 라이브러리로 관리하한다. 내가 느낀것은  prop를 state에 넣어서 사용하나는 느낌이 들었다.

스토어를 최초의 로딩되는 js에 객체로 만든다. 그리고 스토어를 정의할때는 액션과 리듀서를 만들어 놓은뒤에 이 스토어 어떤 것을 쓸것인지 초기에 설정해주어야 한다. 

액션은 데이터의 구조(테이터 템플릿?)를 정의하는 것이라고 한다면, 리듀서는 각 액션의 행동을 정의한다고 보면 될것 같다.
액션 중에서 액션타입을 따로 정의하고는 하는데, 이것은 데이터의 아이디라고 이해하면 쉽다.

* 문제는 처음 정의된 것에서 추가 액션이 나오면 어떻게 되느냐 같다. 
* 그에 대한 문제 해결방법도 있는 것 같이니 한번 유심히 살펴보도록 하자. 

초기 설정이 끝났으면 각 클래스(페이지)에서 쓸때를 생각해야한다.
그것이 디스패치와 구독이다.
구독은 connct로 진행한다. 이제부터 내가 이해해야할 부분들이ㅏ.
초기 설정은 개발자들이 만날일이 거의 없을것 같다. 디스패치와 connect가 가장 많이 보게될 부분.

액션과 리듀서도 많이 추가할지도 모른다. 그때마다 메인 리듀서에 추가해야하는건가?


여기가 본편이다. 설정한것을 어떻게 쓰는지 알아보도록 하자.

올바른 리덕스를 사용하기 위해서는 라이브러리를 설치해야합니다.
> yarn add redux react-redux redux-actions immutable

우선 connect 함수에 대해서 이해할 필요가 있을 것 같다.
connect에는 3개의 파라미터가 있는데 제일 마지막것은 사용하지 않는다.
첫번째 ㅍㄹ미터는 state를 props에 연결한다.
두번째 파라미터는 액션을  props에 연결하는 것으로 정확히는 그 액션에 해당하는 리듀서부분을 리턴해준다. 액션을 받아서 리듀서를 호출하는 역할을 dispatch가 처리해준다.

예를 들어보자.

const mapStateToProps =(stat) =>({
    color : state.color,
    number : stat.number
})

const mapDispatchToProps = (dispatch) =>({
    onIncrement: () => dispatch(actions.increment()),
    onDcremnt: () => dispatch(actions.decrement()),
    onSetColor: () => {
        const color = gtRandomColor();
        dispatch(actions.setColor(color));
    }
})

const CounterContainer = connect(mapStateToProps, mapDispatchToProps(Counter);

이라고 되어 있으면 Counter에 파라미터에 있는 color, number, onIncrement(), onDecrment(), onSetColor()를 전달한다.

그래서 Counter에서는 클래스 선언시 다음과 같이 파라미터를 받을수 있다.
단, 보내는 파라미터명칭과 받는곳에서 명칭은 같아야한다. 순서로 받는게 아니다. 명칭으로 매칭되어진다.

const Counter =({number, color, onInCrement, onDecrement, onSetColor
}) =>{
    return (
        <div></div>
    )

}

액션과 리듀서를 만들때 handleActions와 createAction를 적극활용하자.
connect에서 bindActionCrators를 사용해서 dispatch부분을 줄여서 사용하자.

번외 - connect에 대해서 내식대로 이해해보기 

const CounterContainer = connect(mapStateToProps, mapDispatchToProps(Counter);

위의 것은 다음과 같다고 생각하면 쉬울것같다. 실제로 라이브러리 코딩도 저렇게 넘기지 않을까?

<Counter number={state.number}
                  color = {state.color}
                  onInCrement ={this.onInCrement } 
                  onDecrement = {this.onDecrement}
                  onSetColor = {this.onSetColor}
/>

번외2 - 컨테이너를 클래스 컴포넌트에서 설정하면 아래와 같이 하면된다.

class TodoListContainer eextnds Component{
    render(){
        return (
            <TodoList/>
        )
    }

}

export default connect(param1, param2)(TodoListContainer)

// 다른점을 아시겠나요? export가 자기 자신이며, 리턴값을 넣게 되었습니다. export에서 써야할 값을 return부분에  쓴것입니다.
// 개인적으로는 이게 더 깔끔해보이네요. 일관되어 보이구요..


리덕스의 변화를 보기위해서는 크롬의 확장 프로그램을 이용합니다.
그이름은 Redux DevTools입니다. 
스토어 생성할때 파라미터값도 넣어야 하므로 사용법은 다시 조사해봅니다.

state를 재정의할때 Immutable를 사용하ㅏㅂ니다. 배열을 쉽게 자르고 쉽게 값을 수정할수 있게 해줍니다. 자세한 사용법은 따로 조사해서 익힙시다.

액션과 리듀서 액션생성함수를 하나의 파일에서 하도록 합니다. 그걸 Ducks구조라고 합니다. 파일 많은걸 줄일수 있으니 적극활용합시다.

액션과 리듀서를 따로 코딩안해도 제네릭비슷한것으로 소스를 만들어주는 라이브러리ㅗ 존재합니다. redux-actions라고 합니다.
액션은 createAction으로 만듭니다. 
리듀스는  handleActions를 사용해서 만들어 줄수 있습니다.

대신에 일방적인 필터값을 가지고 있습니다. 액션은 type가 생기고 그 ㄷ음에 payload밑으로 모든 값을 넣게 됩니다.
{type: '',
 payload{
   index:'',
   color:'',
 }
}




순수 UI구조와 state를 가지고 있는 부분을 분리하는 거소 좋은 방법같다. 
순수 UI만 있는 클래스는 함수형 컴포넌트로 만들고, 안에 들어가 있는 곳에서 클래스형 컴포넌트를 쓰면 될것 같다.

UI를 담당하는 컴포넌트는 크게 두개로 또 뉠수 있다. 
전체적인 레이아웃을 담당하는 템플레이트와 일반 컴포넌트이다. 
> 기타적으로 css를 추가해야겠지만....
>> 메뉴별로 나오는 것도 보아야한다.

폴더에 index.js는 그 폴더를 대표하게 되는것 같다. 그래서 폴더를 임포트하면 index.js파일을 먼저 찾는것 같다.

컨테이너에서는 connect부분이 있고, 그 안에 뷰가 있게된다.
솔직히 컨테이너와 UI부분을 분리하면 파일만 늘어나는게 아닌가 생각이 든다. 하....
