# [UI Seriese] 04 Button

## 서론

* Button이란?
  * 특정 형태 안에 라벨을 넣어 표시하는 것.
  * 누름으로써 특정 동작이 수행 됨
* 예시
  * ![image-20210913214955022](04_button.assets/image-20210913214955022.png)

## 본론

### 구현 아이디어

* 버튼을 구현해보는 동시에 버튼의 여러가지 속성들을 확인해보자.
* < button > 태그를 사용하지 않고, 눌렀을 때 네이버로 이동시켜주는 버튼을 만들어보자.
  * 버튼 크기정도(확인필요)의 div를 만든다.
  * div를 클릭하게 된다면 네이버가 연결되어있는 브라우저창을 열어준다.

### 구현해보기

- div 태그 버튼처럼 만들어주기



### 완성 코드

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Button</title>
</head>
<style>
  .div-btn {
    background-color: rgb(119, 132, 143);
    width: 200px;
    padding: 20px;
    font-size: 20px;
    text-align: center;
    cursor: pointer;
    border-radius: 10px;
    box-shadow: 10px 10px 10px black;
    position: absolute;
    top: 50%;
    left: 50%;
    /* 개체의 넓이와 높이를 반대로 50%이동? */
    transform: translate(-50%, -50%);
  }
</style>
<body>
  <div id="div-btn" class="div-btn">div button</div>

</body>
<script>
  const btn = document.getElementById('div-btn');
  const link = "https://www.naver.com"
  btn.addEventListener('click', function() {
    // 현재 창에서
    // location.href = link
    // 새창으로 열기
    // window.open(link)
    // window.open(link,'window_name','width=430,height=500,location=no,status=no,scrollbars=no');
    window.open(link,'window_name','fullscreen=yes');
  })
</script>
</html>
```



## 결론



### 새로 알게 된 것

* 브라우저창을 띄우는 방법

  * 현재 창에서 열기

    ```js
    location.href = "address";
    ```

  * 새 창에서 열기

    ```js
    window.open("address");
    ```

  * 팝업창으로 열기

    ```js
    window.open("address", "window_name", "width=430, height=500, location, status...")
    ```

    ![image-20210913225158435](04_button.assets/image-20210913225158435.png)

  

### 더 생각해볼 거리


