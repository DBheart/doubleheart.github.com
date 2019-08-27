모든 개발이 그렇듯이 개발을 위해서는 프로젝트 구조를 만들어 놓아야한다. 리액트에서 누가 만들었는지는 모르겠지만 쉽게 기본적으로 만들수 있게 라이브러리를 제공하고 있다.

리액트의 기본문법은 컴포넌트를 사용한것과 컴포넌트를 사용하지 않는 순수 함수만으로 구성된 함수형 컴포넌트 두개로 구분할수 있다.

함수형 컴포넌트는 라이프사이클과 state등이 제거된 상태이므로 순수 화면을 그릴때 주로 사용한다. 되도록 함수형 컴포넌트쓰는것을 권장합니다.

<리액트 프로젝트 만들기>
* craete-react-app 설치 : npm or yarn으로 설치하도록 하자
> yarn global add create-react-app
* create-react-app 프로젝트명
> create-react-app hello-react
* 실행, 실행은 개발툴에서 하도록 하자.
>> cd hello-react
>>> yarn start
* 개발툴 각종 확장 프로그램 설치 : 여기서는 VS Code를 위주로 이야기 해본다.
> ESLint, Relative Path, Guides, Reactjs code snippets

<리액트 코드>
리액트는 ES6의 클래스에 jsx문법이 올라가도록 되어있다.
> 'rcc' 단축코드를 입력하여서 만들면 콤포넌트를 기반으로 만들어 진다.
>> rcc외에 다양한 단축코드가 있으니 시도해보자.
```
//기본코드는 아래와 같이 나온다.
import React, {Component} from 'react';

class App extends Component{
    render(){ //여기서부터가 jsx문법이라고 할수 있다.
        //render과 return사이에는 자바스크립트 문법을 쓸수 있습니다. 
        //물론 render함수 밖에서도 사용할수 있습니다. 
        //자바스크립트 문법은 ES6문법에 맞게 사용하기를 권장합니다.
        //return 아래에는 하나의 태그만 존재해야한다. 두개가 존재하면 오류가 발생한다.

        // jsx의 주석 : {/*  */}
        //{}에서 자바스크립트를 쓰더라도 if문은 안됩니다. 대신 삼항연산자는 됩니다.

        let temp ='당신을 사랑합니다.'
        return( 
            <div>{/* 보통 첫 태그는 Fragment를 쓰도록 합시다. */}
            
            {/* jsx문법아래 그러니까 return안에서 자바스크립트는 {}를 감싸서 사용합니다. */}
                테스트 {temp} 
            </div>
        );
    }
}

export default App; //외부에서 import하기위해서는 꼭 마지막에 export를 넣어야 한다.
```


* ref:DOM이 상황에 따라서 컴포넌트를 사용할수 있는 단초가 되지 않을까?
> 아니네... 그냥 안쓰는게 좋은 구조가 맞는것 같다.
>> 부모 컴포넌트에서 자식 컴포넌트의 함수를 가져다 쓸때 사용한다.

* ES6의 비구조화 할당 문법
> 왼쪽에 있는 속성을 오른쪽의 변수값에 대입하는 것입니다. 속성명과 변수명이 일치하는 것만 매칭합니다.
```
class ScrollBox extends Component{
    scrollToBottom = () =>{
        const {scrollHeight, clientHeight} = this.box;

        /*
        위의 코드는 비구조화 할당 문법을 사용했습니다. 
        다음 코드와 같은 의미를 지니고 있습니다.

        const scrollHeight = this.box.scrollHeight;
        const clientHeight = this.box.clientHeight;
        */

    }
}
```

* 화면을 꾸미는 CSS는 3가지의 사용방식이 있습니다. 가장 기본적인것은 css파일을 사용하는 형태입니다. 그외에 Sass와 styled-components를 사용하는 방법이 있습니다.

* 디렉토리에 index.js를 생성한후에 import할때 그 디렉토리를 import하면 index.js를 가져오는 구조로 되어있다.
> 확인해보자.

* 전개 연산자
* Object.assign 함수
* onContextMenu 이벤트
> onContextMenu를 Dom의 이벤트로 줄수 있는데 리액트에서 제공하는 것같다. 마우스 오른쪽 버튼을 눌렀을때 메뉴가 열리는 이벤트라고 한다. 이때 e.preventDefault() 함수를 호출하면 메뉴가 열리는 것을 방지하고 스크립트만 실행할수 있게 한다.