# 📌 Prototype

## ✅ 개요

- 기본적으로 JS는 프로토타입 기반의 언어이며 JS에서 모든 객체는 Object의 인스턴스.
- 일반적 객체는 Obejct.prototype에서 속성과 메소드를 상속받으며 그 중 일부는 숨겨질 수 있음.
- Object Prototype에 수정을 가하는 것은 프로토타입 체인을 통해 더 아래쪽 체인에 덮어쓰는 경우가 아니라면 모든 객체에서 관측할 수 있음.
  그러나 이것은 객체 확장이나 행동에 영향을 줄 수 있는 강력한 방법이자 리스크 임.

## ✅ Protoype Link와 Prototype Obejct

### 💬 protoype Link + Prototype Obejct = Prototype
### 💬 Prototype Obejct
- 객체는 언제나 함수(function)으로 생성. JS에서 기본적으로 제공하는 Obeject 역시 함수.
- 함수를 정의하게 되면 함수만 생성되는 것이 아닌 Prototype Obejct도 같이 생성됨.
- 생성된 함수는 prototype라는 속성을 통해 Prototype Object에 접근 가능.

```js
  /* 접근 예제 */
  function Computer() {}

  Computer.prototype.sdd = 512;
  Computer.prototype.ram = 16;

  const codingComputer = new Computer(); // codingComputer.sdd : 512
  const gammingComputer = new Computer();
```

### 💬 Prototype Link
- 새로 new로 생성한 객체에서도 기존에 정의해두었던 속성을 사용할 수 있는 것은 \_proto\_ 속성이 이를 할 수 있게 해줌.
- 기본적으로 \_proto\_ 속성은 모든 객체가 가지고 있는 속성.
- 결국 \_proto\_ 속성은 최초 생성된 Computer() 함수에 포인터를 두고 있는 셈.
- 바로 이렇게 상위 프로토타입에 연결되어있는 것을 <b>Prototype Chain</b>이라 함.
- 형태를 보면 원형 연결 리스트같은 모습을 보임. 결국 연결(=chain)이니 그렇게 부르는 것 같기두 😅

## ✅ 출처

- [Javascript] 프로토타입 이해하기 : https://medium.com/@bluesh55/javascript-prototype-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-f8e67c286b67
- [MDN] Object.prototype : https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype
