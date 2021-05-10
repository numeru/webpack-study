# Tutorial

1. 시작

```
npm init
```

2. webpack 관련 라이브러리와 lodash 설치

```
npm i webpack webpack-cli -D
npm i lodash
```

3. index.html, index.js 생성

4. package.js에 웹팩 빌드 명령어 추가

```
"scripts": {
  "build": "webpack"
}
```

5. webpack.config.js 파일 생성

6. 실행

```
npm run build
```

---

# 주요 속성

1. entry

- 웹팩에서 웹 자원을 변환하기 위해 필요한 최초 진입점이자 자바스크립트 파일 경로

```
module.exports = {
  entry: './src/index.js'
}
```

2. output

- 웹팩을 돌리고 난 결과물의 파일 경로를 의미

```
1)
module.exports = {
  output: {
    filename: 'bundle.js'
  }
}

2)
var path = require('path');

module.exports = {
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, './dist')
  }
}
```

3. loader

- 웹팩이 웹 애플리케이션을 해석할 때 자바스크립트 파일이 아닌 웹 자원(HTML, CSS, Images, 폰트 등)들을 변환할 수 있도록 도와주는 속성

```
module.exports = {
  module: {
    rules: []
  }
}
```
