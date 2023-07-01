# React Component

1. React basic library
  - react-dom
    * 리액트 컴포넌트를 htmlElement와 연결
    * ReactDOM.render()
  - react
    * 리액트 컴포넌트 생성
  - CDN을 통한 리액트 라이브러리 사용
    ```html
      <script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
      <script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
      <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    ```
  - 실습 준비
    * /what-is-react 폴더 생성
    * npm init -y 파일 생성
    * index.html 생성 후 양식 완성
    * cdn
      - react
      - react-dom
      - babel
  
  - 기존의 프론트엔드
    * html로 문서 구조 정의
    * css로 스타일 저으이
    * javascript로 DOM을 조작
  - 컴포넌트를 활용한 프론트엔드
    * 컴포넌트를 정의
    * 실제 DOM에 컴포넌트를 정의

2. React Component
  - Hooks(?) 이전
    * 컴포넌트 내부에 상태가 존재 -> class
    * 컴포넌트 내부에 상태가 없음 -> 라이프 사이클 사용 -> class
    * 컴포넌트 내부에 상태가 없음 -> 라이프 사이클 없음 -> function
  - Hooks 이후
    * class 
      - react 임포트
      - 정의

        ```html
          class ClassComponent extends React.Component {
            // render() 정의
            render() {
              return <div>Hello</div>;
            }
          }
        ```

      - 사용
     
        ```html
          ReactDOM.render(
            <ClassComponent />,
            document.querySelector('#root')
          )
        ```

    * function 
      - react import
      - 정의에는 2가지 방법이 존재
        * function FunctionComponent () { return }
        * const FunctionComponent = () => { return} 
      - 사용
        * ReactDOM.render(<FunctionComponent />, document.querySelector())

3. React.createElement Component
  - ReactDOM 을 이용하면 자식 태그 요소로 값을 넣게 됨
  - createElement의 요소로 React.Fragment를 넣게 되면 태그가 없이 값 삽입이 가능
  - 하지만 태그의 부모 자식 관계가 복잡한 경우는 어떻게?

4. JSX
  - 작성한 html 코드를 순수하게 실행할 수 있는 자바스크립트 -> babel
    * 과거의 브라우저도 이해할 수 있게
  - jsx 코드도 순수하게 실행할 수 있는 자바스크립트 -> babel
  - 태그의 구조를 babel이 해석해 자식의 요소로 지정
  - babel 과 같은 컴파일 과정에서 문법적 오류를 인지하기 쉽다
  - jsx 문법
    * 최상위 부모 요소가 하나여야 한다. -> 병렬 불가
    * 최상위 요소를 리턴하는 경우 ()로 감싸야 한다.
    * 자식들을 바로 랜더링 하고싶으면 <>자식들</>로 사용 -> Fragment
      - 병렬의 최상위 부모요소가 있을 떄 <></> 로 최상위를 만들어 주면 병렬 구조 사용 가능
    * javascript 표현식은 {표현식}
    * if 문 사용 불가
      - 삼항 연산자 혹은 &&를 사용
    * style 을 이용해 인라인 스타일링 가능
    * className을 사용해 class에 적용 가능
    * 자식 요소가 있으면 닫고 없으면 열면서 닫기

5. Props and State
  - Props : 컴포넌트 외부에서 컴포넌트에게 주는 데이터
  - State : 컴포넌트 내부에서 변경할 수 있는 데이터
    * Props 와 State의 변경이 발생하면 랜더를 다시 실행
  - Render() : 컴포넌트를 그리는 방법을 기술하는 함수
    * Props and State 를 바탕으로 컴포넌트를 그린다. 
    * 위의 두 개가 변경이 되면 컴포넌트를 다시 그림
  - ReactDOM 에서 직접 <Component message=""/>로 데이터 전달 가능
  - function Component
    * jsx 사용
    * props를 파라미터로 사용 > 그 안의 객체를 사용
    * ReactDOM.render() 사용하여 props로 데이터 전달 가능
  - class Component
    * class Component extends React.Component 상속
    * render() 사용
    *  Component.defaultProps 객체 사용 > 데이터 전달 > 클래스 / 함수 전달 방법 둘다 사용가능
      - class Component 안에 static defaultProps 객체로 데이터 전달도 가능 > 클래스만 사용 가능
  - State는 Class에서만 사용
    * 항상 객체로 사용
    * state = {} 안에 값을 지정 하는 방법
    * 생성자 함수를 통한 방법
      - constructor(props) { super(props); this.state = {count: 0}; }
    * hook을 사용해 state의 값을 변화 시켜줄 수 있다. 
      - 아직 hook이란것은 잘모르지만 방식은 그러하고 추후 Component Lifecycle에서 더 학습 진행

