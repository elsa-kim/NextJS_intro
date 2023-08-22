# NextJS introduction

### pages

pages 안에 만드는 js 파일명이 url pathname, 파일 내용이 해당 주소 component

- component 이름은 크게 중요하지 않음
- component가 export default 되어야 하는 것 중요
- 파일명 아닌 페이지 들어가면 404 페이지 뜸
- index.js : 오리지널 주소 페이지 ex)localhost:3000
- jsx 사용시 React.js import 필요없음

### 소스코드

소스코드 안에 실제 HTML이 들어있어 유저가 매우 느린 연결을 하거나 자바스크립트 비활성화 상태에서도 유저는 HTML 볼 수 있음

- 초기상태 pre-rendering 함
- 페이지 로딩 시 react.js가 넘겨받아 Hook 작동

#### hydration

react.js를 프론트엔드 안에서 실행하는 것

- next.js는 react.js를 백엔드에서 동작시켜 페이지 미리 만들어 component들 render 시키고 렌더링이 끝나면 HTML이 됨 => 소스코드에 넣음 => react.js 로딩 되었을 때 이미 존재하는 것들과 연결되어 react.js 앱이 됨

### CSS

1. 태그 안에 스타일 적용
2. CSS modules 사용

- 파일명 : .module.css
- 사용법 : import styles from "파일 위치", classname={styles.클래스이름}
- 클래스명 재사용 가능 : 페이지 빌드될 때 NextJS가 해당 클래스명 뒤 랜덤한 이름 붙여 충돌하지 않음

3. styles JSX 사용

- NextJS 고유기능
- style 태그에 jsx prop 작성, 태그 내부에 괄호&백틱 후 작성
- 컴포넌트 단위로 적용할 스타일 지정
- 글로벌 스타일 지정 위해 style 태그에 global prop 추가 : 페이지 고려해야함

### App Component

모든 페이지에 전역적 스타일링, 설정 위해

- pages 폴더 내 "\_app.js" 이름으로 생성
- prop 두가지 불러옴
  - component
  - pageProps

### next.config.js

#### redirects

url에 특정주소(source) 입력시 정해둔 주소(destination)로 이동,
뒤에 \* 입력시 해당부분 뒤 다 캐치

- 유저가 알 수 있음

#### rewrites

- 유저가 알 수 없음(URL 변화 볼 수 없음)

### Server Side Rendering

- 데이터 유효할 때 화면 보여짐
- loading 없는 대신 API load 느리면 유저가 아무것도 못보는 상태로 오래 기다려야 함
- getServerSideProps 이름으로 함수 생성 후 export
- props 반환해주기
- 서버쪽에서만 작동 ex) 여기에 API key 쓰면 절대 client에게 보여지지 않음

### Client Side Rendering

- static shell(ex. header, footer,nav bar, ...) 미리 보여지고 API에서 데이터 받아올때까지 loading
- API load 느리면 유저는 로딩중 단계 오래 봐야 함
