# Props

- Props는 Properties의 줄임말이다.
- Props는 컴포넌트 외부에서 데이터를 제공받는다.
- 상위 컴포넌트가 하위 컴포넌트에 값을 전달할 때 사용한다.(단방향 데이터 흐름)
- 프로퍼티는 수정할 수 없다.

## 왜 Props를 사용할까?

가장 큰 이유는 **컴포넌트의 재사용을 높이기 위해서**이다.<br>
상황에 따라서 데이터를 전달받아 데이터에 맞게 UI를 구현할 수 있다.<br>

```
class App extends Component {
  handleClick = event => {
    console.log(event);
  };

  render() {
    return <LikeButton title={'Like'} onClick={this.handleClick} />
  }
}
```

`App` 부모 컴포넌트에서 `LikeButton`컴포넌트에 `title`과 `onClick`을 인자로 전달해주었다.

```
class LikeButton extends Component {
  state = {
    numberOfLikes: 0,
  };
  render() {
    console.log(this.props);
    console.log(this.state);
    return <button>{this.state.numberOfLikes}</button>
  }
}
```

전달된 인자들이 오브젝트로 묶어져서 `LikeButton`컴포넌트 안에서 `this.props`로 할당된다.
