# [UI Seriese] 03 Breadcrumb

## 서론

* Breadcrumb 란?
  * Breadcrumb 는 `빵부스러기` 란 뜻 ( 헨젤과 그레텔에서 따온 용어 )
  * 사이트나 웹 앱에서 유저의 현 위치를 보여주는 부차적인 내비게이션 시스템
  * 유저에게 `맥락 정보`의 훌륭한 소스가 되며, 이에 따라 유저가 다음 질문에 대한 답을 찾을 수 있도록 유도
    * 내가 어디서 왔으며, 어디로 갈 수 있는가를 알려주며 어디로 가야할지에 대한 힌트를 주는 것
    * 예시) 쇼핑몰 카테고리 브레드크럼을 통해 유저가 마음에 들지 않으면 쉽게 상위 카테고리로 이동할 수 있게함
* 장점
  * 첫째, 유저가 상위 페이지로 가기 위해 취해야 하는 행동의 수가 줄어듦
  * 둘째, 최소한의 공간을 차지함
    * 링크가 걸린 텍스트를 가로로 펼쳐서 보여주기 때문
  * 셋째, 유저가 잘못 이해하거나 조작할 일이 절대적으로 적음
* 언제 사용하나?
  * 많은 양의 콘텐츠가 수직형 구조 혹은 계층 구조로 이루어져 있으면 반드시 사용해야함
  * 하지만 논리적 계층구조나 그루핑이 없는 단일 레벨 웹사이트에서는 사용하지 말아야 함
* 3원칙
  * Breadcrumb 은 main navigation을 대체하지 않는다.
  * 구분해주는 부호를 사용한다. (예시: >, >>, /, → 등)
  * 디자인의 중심이 되게 만들지 않는다.

## 본론

### 구현 아이디어

* \<li> 태그를 이용하여 왔던 리스트를 만든다.
* 사이에 구분할 요소를 넣는다.

### 구현해보기

* ul 태그와 li 태그를 이용하여 리스트를 만든다.

* ```html
  <body>
    <ul>
      <li>의류</li>
      <li>상의</li>
      <li>아우터</li>
      <li>MA - 1</li>
    </ul>
  </body>
  ```

* 스타일링을 통해 가로로 놓이게 만든다.

* ```css
  .breadcrumb {
      /* 리스트의 똥글뱅이를 없애줌 */
      list-style-type: none;
      display: flex;
  }
  ```

* 형제 선택자와 가상 선택자를 이용하여 요소 사이에 구분 요소 삽입

* ```css
  .breadcrumb li+li::before {
      padding: 8px;
      color: black;
      content: "/";
  }
  ```

* 각 글씨에 clickable 한 인상을 주기 위해 css 요소 적용

* ```css
  .breadcrumb > li {
      color: blue;
      cursor: pointer;
  }
  ```

* 마지막 li 요소는 현재 있는 곳이기 때문에 clickable 한 인상을 주고 싶지 않았다.

* 그래서 마지막 요소에만 색과 커서를 빼기로 했다.

* ```css
  .breadcrumb > li:last-child {
      color: gray;
      cursor: default;
  }
  ```



### 완성 코드

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Breadcrumb</title>
  <style>
    .breadcrumb {
      /* 리스트의 똥글뱅이를 없애줌 */
      list-style-type: none;
      display: flex;
    }
    .breadcrumb li+li::before {
      padding: 8px;
      color: black;
      content: "/";
    }
    .breadcrumb > li {
      color: blue;
      cursor: pointer;
    }
    .breadcrumb > li:last-child {
      color: gray;
      cursor: default;
    }
  </style>
</head>
<body>
  <ul class="breadcrumb">
    <li>의류</li>
    <li>상의</li>
    <li>아우터</li>
    <li>MA - 1</li>
  </ul>
</body>
</html>
```





## 결론



### 새로 알게 된 것

* css 에서 content 요소는 가상 선택자 `::befroe` `::after` 에만 적용할 수 있다.
* \00a0 은 non-breaking space 를 의미한다.
  * `non-breaking space` : 줄 바꿈 없는 공백
* 형제 선택자 `+`
  * A + B 를 선택했을 때
  * `같은 부모`를 가지고, A `바로 뒤`에 오는 B 에만 적용
* `~`
  * A ~ B 일 때
  * 같은 부모를 가지고, A 뒤에 오는 B에 적용
  * 바로 뒤일 필요 X





### 더 생각해볼 거리

* 단순히 Breadcrumb 을 랜더링 하는걸 넘어서서 링크를 눌렀을 때 이동하도록 동작하게 하고 싶다.