6. Event Handling
  - HTML DOM 에 이벤트가 발생하면 그에 맞는 변경이 일어나야 함
  - JSX로 이벤트 설정 가능
    * return 을 사용 할떄 () 소괄호를 묶어야 된다. 중요
  - camelCase 로만 사용 
    * onClick, onMouseEnter
  - event에 연결된 javascript code는 함수이다.
    * event = {함수}
  - 실제 DOM 요소들에만 사용 가능 
    * 리액트 컴포넌트에 사용하면 props 로 전달
  - function Component() {} 구현
    * 태그의 속성으로 onClick 이벤트 호출
  - class Component {} 구현
    * 태그의 속성으로 onClick 이벤트 호출
    * state 객체를 정의
    * this.setState로 state값으로 전달 
      - 현재는 인라인으로 직접 메소드를 작성
      - 메소드를 따로 분리할 수 있다.
      - 분리를 하면 this.click이 바인딩 되지 않는다. > 생성자 함수를 사용해 바인딩 하거나 간단히 메소드를 화살표 함수로 바꾸면 된다.
      - ~~이해가 잘안된다 흑흑~~

7. Component Lifecycle 
  - 리액트 컴포넌트는 탄생부터 죽음까지 여러지점에서 개발자가 작업이 가능하도록 메소드를 오버라이딩이 가능
  - Declarative
    * 탄생 > 변경 > 죽음
      - initialization > mounting > updation > unmounting
  -  Component 생성 및 마운트 (v16.3 이전 기준)
    * constructor
    * componentWillMount
    * render (최초 랜더)
    * componentDidMount
  -  Component props, state 변경 (v16.3 이전 기준)
    * componentWillReceiveProps
      - 파라미터 > nextProps
      - props를 새로 지정 했을 때 바로 호출 > state 변경에는 반응하지 않음
        * 만약 props의 값에 따라 state 를 변경하면 setState를 이용해 변경 
        * 그럼 각 이벤트로 각각 가는것이 아니라 한번에 변경됨(?)
    * shouldComponentUpdate
      - 파라미터 > nextProps, nextState
      - return 값이 true -> render 할 준비 / false -> render 할 준비 하지 않음
      - 다시 말해 아래의 WillUpdate, DidUpdate가 실행되지 않는다.
      - props, state 둘중 하나이상 변경이 된다면 > newProps and new State를 인자로 호출
      - return 타입은 boolean
      - 이 함수를 구현하지 않으면 default value = true
    * componentWillUpdate
      - 컴포넌트가 재 랜더링 되기 직전에 호출
      - setState 같은 것 사용 불가
    * render
    * componentDidUpdate
      - 컴포넌트가 재 랜더링을 마치면 호출
  - Component Unmount (v16.3 이전 기준)
    * 기존 렌더함수를 실행하며 호출했단 setInverval()을 언마운트시 clearInterval 함수를 불러오며 종료
  - Component 라이프 사이클 변경 (v16.3)
    * constructor
      - ~~componentWillMount~~ > getderivedStateFromProps
      - static 명시
      - return 명시 (없을 시 null 명시)
        * props를 변경도 가능 
        * 시간의 흐름에 변경되는 props에 따라 쓰일 때도 있음
    * render
    * componentDidMount
  - Component Props and state Update (v16.3)
    * ~~componentWillReceiveProps~~ > getDerivedStateFromProps
    * shouldComponentUpdate
    * render
    * ~~componentWillUpdate~~ > getSnapshotBeforeUpdate (dom 에 적용)
    * componentDidUpdate
  - Component unmount
    * componentWillUnmount (v16.3)
---------------------------------------------------------------------------------------

# 현재 강의를 나가는 수준이 어려워 차후 다시 돌아올 예정 T_T