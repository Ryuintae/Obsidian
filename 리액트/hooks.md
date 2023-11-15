
# State 와 hook

## State 란?

- state란 리액트에서 이벤트에 의해 변경되는 동적인 값입니다.
- 버튼을 클릭하는 onClick 이벤트, input 입력으로 인해 발생하는 onChange 이벤트에 의해 입력값이 변경된 경우 사용됩니다.
- props는 부모 컴포넌트가 설정하는 값이며 읽기 전용이지만, state는 하위 컴포넌트도 데이터를 변경할 수 있습니다.


> [!tip] 훅의 기본조건
> 1. Hooks는 React 함수 컴포넌트 내에서만 호출할 수 있습니다.
> 2. 후크는 구성 요소의 최상위 수준에서만 호출할 수 있습니다.
> 3. Hooks는 조건부일 수 없습니다


## **Hook은 계층의 변화 없이 상태 관련 로직을 재사용할 수 있도록 도와줍니다.**


## useEffect Hook
#### 🚀 **useEffect()란?**

useEffect() 함수는 React component가 렌더링 될 때마다 특정 작업(Sied effect)을 실행할 수 있도록 하는 리액트 Hook입니다. 

여기서 Side effect는 component가 렌더링 된 이후에 비동기로 처리되어야 하는 부수적인 효과들을 뜻합니다. 

이러한 기능으로 인해 함수형 컴포넌트에서도 클래스형 컴포넌트에서 사용했던 생명주기 메서드를 사용할 수 있게 되었습니다.

`useEffect`는 기본적으로 다음 두 가지 주요 시점에서 실행됩니다:

1. 컴포넌트가 마운트(처음 화면에 나타남)된 후
2. 컴포넌트가 업데이트(상태나 props 변경 등으로 재렌더링)된 후


* 마운트
* 업데이트
* 언마운트


## useContext
![[Pasted image 20231114155111.png]] ![[Pasted image 20231114155202.png]]

>[!tip] 쉽게 생각하는 사용해야 하는 이유
>props 를 글로벌하게 사용 할 수 있게 도와준다.
>props 는 부모 자식 단방향 관계로 이어지지만 자식에서 자식이 props 를 사용할 때  수정할 때 큰 문제가 생길수도 있기 때문이다.
>

**useContext**는 기존의 React에 존재하는 Context를 더 편하게 사용할 수 있게 해주는 역할을 한다. 
따라서 useContext에 대해서 다루기 전에 우선 React에서 **Context란** 무엇인지부터 다뤄야 한다! 🏃‍♀️

### Context 란?

React 공식 문서에 쓰여있는 설명에는,
_' context를 이용하면 단계마다 일일이 props를 넘겨주지 않고도 컴포넌트 트리 전체에 데이터를 제공할 수 있습니다 '_ 라고 적혀있다.  

>[!tip] useContext 를 사용해야 하는 상황
>일반적인 React 어플리케이션에서 **데이터는 props를 통해서 부모에서 자식**에게 전달 되지만, 
>어플리케이션 안의 여러 컴포넌트들에게 props를 전달해줘야 하는 경우 context를 이용하면 명시적으로 props를 넘겨주지 않아도 값을 공유할 수 있게 해주는 것이다.  
>   
> **한마디로 데이터가 필요할 때마다 props를 통해 전달할 필요가 없이 context 를 이용해 공유한다!**

context API를 사용하기 위해서는 `Provider` , `Consumer` , `createContext` 이렇게 세가지 개념을 알고 있으면 된다.

- `createContext` : context 객체를 생성한다.
- `Provider` : 생성한 context를 하위 컴포넌트에게 전달하는 역할을 한다.
- `Consumer` : context의 변화를 감시하는 컴포넌트이다. (useContex 와 동일한 역할 )

### Context 예제

#### App.js

```js
import React, { createContext } from "react";
import Children from "./Children";

// AppContext 객체를 생성한다.
export const AppContext = createContext();

const App = () => {
  const user = {
    name: "김채원",
    job: "가수"
  };

  return (
    <>
      <AppContext.Provider value={user}>
        <div>
          <Children />
        </div>
      </AppContext.Provider>
    </>
  );
};

export default App;
```

#### Children.js

```js
import React from "react";
import { AppContext } from "./App";

const Children = () => {
  return (
      <AppContext.Consumer>
        {(user) => (
          <>
            <h3>AppContext에 존재하는 값의 name은 {user.name}입니다.</h3>
            <h3>AppContext에 존재하는 값의 job은 {user.job}입니다.</h3>
          </>
        )}
      </AppContext.Consumer>
  );
};

export default Children;
```

![](https://velog.velcdn.com/images%2Fjminkyoung%2Fpost%2Ffc6b239b-417b-455a-8951-894c2ddcb46d%2Fimage.png)  
이 예제에선 하나의 컴포넌트에서만 context를 사용했지만 코드가 늘어나면 여러 컴포넌트에서 사용이 가능하지만 코드가 점점 더러워지는 문제가 생길 것이다.

### useContext 를 적용하면

#### Children.js

```js
import React, { useContext } from "react";
import { AppContext } from "./App";

const Children = () => {
  // useContext를 이용해서 따로 불러온다.
  const user = useContext(AppContext);
  return (
    <>
      <h3>AppContext에 존재하는 값의 name은 {user.name}입니다.</h3>
      <h3>AppContext에 존재하는 값의 job은 {user.job}입니다.</h3>
    </>
  );
};

export default Children;
```

App.js 에서 Context를 생성하고 Provider를 통해 전달하는 코드는 그대로지만 Children.js에서 `AppContext` 를 사용하는 과정에서 `<AppContext.Consumer>` 같은 코드를 사용해서 복잡하게 작성하지 않고 `const user = useContext(AppContext)`를 통해 Context를 불러 온 후 바로 사용이 가능하게 바뀌었다.  

> 따라서 useContext 를 사용하면 기존의 Context 사용 방식보다 더 쉽고 간단하게 Context를 사용이 가능하고, 앞서 다뤘던 useState, useEffect와 조합해서 사용하기 쉽다는 장점이 있다 ✨