# React

### react.js가 나온 이유

react.js는 UI를 interactive(상호작용)하게 만들어 준다.

react의 가장 멋진 점은 component를 새로고침 하는 것

### Before React

1. HTML을 만든다.
2. JavaScript에서 가져온다.
3. event를 감지한다.
4. 데이터를 업데이트한다.
5. HTML을 업데이트 한다.

이런 식으로 계속 event listener만들면 코드의 양이 엄청 많아진다.

### React Element

ReactJS의 규칙 중 하나는 HTML을 이 페이지제 직접 작성하지 않는것

→ 대신 JS코드를 이용

ReactJS: 어플리케이션이 interactive하도록 만들어주는 library

react-dom: library or package, 모든 React element들을 HTML body에 둘 수 있도록 해줌

render: React element를 가지고 HTML로 만들어 배치하는것(사용자에게 보여준다)

JS: HTML을 먼저 만들고 그걸 Javascript로 가져와서 HTML을 수정함

React.JS: 모든 것이 Javascript로써 시작함, 그 다음에 HTML이 된다.(이것이 핵심)

→ Javascript와 ReactJS를 사용하여 element를 생성할 때에는 ReactJS가 element를 생성한다. 이 말은 ReactJS는 업데이트가 필요한 element를 업데이트할 것이라는 말

→ 바로 ReactJS가 결과물인 HTML을 업데이트할 수 있다는 것

ReactJS는 유저에게 보여질 내용을 컨트롤할 수 있다.(핵심)

→HTML을 만들고 찾아서 가져오고 그러고 나서 업데이트 할 필요가 없다.(기존의 JS)

### JSX

JavaScript를 확장한 문법

React 요소를 만들 수 있게 해줌(HTML에서 사용한 문법과 흡사한 문법을 사용하여)

### State

state는 기본적으로 데이터가 저장되는 곳

함수로 변수값을 변경하면 항상 rerendering을 해줘야함 → setState 사용

바닐라JS에서는 span, div값들이 모두 업데이트되지만

ReactJS에서는 UI에서 바뀐부분만 업데이트해준다.

ReactJS는 이전에 렌더링된 컴포넌트는 어떤거였는지 확인한다.

→ 아주 interactive한 어플리케이션을 만들 수 있다.

React.useState()가 배열이기 때문에 변수선언할때 [state,setState]의 형식으로 선언해준다.

→ [counter, modifier]의 형식

왜 counter를 직접바꾸지 않고 modifier를 이용해서 바꿔야할까?

→ counter를 직접바꾸면 항상 직접 리렌더링 해줘야됨 (ReactDOM.render(<APP />, root)

→ modifer를 이용하여 값을 바꿔주면 modifier함수 안에서 counter의 값을 바꿔주고 리렌더링을 자동으로 해줌

### State Functions

setCouter(couter + 1);

setCounter((current) ⇒ current + 1); → 더 안전한 방법 (현재 state를 기반으로 계산하고 싶다면)

리액트가 이 current가 확실히 현재 값이라는걸 보장해줌

### Props

Props는 부모 컴포넌트로부터 자식 컴포넌트에 데이터를 보낼 수 있게 해주는 방법

컴포넌트의 매개변수를 이용하여 값을 바꿀 수 있어 컴포넌트의 재활용가능

리액트 컴포넌트의 onClick은 이벤트리스너가 아닌 props이다.

props가 useState에 의해 값이 바뀌어 re-render될 때 바뀌지 않은 컴포넌트까지 re-render될 필요는 없다.

→ React.memo를 이용하면 props가 바뀌지 않은 컴포넌트는 re-render되지 않는다.

→ 어플리케이션의 성능을 높일 수 있다.

const MemorizedBtn=React.memo(Btn)

propTypes: props의 타입이 뭐고 어떤 모양이어야 하는지를 설명해줄수 있다.

Btn.propTypes={

text: PropTypes.string,

fontSize: PropTypes.number,

};

.isRequired: props를 확실히하고 싶을때, 즉 컴포넌트가 해당하는 prop들만을 정확히 갖고 render될 것이라는 걸 확실히하고 싶을때 사용 (PropTypes.string.isRequired)

.module.css : react에서 css코드 작성 가능

그리고 <h1 className={styles.xxx}> 이런식으로 적용 가능

### Effects(react에서 가장 중요한 부분)

how react.js works: state의 값이 바뀌면 re-render

계속 re-render될 때마다 반복실행되어도 괜찮은 코드가 있을 수 있음

하지만 가끔은 component가 처음 render될 때만 코드가 실행되길 원할 수 있음

→ 첫번째 render에만 코드가 실행되고, 다른 state 변화에는 실행되지 않도록 하고 싶음

(ex: api를 계속 불러오는 건 성능 저하가 크다)

input을 사용하여 글자를 타이핑할 때마다 re-render되면 성능이 매우 저하된다.

→ 특정 코드들이 첫번째 component render에서만 실행되게 하고 싶다. state가 변화하더라도 re-render되지 않는다. → useEffect

### useEffect

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/57593e4b-c691-4a20-8347-78f1ef249fef/Untitled.png)

useEffect는 두개의 argument를 가지는 function

첫번째 argument는 딱 한번만 실행하고 싶은 코드

두번째 argument는 Deps

useEffect function은 코드가 딱 한번만 실행될 수 있도록 보호해준다.

### Deps

useEffect의 두번째 argument

코드의 특정한 부분만이 변화했을 때 원하는 코드들을 실행하고 싶을때 사용

[ ] 안의 값이 변화될 때마다 코드를 실행시키고 싶은 state를 입력

→ 빈 array를 써주면 코드가 단 한번만 실행되는 이유

return 안에 js 코드를 쓰고 싶으면 { }이용

cleanup: useEffect로 함수의 생성과 소멸을 알 수 도 있다. useEffect안의 return을 이용하여
