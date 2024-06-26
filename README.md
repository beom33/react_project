# 설정

## .prettierrc 설정

```json 
{
"singleQuote": true,
"semi": true,
"useTabs":  false,
"tabWidth": 2,
"trailingComma": "all"
}
```

## 의존성  
> 필요 라이브러리 

  - react-router-dom  : 라우터 
  - sass, styled-components, classnames : 스타일링 목적 
  - immer : 불변성 관리 
  - react-icons : 리액트에서 제공하는 아이콘 라이브러리 
  - @loadable/component : 지연로딩 
  - react-helmet-async : head 태그 내의 특정 태그의 내용을 변경시 

  - 의존성 설치 

  ```
  yarn add react-router-dom sass styled-components classnames immer react-icons @loadable/component
  yarn add react-helmet-async  
  ```

  ## react- helmet - async 설정 
    -src/index.js

    ```jsx
    ...

    import { Helmet, helmetProvider } from 'react-helmet-async';
    ...

root.render(
  <React.StrictMode>
    <helmetProvider>
           <App />
    </helmetProvider>
  </React.StrictMode>
);
 
 ```jsx

 - 사용법
import { Helmet } from "react-helmet-async";

const App =() => {
  return (
   <>
   <Helmet>
   <title>사이트 제목 변경 테스트!</title>

   </Helmet>
   
    </>

  );

};

export default App;

```

## 메세지, 다국어 처리 

-의존성 :i18next, react-i18next
-의존성 설치 

```
yarn add i18next react-i18next
```

- 언어파일 생성
    -src/langs/ko, src/langs/en 폴더 생성
    -각 폴더별로 공통문구 - commons.js 검증 문구 - validations.js, 에러 문구 - errors.js

    -언어 파일 통합 : 예) src/langs/ko/index.js
    
    ```javascript
    import commons from "./commons";
    import validtions from "./  validations";
     import errors from "./errors";

     const ko = { ...commons, ...validtions, ...errors };

    export default ko;

```

-설정파일 구성


```javascript

import i18n from 'i18next';
import {  initReactI18next } from 'react-i18next'
import ko from './langs/ko';
import en from './langs/en';

const resources = {
     en: {
         translation: en,

     },

     ko: {
        translation: ko,
     },
};

i18n.use(initReactI18next).init ({
   resources,
   lng: 'ko',
   
});
```

-설정 반영 : src/index.js

```javascript
...

import'./i18n';

...

```

- 적용하기 : useTranslation  훅 / react-i18next
 - t : 메세지 조회 함수 
 - i18n: 편의 기능 객체, changeLanguage(..) : 언어변경




# 스타일링
## 공통 스타일 : src/index.css
- 공통 폰트
- 스타일 초기화 
- 기준 폰트 사이즈 : styles/fontSize.js / small, normal, medium, big, extrabig

기준컬러: primary, Secondary, Success, Danger, Warning, info, Light, Dark