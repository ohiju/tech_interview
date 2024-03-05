# 컴포넌트 LifeCycle

- React components는 create, render, DOM에 추가, 업데이트, 삭제될 수 있다. 이 모든 스텝들을 '컴포넌트의 생명주기(lifecycle)'라고 한다.

- lifecyle은 Mounting - Updating - Unmounting의 3단계를 거친다.

1. Mounting - 컴포넌트 호출
컴포넌트가 초기화되고 DOM에 놓이는 첫 순간으로 Mount 되지 않으면 화면에서 볼 수 없다.
constructor(), render(), componentDidMount() 메서드가 실행된다.
2. Updating - 상태 업데이트
state나 props의 상태 변화에 따라 컴포넌트가 업데이트 될 때
정적인 컴포넌트(예: 로고)를 제외하고 컴포넌트의 상태값이 변하거나, 다른 props가 컴포넌트에 전달될 때 업데이트 된다.
-render(), componentDidUpdate() 메서드가 실행된다.
3. Unmounting - 제거
컴포넌트가 DOM에서 삭제될 때
componentWillUnmount() 메서드가 실행된다.