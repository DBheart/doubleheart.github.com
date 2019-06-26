
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
