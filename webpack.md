# 📌 웹팩(Webpack)

기본형 데이터와 참조형 데이터에 대해 알아보고자 작성했다.  **[코어 자바스크립트]** 책을 보면서 직접 그림그리며 작성해보았다. 메모리에 할당되는 형태를 보면서 작성하니 이해에 많은 도움이 되었다. 참고로 내돈내산...

## ✅  개요

```
- 오픈 소스 자바스크립트 모듈 번들러.
- 여러개로 나뉘어진 파일들을 하나의 자바스크립트 코드로 압축하고 최적화하는 라이브러리.
```



## ✅  모듈 번들러의 장점

- 여러 파일의 자바스크립트 코드를 압축하여 최적화 -> **로딩에 대한 네트워크 비용의 Down.**
- 모듈 단위 개발이 가능하여 가독성과 유지보수성이 좋아짐
- 최신 자바스크립트 문법을 지원하지 않는 브라우저에서 사용할 수 있는 코드로 쉽게 변환해줌.



## ✅ 초기 로딩의 문제

- 수많은 자바스크립트 파일이 하나로 묶이면 초기 로딩 속도가 커질 수 있음
- 이를 해결하기 위해 웹팩은 **청크, 캐시, 코드 스플릿 개념을 도입**하여 해결하고 있음.



## ✅  웹팩의 구성요소

```
1. Entry : 웹팩이 빌드할 파일의 시작 위치를 나타냄.
2. Output : 웹팩에 의해 생성되는 번들을 내보낼 위치와 파일 이름을 나타냄.
3. Loaders : 자바스크립트 파일이 아닌 파일들도 유효한 모듈로 변환시켜줌.
4. Plugins : 로더가 파일단위로 처리하는 반면 플러그인은 번들된 결과물을 처리.
5. Mode : 웹팩을 셋팅하는 것에 있어 development(최적화 빌드)/Production(빠른 빌드)/none(웹팩 빌드)
```



## ✅ 웹팩 추가 기능들

### 💬 웹팩 개발 서버(webpack-dev-server)

```js
// webpack.config.js:

module.exports = {
  devServer: {
    contentBase: path.join(__dirname, "dist"), // 정적 파일 제공 경로 - 절대경로사용
    publicPath: "/", // 브라우저를 통래 접근하는 경로
    host: "localhsot", // 개발환경 구축 시 도메인을 맞춰야하는 경우에 사용
    overlay: true, // 빌드시 에러나 경고를 브라우저 화면에 표시하는 옵션
    port: 9000, // 포트번호 설정 - 기본값 8080
    stats: "errors-only", // 메시지 수준 설정
    historyApiFallback: true, // 히스토리 API를 사용하는 SPA 개발 시 설정. 404 에러 시 index.html로 리다이렉트
    hot: true, // 전체화면을 갱신하지 않고 변경한 모듈만 바꿔치기 할 수 있는 기능.
  },
}
```



## ✅ 웹팩 설정 에러

### 💬 MIME TYPE Error

```bash
webpack Refused to apply style from 'http://...' because its MIME type ('text/html') is not a supported stylesheet MIME type, and strict MIME checking is enabled.
```

#### 📑 발생한 상황

- <span style="color:red">**바닐라 JS에서 SPA 구현 중 href로 이동을 진행함.** </span>
- **localhost:port/a** : 정상작동.
- **localhost:port/a/1** : MIME TYPE Error 발생.

#### 📑 해결방법

- **SCSS 삭제해보기** : 증상 동일

- **재빌드** : 증상 동일

- **output 설정 변경** : 증상 해결

  ```js
  module.exports = {
    ...
    output: {
      path: path.resolve(__dirname, "dist"),
      publicPath: "/", /* publicPath 추가 */
      filename: "js/bundle.js",
    },
  }
  ```

  - **publicPath** = 번들 파일을 위한 위치. (절대 경로 혹은 기본 HTML 파일에 대한 상대경로)
    - 번들링한 파일의 경로를 지정하는 방법.
    - 만약 설정하지 않으면 "localhost:port/a/1/css/style.css"로 경로 설정되어 Error 발생되는 것.
    - 개발자 도구 source에서 경로 확인하고 잘못됨을 알았는데 해결방법을 찾지못하다 웹팩 공식문서 보니 해결할 수 있었음😂
  - **path** = 번들링한 출력 파일을 저장하는 경로.

