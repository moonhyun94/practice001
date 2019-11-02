# Nodejs 공부하기

# 기본 활용법
-------------------------------
* nodejs.org-->docs로 들어가면 여러가지 내장 함수들을 검색할수있다.
* visual studio code를 이용할것이다.
* node (file name).js 를 이용하여 terminal에서 execution 할수있다.
* cd ../(folder name) << changing directory
 
# 문법 & 메소드
-------------------------------
* const 변수이름 = 'data'// 변수 설정
* console.log('hello') // 출력문
* fs.writeFileSync('filename','input') // writes a data in a file. if no file creates a file
- fs를 사용하기 위해선 const fs = require('fs') 를 해주어야만 한다!!
- require()은 node 내부 module을 사용할때 적어줘야하고 const fs 라는 변수를 설정하여 return값을 넣어주는 역할을 한다. 
- fs.appendFileSync('file name','data to append') // data를 추가해줌
- fs.readFileSync('file name')
- .toString() // data를 string 형태로 바꿈
- 다른 파일 동기화 하려면 require('./file name')을 해주면 된다.다른 파일에 있는 변수 함수 등등..은 넘어가지않음!
- 다른 파일에 있는 변수, 함수 등등.. 을 공유하고싶다면 module.exports = var name or func name 그리고 require('./file name') 의 return 값을 저장할 const var 를 설정해준다. ex) const name = require('./ustils.js')
* 함수 const add = function(){}
- forEach() // 주어진 함수를 배열 요소 각각에 실행함
- filter() // 주어진 함수의 조건을 통과한 모든 요소들을 새로운 배열로 반환
- find() 

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
4. yargs : command line argument parsing npm module
           Customizing yargs version : yargs.version('1.1.0') and execute node any.js --version int terminal
EX)
<pre><code>
커맨드 사용
termianl : node any.js add(setting a function) --(adding options to the function)title="Things to buy"
code: const yargs = require('yargs')
console.log(yargs.argv)
terminal : {_:[add],title:'Things to buy','$0':'any.js'}</pre></code>

# JSON
----------------------------
* JSON(JavaScript Object Notation) 
- JSON은 string data만을 처리
- JSON의 return 값은 binaray 이므로 return 값을 buffer라고 말함 
- JSON.stringify(obect,array 등..) Object, Array 등을 JSON string으로 바꿔줌 
- JSON.parse() JSON string을 Object, Array 등으로 반환해주는 작업
# 활용
----------------------------
1. getting input from users
 - node any.js add //이걸로 add 라는 action을 취할수있게 함
 -> console.log(proccess.argv[2]) // array 이며 사용자가 입력한 값을 배열 형태로 보여줌
 
 EX)
 <pre><code>
 const command = process.argv[2] << add를 저장하고있음

if (command === 'add') {
    console.log('Adding note!')
}
terminal : node any.js add
-> Adding note! 가 출력</code></pre>

# ArrowFunction
------------------------------
function을 만드는 여러가지 방법
1. const square = function(x){return x*x} // 일반적인 형태
2. const square = (x) =>{return x*x} //arrow-function 형태
3. const square = (x) => x*x // arrow-function 형태 return만 한다면 {} 필요 없음
4. 보통 함수 or 객체들은 자기자신을 가리키는 "this"바인딩이 존재 
   하지만 arrow-function은 "this" 바인딩이 존재하지않음!!
<pre><code>
EX1) 일반적인 형태
const event = {name:'Party',
                   guestList:['Lee','Han','Huh'] //string 배열
                   printGuestList: function(){
                   console.log('Guest list for '+this.name)
              this.guestList.forEach((guest))=>{
              console.log(guest + ' is attending '+ this.name)})
              } //event 객체 생성
              event.printGuestList() // printGuestList 함수 호출
EX2)
printGuestList(){
console.log('Guest list for '+this.name)} // 이렇게도 함수 선언 가능! ES6 방식
EX3) 에러!
printGuestList(){
        console.log('Guest list for '+ this.name)

        this.guestList.forEach(function(guest){
            console.log(guest + ' is attending '+ this.name)
        }) // 오류발생!! this.name 이 부모의 this와 바인딩 하지 못함! 
           //이럴땐 arrow-function을 사용한다 자신의 "this"바인딩이 존재하지 않기 때문
EX3) 수정
printGuestList(){
        console.log('Guest list for '+ this.name)

        this.guestList.forEach((guest)=>{
            console.log(guest + ' is attending '+ this.name)
        })
</pre></code>        
