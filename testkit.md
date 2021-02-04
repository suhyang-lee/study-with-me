# 📌 자바스크립트 테스트 도구

자바스크립트 테스트 도구에 대해 궁금해져서 검색해봤는데 생각보다 더 많은 테스트 도구를 정리해놓은 IT 뉴스를 발견할 수 있었다. 검색하면 주로 나오는 도구가 [JEST]와 [Mocha] 였는데 이 두가지말고도 다른 테스트 도구가 있어서 한번 정리해보려 한다.

## 목차

[TOC]

### ✅ 유닛테스트란 뭘까

```
컴퓨터 프로그래밍에서 소스 코드의 특정 모듈이 의도된 대로 정확히 검증하는 절차.
'모든 함수'와 '메소드'에 대한 '테스트 케이스'를 '작성'하는 절차를 말한다.
```

- **유닛테스트**에서 얻을 수 있는 키워드는 '**모든함수**', '**메소드**', '**테스트케이스**','**작성**'
- 결국 **유닛테스트 === 모든함수나 메소드에 대한 테스트를 실행**하는 것.
- 이상적으로 테스트 케이스는 서로 분리되어야 하며, 이를 위해 Mock Object를 생성하여 테스트를 하는 것은 좋은 방법이 될 수 있음.

### ✅ 장점

- **📑 문제점 발견** 
  
  - 유닛테스트의 궁극적 목적은 프로그램의 각 부분을 고립시켜 각각의 부분이 정확하게 동작하는지 확인하는 것.
  - 프로그램을 작은 단위(Unit)로 쪼개서 각 단위가 정확하게 동작하는지 검사하고 이를 통해 문제 발생 시 정확하게 어느 부분이 잘못되었는지 재빨리 확인할 수 있게 함.
  - 따라서 이는 <u>프로그램의 안정성을 높일 수 있는 방법</u>이 될 수 있음.
  - 유닛테스트를 실행하는 것이 한 편으로는 테스트 케이스의 작성으로 개발 시간을 증가시키는 것 처럼 보일 수 있지만 개발 기간 중 대부분을 차지하는 디버깅 시간이 궁극적으로는 단축시킬 수 있는 방법이 될 수 있음. 
  - ~~적어도 유닛테스트를 실행한 단위에 대해서는 문제가 없다고 판단할 수 있기 때문인 것 같다.~~
  
- 📑 **변경의 쉬움**

  - 언제든지 유닛테스트를 믿고 리팩토링을 진행할 수 있음.

  - 이는 리팩토링 후에도 해당 모듈이 의도대로 작동하고 있음을 유닛 테스트를 통해 확신할 수 있기 때문.

  - 테스트케이스를 테스트하는 모듈이 사용되는 모든 경로를 커버할 수 있는 테스트케이스를 만들면 리팩토링 이후에 코드를 고치더라도 문제점 파악이 매우 빠름.

  - 리팩토링에 오류가 발생하여 테스트할 때 대체적으로 '회귀테스트'를 진행함.

    ```
    회귀버그를 찾는 모든 소프트웨어 방식은 회귀 테스트라 할 수 있음. 이때, 회귀버그란 이전에 제대로 동작하던 소프트웨어 기능에 문제가 생기는 것을 말함.
    일반적으로 회귀 버그는 '프로그램 변경' 중에 뜻하지 않게 발생하는 것.
    
    회귀테스트는 이전의 실행테스트를 재 실행하며 이전에 고쳐졌던 오류가 재현되는지 검사하는 방법이 많이 사용됨. 일반적으로 부실한 버전관리로 인해 이전의 버그 수정분을 유실하고 이로인해 버그를 재발하는 경우가 종종있기 때문...(!)
    
    리팩토링을 통해서 몇몇 기능을 재디자인할 경우 동일한 문제가 이전에 고쳐진 부분에서 다시 발생하는 경우가 많음.
    ```

- **📑 통합이 쉬움**
  
  - 유닛 테스트는 유닛 자체의 불확실성을 제거해주므로 상향식 테스트 방식에서 유용함.
  
  - 먼저 프로그램의 각 부분을 검증하고 그 부분들은 합쳐서 다시 검증하는 통합 테스트에서 더욱 빛을 발하는 테스트 방법.
  
    

### ✅ 자바스크립트의 테스트 도구

#### 💬 AVA

- **개요** : 자바스크립트는 싱글스레드 기반으로 작동하지만 Node.js 에서의 입출력은 비동기 생태계를 이용하여 **병렬 처리**가 가능하도록 한다. AVA는 무거운 입출력 작업에 사용할 수 있는 해당 방법을 적극적으로 활용하여 **테스트를 동시에 처리**할 수 있도록 해준다

- **활용** : Node.js 모듈 및 서버 어플리케이션 테스트에는 최적. UI 테스트로는 부적합.

