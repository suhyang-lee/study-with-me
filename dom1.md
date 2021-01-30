# 📌 DOM 조작하기

## ✅ winodw.onLoad

- 객체가 로드되었을 때 발생
- 웹페이지가 모든 콘텐츠(이미지, 스크립트, CSS)를 완전히 로드한 후 스크립트를 실행하기 위해 사용.
- 방문자의 브라우저 유형 및 버전을 확인하고 정보를 기반으로 웹 페이지 로드시 사용할 수 있음.
- 해당 이벤트를 통해 쿠키 처리가 가능함.
- 여러번 선언해도 하나의 이벤트만 실행됨.

## ✅ document.reday

- 외부 리소스나 이미지 등에 상관없이 Dom Tree 생성 직후 실행.
- 다른 유형의 콘텐츠 로드 여부가 상관없으므로 winodw.onLoad 이벤트보다 빨리 실행됨.
- winodw.onLoad 와는 달리 중복 사용하여도 선언한 순서대로 실행됨.

## ✅ window 객체와 document 객체

### 💬 window

- 개요 : 웹 브라우저의 창을 나타나는 객체로 대부분의 웹 브라우저에서 지원
- 자바스크립트의 모든 객체, 전역 함수, 전역 변수들은 자동으로 window 객체의 프로퍼티가 됨.
- window 객체의 메소드, 프로퍼티는 전역 변수임.
- DOM의 요소들도 모두 window 객체의 프로퍼티 임.

### 💬 document

- 개요 : Document 객체는 웹 페이지 그 자체를 의미하며 웹 페이지에 존재하는 HTML 요소에 접근하고자 할 때 반드시 Document 객체부터 시작해야 함.
- Document 메소드 : HTML 요소의 선택, HTML 요소의 생성, HTML 이벤트 핸들러 추가, HTML 객체의 선택
  |메소드|설명|
  |:---|:---|
  |document.getElementsByTagName(태그이름)|해당 태그 이름의 요소를 모두 선택함.|
  |document.getElementById(아이디)|해당 아이디의 요소를 선택함.|
  |document.getElementsByClassName(클래스이름)|해당 클래스에 속한 요소를 모두 선택함.|
  |document.getElementByName(name속성값)|해당 name 속성값을 가지는 요소를 모두 선택함.|
  |document.querySelectorAll(선택자)| 해당 선택자로 선택되는 요소를 모두 선택함.|
- Document 메소드 : 새로운 HTML 요소를 생성하기 위해 제공되는 메소드
  |메소드|설명|
  |:---|:---|
  |document.createElement(HTML요소)|지정된 HTML 요소를 생성함.|
  |document.write(텍스트)|HTML 출력 스트림을 통해 텍스트를 출력함.|


## ✅ 어떤 방법으로 코딩을 할까

### 💬 window.onload = function() vs window.addEventListener("load")
- 협업 시에는 window.onload에 바로 function을 정의하지 않음.
- 혼자 사용할 때는 문제는 없지만, 가급적이면 리스너를 달아 사용하는 것이 좋음.

### 💬 createElement vs innerHTML
- 유지보수의 문제로 innerHTML 을 주로 사용한다.
- createElement를 사용하게되면 가독성이 떨어져 협업을 하기 어려워짐.
- innerHTML 사용 : 보안의 위험성은 있지만 충분히 막을 수 있는 여러 대안이 마련되어있으므로 유지보수 측면에서 고려하는 것이 좋음.

### 💬 getElemnet(s)By ~ vs querySelector
- id 등은 바로 접근하면 위험할 수 있음.
- tagName은 레거시. 
- 주로 querySelector를 사용함. (가장 처음에 일치되는 값을 가져옴)

### 출처

- [Document 객체] http://www.tcpschool.com/javascript/js_dom_document
- [Window 객체] http://www.tcpschool.com/javascript/js_bom_window
- [onload 이벤트] https://www.w3schools.com/jsref/event_onload.asp

