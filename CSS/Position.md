# Position
- 요소를 원하는 위치에 자유롭게 이동시키기 위한 속성
- 총 5가지 속성이 존재
  - static 
  - relative
  - absolute
  - fixed
  - sticky
- sticky같은 경우 지원을 안하는 브라우저가 존재 함.

Position 속성을 적용할 때는 2가지를 유의해야됨.
> Type => 기준점
1. position 속성을 적용하려는 box가 어떤 `타입`인지
2. box가 어떤 `기준점`을 가지고 움직이는지

___

## static
- 모든 요소의 기본 포지션
- 가장 일반적인 상태
___ 


## relative 
- 자신이 본래 있던 자리를 기준으로 위 아래 좌우로 이동

```css
.container {
  margin: 0px auto;
  width: 100px;
  background-color: grey;
}

.box {
  height: 100px;
  width: 100px;
}
/* relative right 적용*/
.red {
  background-color: red;
  position: relative;
  right: 110px;
}

.yellow {
  background-color: yellow;
}

.blue {
  background-color: blue;
}
```
<img width="284" alt="relative" src="https://user-images.githubusercontent.com/75591730/166887708-924cdf04-7800-4923-8bd9-e29deb02b819.png">

___

## absolute
- 요소에 absolute를 적용하면 float을 적용할 때와 비슷한 box 속성을 가지게 됨
  - box type이 `block`으로 변경
  - 대신 `영역`을 차지하는 block이 아님.
-  부모뷰들을 기준으로 position을 이동 
  - 이때 부모뷰는 static 속성일 제외한 요소 이어야 함.

```html 
.container {
  position: relative;
  margin: 0px auto;
  width: 100px;
  background-color: grey;
}

.box {
  height: 100px;
  width: 100px;
}

.red {
  background-color: red;
  position: absolute;
  left: 110px;
}1
```

<img width="328" alt="position" src="https://user-images.githubusercontent.com/75591730/166905198-71e6962a-40ac-4834-a91d-34b3aa38b718.png">


--- 

## fixed
- absolute과 동일 현상이 나타남
  - fixed가 된 요소는 blcok box 타입이 적용
  - 별도의 width를 명시하지 않으면 요소의 content 사이즈 만큼 expand
- 다만 fixed는 본인의 기준점 정확히 정해져 있음
  - `viewprot`가 기준이 됨
  - 여기서 `viewprot`란 브라우저의 사이즈를 의미
- 스크롤을 해도 위치값이 고정.

```html 
.container {
  margin: 0px auto;
  width: 100px;
  background-color: grey;
}

.box {
  height: 100px;
  width: 100px;
}

.red {
  background-color: red;
  position: fixed;
  left: 0;
}
```

<img width="602" alt="fixed" src="https://user-images.githubusercontent.com/75591730/166906223-5e5b3285-1855-4e7e-ab39-cad80bdb3da6.png">

___  

## 실습
### 1
<img width="464" alt="position_예제" src="https://user-images.githubusercontent.com/75591730/166913114-a8d26a60-e2f1-40bd-9c19-e0a935c974f5.png">
HTML 

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="style.css" />
    <title>Document</title>
  </head>
  <body>
    <div class="user-card">
      <div class="user-profile-image">
        <img src="./images/user.jpeg" />
        <span class="user-status"></span>
      </div>
      <span class="user-name">SimYa</span>
    </div>
  </body>
</html>

```
CSS 
```css 
* {
  margin: 0;
  box-sizing: border-box;
  font-family: "Spoqa Han Sans", sans-serif;
}

html {
  font-size: 16px;
  font-family: "Spoqa Han Sans", sans-serif;
  letter-spacing: -0.03em;
  color: #212529;
}

body {
  background-color: gainsboro;
  margin: 40px auto;
}

.user-card {
  height: 56px;
  width: 240px;
  background-color: white;
  display: flex;
  margin-left: 40px;
  padding: 0px 12px;
  border-radius: 4px;
}

.user-profile-image {
  height: 40px;
  margin: auto 0px;
  position: relative;
}

.user-profile-image img {
  height: 40px;
  width: 40px;
  border-radius: 20px;
}

.user-status {
  height: 6px;
  width: 6px;
  box-sizing: content-box;
  border-radius: 5px;
  background-color: aquamarine;
  border: 2px solid white;
  position: absolute;
  bottom: 0px;
  right: 0px;
}

.user-name {
  margin: auto 0px auto 12px;
}