- **GitHub** : [AVA](https://github.com/avajs/ava-docs/blob/main/ko_KR/readme.md)

- **설치방법**

  ```javascript
  // global install
  $ npm install -g ava
  $ ava --init 
  
  // package.json 설치
  $ npm install -D ava
  ```

- **테스트 파일 만들기**

  ```javascript
  import test from "ava";
  
  test("foo", t => {
     t.pass();
  });
  
  test("bar", async t => {
      const bar = Promise.resolve("bar");
      t.is(await bar, "bar");
  })
  ```

#### 💬 Cucumber.js

이것은 개인적인 생각인데.... 외국사람들은 오이가 싫다면서 오이를 사실 제일 사랑하는게 아닐까? 이 테스트는 신기한게 진짜 영어로 되어있다. 근데 영어로만 되어있을뿐 들여쓰기 이런 것은 필요해서 오히려 가독성이 더 떨어진다는 느낌을 받았다. 글 읽을 때 들여쓰기가 요상하게 되어있으면 가독성이 떨어지는 그런 느낌? 

- **개요** : 평문(영어)으로 작성된 자동화된 테스트를 실행하기 위한 도구로 팀원 누구나 읽을 수 있는 것이 최대의 장점인 테스트 도구. 팀에 대한 커뮤니케이션, 협업 및 신뢰를 개선하는데 사용할 수 있는 도구.

- **활용** : 개발자가 아닌 사람과의 커뮤니케이션이 필요할 때 사용할 수 있음. (실제로 영어로 작성됨.)

- **GitHub** : [cucumbar](https://github.com/cucumber/cucumber-js)

- **설치방법**

  ```js
  $npm install @cucumber/cucumber
  ```

- **테스트 파일 만들기** : [데모] https://cucumber.github.io/cucumber-js/

#### 💬 엔자임

다른 테스트 모듈과 함께 사용할 수 있음. 모카, 차이, 제스트 등과 함께 사용이 가능하다. 

- **개요** : 리액트 컴포넌트의 출력을 보다 쉽게 테스트르 할 수 있는 React용 자바스크립트 테스트 유틸리티. 출력이 주어지면 조작, 트래버스 및 어떤 방식으로든 런타임 시뮬레이션이 가능함. DOM 조작의 순회를 위해 jQuery의 API를 모방하여 직관적이고 유연함.

- **활용** : 리액트의 컴포넌트 테스트.

- **GitHub** : [enzymejs](https://enzymejs.github.io/enzyme/)

- **설치방법**

  ```js
  $ npm install -D enyme enzyme-adapter-react-16
  ```

- **테스트 파일 만들기**

  ```js
  import React from 'react';
  import { expect } from 'chai'; //다른 테스트 모듈 사용 가능!
  import { shallow } from 'enzyme';
  import sinon from 'sinon';
  
  import MyComponent from './MyComponent';
  import Foo from './Foo';
  
  describe('<MyComponent />', () => {
    it('renders three <Foo /> components', () => {
      const wrapper = shallow(<MyComponent />);
      expect(wrapper.find(Foo)).to.have.lengthOf(3);
    });
  
    it('renders an `.icon-star`', () => {
      const wrapper = shallow(<MyComponent />);
      expect(wrapper.find('.icon-star')).to.have.lengthOf(1);
    });
  
    it('renders children when passed in', () => {
      const wrapper = shallow((
        <MyComponent>
          <div className="unique" />
        </MyComponent>
      ));
      expect(wrapper.contains(<div className="unique" />)).to.equal(true);
    });
  
    it('simulates click events', () => {
      const onButtonClick = sinon.spy();
      const wrapper = shallow(<Foo onButtonClick={onButtonClick} />);
      wrapper.find('button').simulate('click');
      expect(onButtonClick).to.have.property('callCount', 1);
    });
  });
  ```

  

#### 💬 카르마

- **개요**
- **활용**
- **GitHub**
- **설치방법**
- **테스트 파일 만들기**

#### 💬 자스민

- **개요**
- **활용**
- **GitHub**
- **설치방법**
- **테스트 파일 만들기**

#### 💬 제스트

- **개요**
- **활용**
- **GitHub**
- **설치방법**
- **테스트 파일 만들기**

#### 💬 루나

- **개요**
- **활용**
- **GitHub**
- **설치방법**
- **테스트 파일 만들기**

#### 💬 모카

- **개요**
- **활용**
- **GitHub**
- **설치방법**
- **테스트 파일 만들기**

#### 💬 프로트랙터

- **개요**
- **활용**
- **GitHub**
- **설치방법**
- **테스트 파일 만들기**

#### 💬 큐유닛

- **개요**
- **활용**
- **GitHub**
- **설치방법**
- **테스트 파일 만들기**



### ✅ 참고

[유닛테스트](https://ko.wikipedia.org/wiki/%EC%9C%A0%EB%8B%9B_%ED%85%8C%EC%8A%A4%ED%8A%B8)

[믿을만한 자바스크립트 테스트 도구 10가지](https://www.itworld.co.kr/news/128974)

[회귀테스트](https://ko.wikipedia.org/wiki/%ED%9A%8C%EA%B7%80_%ED%85%8C%EC%8A%A4%ED%8A%B8)