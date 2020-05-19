# 기초지식, 자료형 정리
Typescript의 기초 지식 및 자료형에 대해 정리한 내용입니다.
<br>

## 정의

## Javascirpt vs Typescirpt ?

## 자료형
- Javascript의7가지 type을 유사하게 가지고 있다.(ES6기준)
  - null, undefined, boolean, number, string, object, symbol
- null과 undefined 타입은 서로 할당이 가능하다. 그러나 같은 타입은 아니다.
- null, undefined 타입은 모든 type의 하위타입으로 모든 상위 타입에 할당될 수 있다.
- string 문자열에 여러줄을 입력하러면개행문자를 사용해야한다.
<pre><code>const str = `this is 
            example`</code></pre>

- Object 타입에는 Primitive Value를 제외한 값을 모두 할당할 수 있다.
- Symbol은 객체 Property Key로 사용될 수 있다.
- tuple 형태를 정의할 수 있으며, 다음과 같이 inline annotation이 가능하다.
```
let tuple:[number, string];
let tuple3:[number, number, number];
```

## Interface
- `Interface`키워드는 기존 OOP언어들처럼(Java) Type을 정의하는 역할을 한다.
  - 해당 Type의 형태 및 속성만을 기술하며 Body-Block이 없다.
  - 해당 Person을 가지는 클래스 또는 변수등은 해당 interface에서 가지는 속성과 메서드를 반드시 실행해야한다.
  ``` 
  interface Person{
    name:string
    age:number
    speak():void
  }
  
  const student:Person = { 
                           name:'Sam', 
                           age:'13', 
                           speak:()=>{ console.log("My name is "+this.name+"and, I'm "+this.age)};
                         }
  ```
  - 실체 구현체와 관련없이 같은 동작(행위) 또는 변수(데이터)를 가질때 interface를 사용한다.
  - 어떤 여러 구현체가 같은 동작 또는 변수를 가진다면 interface를 사용하면 유용하다.
  
## Function
- 파라미터값들의 자료형과 리턴값의 자료형을 지정할 수 있다. -> 해당 자료형 이외의 값을 넣으면 TypeError 오류를 출력한다.
- 함수의 리턴값을 밝혀주지 않으면 파라미터값의 자료형을 통해 리턴값 자료형을 예측한다.
```
function add(x:number, y:number){
           return a+b;
}

const result1 = add(1,2);//3
const result2 = add(1,'s');//TypeError
const result3 = add();//인수값없이 실행할 수 없다.
```
- 함수의 파라미터값에는 기본값(default)을 설정할 수 있다. -> 함수에 파라미터를 넣지 않으면 자동으로 기본값이 적용된다.
- 함수의 파라미터값에 `?` 라는 optional 설정을 붙여주면 실행된다. -> 파라미터를 넣지 않아도 실행된다.
```
function add(x?=1, y?=2){
           return a+b;
}

const result1 = add(1,2);//3
const result2 = add(1,'s');//TypeError
const result3 = add();//3
```
- 화살표함수(Arrow function)의 annotaion은 일반 function과 똑같다.
```
(a:number,b:number):number => a+b;
```
- 오버로딩(Overloading)을 사용할 수 있다. -> 반환형 타입, 매개변수의 종류 및 개수가 다른 같은 이름의 함수를 여러개 선언하는 것 
- __정적언어type인 TS, 동적언어type인 JS의 차이점__ 중 하나이다.
- `|(union)` 연산자를 이용해 Overloading 해준다.
```
function store(type: string):Storage

interface Storage{...}, interface ColdStorage{...}
function store(type: "noodle"):Storage
function store(type: "icecream"):ColdStorage

//다음과 같이 같은 이름의 함수들을 오버로딩 해준다.
function store(type: "noodle"|"icecream"){
        if(type==="noodle") return (...)//Storage type
        else return (...)//ColdStorage type
}
```

## enum
- 작성예정

## Class
- 작성예정

## Reference
- FastCampus Typescript 온라인 강좌(Teacher: Harry)
