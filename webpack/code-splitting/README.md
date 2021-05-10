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

4. plugin

- 웹팩의 기본적인 동작에 추가적인 기능을 제공하는 속성
- 로더는 파일을 해석하고 변환하는 과정에 관여하는 반면, 플러그인은 해당 결과물의 형태를 바꾸는 역할을 한다.
- 플러그인의 배열에는 생성자 함수로 생성한 객체 인스턴스만 추가될 수 있다.

```
var webpack = require('webpack');
var HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  plugins: [
    new HtmlWebpackPlugin(),
    new webpack.ProgressPlugin()
  ]
}

```

---

# Code Splitting

1. 시작

```
npm init -y

npm i webpack webpack-cli css-loader style-loader mini-css-extract-plugin -D
```

2. html, css, js 생성

3. webpack.config.js 생성

4. plugin 적용

```
// webpack.config.js

var MiniCssExtractPlugin = require("mini-css-extract-plugin");

module: {
  rules: [
    {
      test: /\.css$/,
      use: [{ loader: MiniCssExtractPlugin.loader }, "css-loader"],
    },
  ],
},
plugins: [new MiniCssExtractPlugin()],

// index.html
// dist에 main.css가 따로 생김
<link rel="stylesheet" href="./dist/main.css" />
```

---

## 결과 분석

1. bundle.js

```
var ___CSS_LOADER_EXPORT___ = _node_modules_css_loader_dist_runtime_api_js__WEBPACK_IMPORTED_MODULE_0___default()(function(i){return i[1]});
// Module
___CSS_LOADER_EXPORT___.push([module.id, "p {\r\n  color: blue;\r\n}\r\n", ""]);
```

2. webpack.config.js

```
1) plugin 적용 이전
module: {
    rules: [
      {
        // 모든 css에 아래 loader 적용
        test: /\.css$/,
        // 오른쪽에서 왼쪽 순서로 loader를 실행시킨다.
        use: ["style-loader", "css-loader"],
      },
      // 적용할 것들을 배열에 추가
    ],
  },
```
