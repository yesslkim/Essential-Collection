## NPM and Babel

웹사이트 : ttps://babeljs.io/

Terminal에서 babel & NPM 설치
npm install -g npm

1.  Node가 설치 되어있는지 확인한다 : node -v
2.  시작할 폴더로 이동 : cd 폴더명 \*cd의 의미 - change directory
3.  NPM설치 : npm init to create a package.json file in the project directory  
    → package.json : keep tracking any packages that we installed
4.  Babel 설치 : npm install @babel/core @babel/cli --save-dev  
    → Use npm to install babel / core & babel / cli packages.
5.  Babel preset - certain language : npm install @babel/preset-env --save-dev
6.  Register it in .babelrc
7.  .babelrc의 내용
    {
    "presets" : ["@babel/preset-env"]
    }

Babel 사용방법

1. 터미널에 해당파일 경로인지 확인 후 입력 :  
   node_modules/.bin/babel before.js -o after.js 이거 안되면  
   node_modules\.bin\babel before.js -o after.js
   -o는 output이라는 뜻이다.

2. 용량이 너무 커서 노트 모듈은 업로드하지 않는다.  
   => package.json에서 필요한 패키지를 파악할 수 있다.  
   npm install로 다시 node_module을 다운받을 수 있다.

## common work flow (1번 - 2번 - 4번)

1. src 폴더 만든다 - 안에 index.js만들기 (우리가 직접 쓰는 자바스크립트코드)
2. dist 폴더 만든다 distribution폴더이다
   dist 폴더안 - assets 폴더 : bundle.js(바벨로 converting된 코드용) - index.html
3. Babel Cli 사용 : node_modules\.bin\babel src\index.js -o dist\assets\bundle.js.
4. 3번은 바꿀때마다 계속 해야한다. 그래서 package.json 스크립트에 넣어주고

```
  "scripts": {
    "babel": "node_modules/.bin/babel src/index.js -w -o dist/assets/bundle.js"
  },
```

- -w는 watch라는 뜻으로 알아서 바뀐점을 찾아서 변환해준다. 맨처음에는 터미널에 npm run babel입력해야됨!! (자동)

- -w를 안쓰면 터미널에 npm run babel이라고 입력하면 알아서 찾아서 바꿔준다. (수동)
