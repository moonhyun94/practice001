##Nodejs 공부하기
================================
#기본 활용법
-------------------------------
* nodejs.org-->docs로 들어가면 여러가지 내장 함수들을 검색할수있다.
* visual studio code를 이용할것이다.
* node (file name).js 를 이용하여 terminal에서 execution 할수있다.

#문법
-------------------------------
* const 변수이름 = 'data'// 변수 설정
* console.log('hello') // 출력문
* fs.writeFileSync('filename','input') // writes a data in a file. if no file creates a file
- fs를 사용하기 위해선 const fs = require('fs') 를 해주어야만 한다!!
- require()은 node 내부 module을 사용할때 적어줘야하고 const fs 라는 변수를 설정하여 return값을 넣어주는 역할을 한다. 
- fs.appendFileSync('file name','data to append') // data를 추가해줌
- 다른 파일 동기화 하려면 require('./file name')을 해주면 된다.다른 파일에 있는 변수 함수 등등..은 넘어가지않음!
- 다른 파일에 있는 변수, 함수 등등.. 을 공유하고싶다면 module.exports = var name or func name 그리고 require('./file name') 의 return 값을 저장할 const var 를 설정해준다. ex) const name = require('./ustils.js')
* 함수 const add = function(){}

# NPM Module
------------------------------
* local npm modules , global npm modules
* www.npmjs.com/package
* initiallizing npm project: npm init
* installing npm package: npm i (package name)@(version) -g<< globally installing npm module
1. validator : validating emails , urls, phone numbers , social security numbers, credit cards and other types of string information
2. chalk
3. nodemon : nodemon app.js << 코드를 바꾸면 자동으로 terminal에서 실시간으로 바꿔주는 npm
종료하기 : ctrl + c

# aa
----------------------------
1. getting input from users
 - node any.js add //이걸로 add 라는 action을 취할수있게 함
 >> console.log(proccess.argv[2]) // array 이며 사용자가 입력한 값을 배열 형태로 보여줌
 EX)
 <pre><code>
 const command = process.argv[2] << add를 저장하고있음

if (command === 'add') {
    console.log('Adding note!')
}</code></pre>
