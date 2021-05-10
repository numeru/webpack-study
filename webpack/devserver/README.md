# dev server

- 다시 build 할 필요 없이 변경된 코드를 바로 적용시켜준다.

1. 시작

```
npm init -y

npm i webpack webpack-cli webpack-dev-server html-webpack-plugin -D
```

2. script 속성에 명령어 추가

```
"scripts": {
  "dev": "webpack serve"
},
```

3. html, js 파일 생성

4. webpack.config.js 생성

5. 실행

```
npm run dev
```
