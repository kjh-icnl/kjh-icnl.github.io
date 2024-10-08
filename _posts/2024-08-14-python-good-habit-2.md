---
title: (Python) 좋은 코딩 습관 2편
date: 2024-08-13 15:10:00 +0900
categories: [python, habit]
tags: [python, habit, coding, programming]
---

# 좋은 코딩 습관 Python 2편

오늘 소개할 Python의 좋은 코딩 습관은 ***할당 코드를 한 줄로 표현하기***입니다. 이게 무슨 의미냐? 당연히 할당 코드를 작성할 때는 한 줄로 쓰지 않아? 뭐 다른게 있어?라고 생각할 수도 있다. 하지만, `if` 또는 `for`와 같은 조건문, 반복문이 나온다면 여러줄이 하나의 할당코드가 될 수 있다. 이러한 경우에, 한 줄로 간단히 작성하는 습관을 들인다면, 좋은 코드를 작성하는 데에 도움이 될 수 있다.

## 예시

먼저, 말하고자 하는 상황을 예시로 보는 것이 이해하기에 편할 듯 싶다. 각각 위아래의 코드는 조건문과 반복문에서 변수에 값들을 할당하는 예시들이다.

```python
num: int = int(input('input a number'))
result: str = None

if num%2 == 0:
    result = 'even'
else:
    result = 'odd'
```

```python
lst = []
for i in range(1, 100, 3):
    lst.append(i)
```

제가 말하고자 하는 바가 이해되시나요? 이러한 코드들을 1~2 줄로 매우 짧게 표현을 변화시키고자 하는 바가 제가 이번 습관에서 말하고 싶은 바입니다.


## 조건문

### 목적 (purpose)

1줄로 코드를 바꾸려고 하는 노력이 대체 왜 필요할까? 나는 이런 질문을 던지고 싶다. '코드를 길게 짰다고 해서 잘 짠 코드일까?', '이런 습관의 요구는 리팩터링과 유지보수의 목적이 전부일까?' 아니다. 코드를 길게 몇 천줄, 몇 만줄, 몇 십만줄 이렇게 짰다고 하면, '어떻게 그렇게 길게 짤 수가 있지?'라는 반응과 함께 '대단하다'라는 감정이 드는가? 정말 대단한 코드일 수 있다. 하지만, 의미없는 코드만 덩그러니 남겨있는 경우도 많다. 결론적으로, 이러한 습관의 요구는 결국 쓸모없는 코드를 해석하는 노력을 최대한 줄여서 디버깅에 드는 시간을 줄이자는 목적이 굉장히 강하게 들어있다. 

### 축소 코드 (concise form)

실제로 살펴보자. 사실 조건문 예시 코드는 파악하기 어렵지 않다. 숫자를 받아들이고, 그 숫자가 홀수인지 짝수인지 구분한다. 이 간단한 코드를 해석하고자 6줄의 코드를 우리는 해석해야한다. 이건 텍스트 낭비, 코드라인 낭비, 노력 낭비가 된다. 축소 코드를 살펴보자.

```python
num: int = int(input('input a number'))
result: str = 'even' if num%2 == 0 else 'odd'
```

훨씬 간단하고, 해석하기에도 편하지 않은가? 쓸모없는 코드 라인들이 모두 사라졌다. 이렇게 축소된 코드의 형태로 코딩을 하는 것이 더 좋은 코드를 짜는 데에 도움이 될 수 있다. 물론, 익숙하지 않아서, 간단하게 보이지 않고 해석하기에 불편해보일 수 있다. 하지만, 익숙해진다면, 가장 처음 보여주었던 예시 코드가 더러워보이는 지경에 이를 수도 있다.

### 장단점

장단점은 명확하다. 장점은 위에서 언급한 단점을 없애준다. 단점은 `elif`를 통한 다조건이 불가능하다. `if~elif~else`를 써야한다면, 어쩔 수 없이 축소 형태는 사용하지 못한다.

## 반복문

### 축소 코드 (concise form)

반복문의 경우, 축소된 코드부터 확인해보자.

```python
lst = [i for i in range(1, 100, 3)]
```
정말 훨씬 더 쉽고, 간편하게 할당할 수 있다. 물론 이 방법은 `iterator`에 대해서는 `for`를 통해 실현가능한 코드이다. 이는 `list.append`함수를 계속해서 호출해 코드가 더 느려지는 상황을 방지할 수 있는 매우 좋은 코드가 된다. 이는 반복을 통해 계속해서 원소를 추가하는 옛 방식보다 훨씬 메모리 그리고 실행속도 측면에서 많은 이점이 있다.


> 물론, 아래처럼
> ```python
> list(range(1, 100, 3))
> ```
> 으로도 가능하지만 이건 내가 말하고자 하는 포인트가 아니니 알아서 패스하자.


## 마치며

오늘은 할당 코드 문법을 간단한 형태로 표현하는 방법을 알아보았다. 이 습관이 잘 안 받아들여지겠지만, 요즘 **코딩 좀 한다싶으면** 다 이 문법을 쓰고 있는 경우를 볼 수 있다. 또는 잘 만들어진 최신의 프레임워크나 모듈, github repository를 뜯어보면, 이렇게 짜여진 경우가 굉장히 많음을 알 수 있다. 물론 이건 습관이므로, 무조건 이렇게 해야한다는 강요는 할 수 없다. 하지만, 이 습관을 통해 다른 사람들과 코드를 통해 더욱 효과적이고 바람직한 방법으로 소통할 수 있게 되었으면 좋겠다. 다들 더욱 좋은 코드를 짤 수 있는 사람들이 되었으면 좋겠다.