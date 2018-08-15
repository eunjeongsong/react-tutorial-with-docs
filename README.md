# Tutorial: Intro-to-React
[Tutorial: Intro to React](https://reactjs.org/tutorial/tutorial.html) 를 따라 튜토리얼 진행

- [Setup for the Tutorial](#setup-for-the-tutorial)
- [Overview](#overview) - React 기초에 대해 배우기(components, props, and state)
- [Completing the Game](#completing-the-game) - React 개발에 가장 공통적인 기술들에 대해 배우기
- [Adding Time Travel](#adding-time-travel) - React의 독특한 강점에 대해 깊게 알기
<br/>




## Setup for the Tutorial
이 튜토리얼을 완료하기위한 두가지 방법이 있다.
- 브라우저에서 코드를 작성하거나, 
- 당신의 컴퓨터에 로컬 개발환경을 설정해 진행하는 방법이다.


### Setup Option 1: Write Code in the Browser
이것은 가장빠른 방법으로 튜토리얼을 시작할 수 있다.    
새로운 탭에서 [Starter_Code](https://codepen.io/gaearon/pen/oWWQNa?editors=0010) 를 오픈한다.이 화면에서 리액트 코드와 비어있는 tic-tac-toe 게임보드를 화면에 보여주고, 코드를 수정할 수 있다.
이것을 사용하면 'Setup Option 2'를 건너뛰고, [Overview](#overview) 섹션으로 넘어가는 것이 가능하다.


### Setup Option 2: Local Development Environment
로컬 개발환경을 설정하는 것은 선택사항이며 이 튜토리얼에서 반드시 요구되는 것은 아니다.
당신이 선호하는 텍스트 에디터를 사용하여 로컬에 구성하기 위한 방법이다.    
<br/>




## Overview
[Setup](#setup-for-the-tutorial) 단계를 진행했다면 리엑트에 대해 알아보자!


### What Is React?
React 는 사용자 인터페이스를 만들기 위한 선언적이고, 효율적이며 자바스크라이브러리다. 당신이 ‘components’ 라고 불리는 작고 독립적인 코드 조각으로 복잡한 UI 를 구성하는것을 가능하게 해준다. React 는 여러 종류의 컴포넌트를 가지지만, 이 튜토리얼에서 우리는 React.Components 의 subClasses 로 시작할 것이다.    
```js
class ShoppingList extends React.Component {
  render() {
    return (
      <div className="shopping-list">
        <h1>Shopping List for {this.props.name}</h1>
        <ul>
          <li>Instagram</li>
          <li>WhatsApp</li>
          <li>Oculus</li>
        </ul>
      </div>
    );
  }
}

// Example usage: <ShoppingList name="Mark" />
```
우리는 컴포넌트라는 것을 사용하여 우리가 화면에서 보여주고 싶은것을 React 에게 전달한다. 우리의 데이터 변경이 있을때 React 는 효율적으로 업데이트하고 우리의 컴포넌트를 리랜더링한다.    

위에 ShoppingList 는 React 컴포넌트 클래스 또는 React 컴포넌트 타입이다.
컴포넌트는 props 라고 불리는 파라미터를 사용하고, 리랜더 메소드를 통해 보여주려는 뷰의 계층구조를 반환한다.
대부분의 리엑트 개발자는 JSX 라고 불리는 특별한 구문을 사용하고, 이것은 더 쉽게 코드를 작성할 수 있게 해준다.    
**\<div \/>** 구문은 아래 코드와 같이 **'React.createElement(‘div’)'** 로 transformed 되어 빌드 된다.
```js
return React.createElement('div', {className: 'shopping-list'},
  React.createElement('h1', /* ... h1 children ... */),
  React.createElement('ul', /* ... ul children ... */)
);
```
만약 당신이 궁금하다면 [API reference](https://reactjs.org/docs/react-api.html#createelement)를 참고하면되지만, 이 튜토리얼에서는 JSX 를 사용할 것이다.
JSX는 JavaScript의 모든 기능을 제공한다. JSX 내 중괄호 안에 JavaScript 표현식을 넣을 수 있다.


### Inspecting the Starter Code
너가 브라우저를 이용해 튜토리얼을 진행하고 있다면 새로운 탭에서 [Starter_Code](https://codepen.io/gaearon/pen/oWWQNa?editors=0010)를 열고, 너의 로컬 컴퓨터에서 진행하고 있다면 src/index.js 안의 코드를 열어봐라.

코드를 살펴보면 세가지 React 컴포넌트로 구성되어 있다는 것을 알 수 있다.
- Square
- Board
- Game

Square 컴포넌트는 싱글 \<button\> 을 렌더하고, Board 컴포넌트는 9개의 Square 를 렌더한다.
Game 컴포넌트는 Board 를 placehoder values 와 함께 렌더하고, 우리는 나중에 수정할 것이다.
현재는 interactive 컴포넌트가 없다.


### Passing Data Through Props
