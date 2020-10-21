## Webpack
- A module bundler / works well with babel / local development server

1. 웹팩 설치 
```
npm install webpack webpack-cli --save-dev
```
2. 웹팩 실행

```
node_modules\.bin\webpack
```

```javascript
(()=>{const o=o=>{console.log("Hello "+o)};o("kim"),o("test2"),o("test3")})();
```
- output이었던 bundle.js는 이렇게 바뀌게 된다.

```
node_modules/.bin/webpack
```
- package.json에 script쪽에 명령어를 적어두면 그뒤로 자동화된다.

```
npm run webpack
```
- 파일 바꾼 이후로 확인할 수 있는 방법

### 웹팩을 ES6 모듈과 쓰는 방법

```
import './dom';
```
- index.js는 html 파일에 연결되어있다.
- dom.js 파일에 코드를 적는다 
- index.js에 `import './dom';`를 적는다.
- npm run webpack명령어를 터미널에 적는다
- dom.js를 import하기 때문에 index.js 1줄에 
- dom.js => index.js 순으로 파일이 실행된다.

- import는 결론적으로 파일을 가져오기만 하고, 안에있는 코드는 사용할 수 없다. (변수나 함수등)

- `export`키워드를 가져갈 코드 앞에 적어준다. 
- dom.js 파일에 `import{export키워드를 적은 함수, 변수이름} from './dom'`;
- 가져갈 코드가 많을 경우 맨 아래에 `export{변수1, 함수1, 변수3}`라고 한번에 적을 수 있다.

default exports
- 디폴트는 하나만 한다

- webpack.config.js
```
module.exports = {
  entry: './src/index.js', //상대주소 기입
  output: {
    path: path.resolve(__dirname, 'dist/assets'), //폴더이름은 기입 ㄴㄴ
    filename: 'bundle.js'
  },
  devServer: {
    contentBase:  path.resolve(__dirname, 'dist'), // absolute path for bundle.js to have server
    publicPath: '/assets/' // path in my folder
  }
};
```
- package.json
```
  "scripts": {
    "babel": "node_modules/.bin/babel src/index.js -w -o dist/assets/bundle.js",
    "webpack": "node_modules/.bin/webpack -w",
    "serve": "webpack-dev-server"
```
- 바벨로더 실행
```
npm install babel-loader --save -dev
```
