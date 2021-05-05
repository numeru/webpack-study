# NPM

- 명령어로 자바스크립트 라이브러리를 설치하고 관리할 수 있는 패키지 매니저

### 1. 시작

```
npm init

npm init -y
```

### 2. 지역 설치, 제거

```
npm install A

npm i A

npm uninstall A
```

### 3. 전역 설치

- 프로젝트에서 사용할 라이브러리를 불러올 때 사용하는 것이 아니라 시스템 레벨에서 사용할 자바스크립트 라이브러리를 설치할 때 사용

```
npm install A --global

npm install A -g
```

### 4. 지역 설치 옵션

1. --save-prod

- 화면 로직과 직접적으로 관련된 라이브러리는 배포용으로 설치
- npm run build로 빌드를 하면 최종 애플리케이션 코드 안에 포함된다.

2. --save-dev

- 빌드하고 배포할 때 애플리케이션 코드에서 빠지게 된다. (개발용)
- 최종 애플리케이션에 포함되어야 하는 라이브러리는 -D로 설치하면 안된다.
- 개발할 때만 사용하고 배포할 때는 빠져도 좋은 라이브러리 (webpack, eslint, imagemin, sass...)

```
1. dependencies
npm install A --save-prod
npm i A

2. devDependencies
npm install A --save-dev
npm i A -D
```