```

### 2
<img width="681" alt="position2" src="https://user-images.githubusercontent.com/75591730/166926075-5d5bbf73-4dfe-47d5-8273-210a626831e3.png">


HTML
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="style.css" />
    <title>Document</title>
  </head>
  <body>
    <div class="card">
      <!-- Image -->
      <div class="card-image">
        <img src="./images/img-card.jpg" />
        <div class="card-button-wrapper">
          <button type="button" id="prev"></button>
          <button type="button" id="next"></button>
        </div>
      </div>
      <!-- Contents -->
      <div class="card-content">
        <span class="title">그랜드캐년+앤텔롭+홀슈밴드 자유일정</span>
        <span>김버그트래블</span>
        <strong class="price"><span>1인 </span> 180,000원</strong>
      </div>
    </div>
  </body>
</html>

```
CSS
```css
* {
  margin: 0;
  box-sizing: border-box;
  font-family: "Spoqa Han Sans", sans-serif;
}

html {
  font-size: 16px;
  font-family: "Spoqa Han Sans", sans-serif;
  letter-spacing: -0.03em;
  color: #212529;
}

body {
  margin: 200px;
  background-color: gainsboro;
}

#prev {
  height: 28px;
  width: 28px;
  background: url(/images/icon-backward.svg);
  float: left;
}

#next {
  height: 28px;
  width: 28px;
  background: url(/images/icon-forward.svg);
  float: right;
}

.card {
  height: 354px;
  width: 400px;
  position: relative;
  background-color: white;
}

.card-image {
  position: relative;
  height: 240px;
  width: 100%;
}

.card-image img {
  width: 100%;
  height: 240px;
  display: block;
}

.card-button-wrapper {
  top: 50%;
  transform: translateY(-50%);
  width: 100%;
  position: absolute;
}

.card-image button {
  border: none;
  color: blue;
  display: flex;
  float: right;
}

.card-content {
  padding: 12px 16px;
}

.card-content span {
  display: block;
}

.card-content .title {
  font-size: 20px;
  line-height: 32px;
}
.card-content span:nth-child(2) {
  font-size: 16px;
  color: darkslategrey;
}

.card-content strong {
  position: absolute;
  display: flex;
  right: 16px;
  bottom: 12px;
}

.card-content .price {
  font-size: 20px;
  color: #2860e1;
}

.card-content .price span {
  font-size: 12px;
  color: darkslategrey;
  margin: auto 4px auto 0px;
}
```

--- 
## 3
<img width="1020" alt="subscription" src="https://user-images.githubusercontent.com/75591730/167053936-f7f7a74e-f8b3-4319-8ef7-c9d4c97399fc.png">

HTML
```html 
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="style.css" />
    <title>Document</title>
  </head>
  <body>
    <div class="modal">
      <button id="modal-cancel-btn" type="button"></button>
      <h2 class="title">Manage Subscriptions</h1>
      <p class="description">You can follow the discussion on @SimYa without to leave a comment. Cool, huh?</br> 
      Just enter your email address in the form here below and you are all set.
      </p>
      <form>
        <input id="modal-email-field" type="email" placeholder="Your e-mail">
        <button id="modal-email-btn" type="submit">Subscribe</button>
      </form>
    </div>
  </body>
</html>
```

CSS 
```css
* {
  margin: 0;
  box-sizing: border-box;
  font-family: "Spoqa Han Sans", sans-serif;
}

html {
  font-size: 16px;
  font-family: "Spoqa Han Sans", sans-serif;
  letter-spacing: -0.03em;
  color: #212529;
}

body {
  margin-top: 40px;
  background-color: gainsboro;
}

.modal {
  height: 216px;
  width: 671px;
  padding: 32px 40px;
  border-radius: 4px;
  background-color: white;
  margin: 0px auto;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  position: relative;
}

#modal-cancel-btn {
  height: 20px;
  width: 20px;
  background: url(/images/icon-close.svg) no-repeat;
  border: none;
  position: absolute;
  right: 12px;
  top: 12px;
}

.modal .title {
  margin-top: 0px;
  margin-bottom: 0px;
  font-size: 24px;
  color: #1f2d3d;
}

.modal .description {
  font-size: 16px;
  line-height: 24px;
  color: #273444;
  margin-bottom: 20px;
}

#modal-email-field {
  background-color: #f6f8fa;
  border: none;
  height: 36px;
  width: 200px;
  border-radius: 4px;
  padding-left: 16px;
}

#modal-email-btn {
  background-color: #2860e1;
  border: none;
  border-radius: 4px;
  height: 36px;
  width: 90px;
  color: white;
}

```





