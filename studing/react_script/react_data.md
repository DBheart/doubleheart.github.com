리액트의 데이터 관리는 두개로 압축된다.
props와 status이다.

# props
props는 부모 컴포넌트에서 건네받는 속성값을 말한다.
자식 컴포넌트에서는 수정이 불가능한 값이다.
아래의 코드를 보도록 하자.

```
//부모 컴포넌트
<MyComponent name="React"/>

//자식 컴포넌트
<div>
    안녕하세요, 제 이름은 {this.props.name}입니다.
</div>
```

## 주요사항
* Component를 확장받은 클래스에서만 사용되겠지?
> 확인 안해본 사항이다. 다음에 확인해 보자.
* 부모에서는 속성값으로 내보내면 되고, 자식 컴포넌트에서는 this.props.속성 으로 사용할수 있다.
* 부모 컴포넌트에서 값을 입력안했을때를 대비해서 자식 컴포넌트에서는 기본값을 줄수도 있다.
> 컴포넌트.defaultProps ={}
>> 위와 같이 지정하면된다 {}에 속성값에 값을 넣으면 된다. 
>>> name="기본이름"과 같이

> 아래 방법말고 static defaultProps ={}로 설정할수도 있다.
>> Types설정은 static proTypes ={}로 설정한다.
>>> proTypes로 설정할수 있는것은 찾아보자. 
```
//다음과 같이 {}로 import한 것은 react에 있는 Component를 Component로 쓰겠다는 의미가 있다.
import React,{Component} from 'react';

//위에 {Component}라고 지정을 안했으면 React.Component라고 써야한다.
class MyComponent extends Component{
    (...)
}
MyComponent.defaultProps ={
    name:'기본이름'
}

//props의 속성들의 타입을 다음과 같이 설정할수도 있다.
MyComponent.propTypes = {
    
    name:PropTypes.string 
    age:PropTypes.number.isRequired //필수적으로 프로퍼티를 넣어야할때 isRequired를 쓰도록 한다.
}
exprot default MyComponent;
```
# state
* state의 실제 사용은 리덕트 라이브러리를 사용해서 사용한다.
* 초기값은 constructor에서 지정하며 this.state ={필드:필드값}로 만든다.
> constructor에서 벗어나서 사용할수 있다. 
* 수정값은 this.setState({필드:필드값}) 을 사용한다.
* state값을 바꾸면 화면을 다시 그리게 된다. 렌더링이 다시 된다는 말입니다.

```
class MyComponent extends Component{
    (...)
    constructor(props){
        super(props);
        this.state = {
            number:0,
            test:'test'
        }
    }
}

exprot default MyComponent;
``` 

```
class MyComponent extends Component{
    (...)
    state = {
        number :0,
        test:'test'
    }
}

exprot default MyComponent;
``` 

위의 코드는 state가 저렇게 만들어진다는 예시입니다.
실제는 리덕트를 사용하기 때문에 다릅니다. 다음 확인때에 볼것입니다.

