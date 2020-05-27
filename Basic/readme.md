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
- 열거형으로 상수의 집합에 이름을 부여할때 사용한다.
```
enum Grade{
  BRONZE,
  GREEN,
  SILVER,
  GOLD
}
```
- 다음과 같이 enum형 Grade를 선언하면 기입한 순서대로 양방향 key-value를 형성한다.
    *  `0`  : `BRONZE`,  `1`: `GREEN`, `2`: `SILVER`, `3`: `GOLD`
    *   `BRONZE`: `0` , `GREEN`:`1`, `SILVER`:`2`, `GOLD`:`3`
- 만약 특성인덱스(key)를 고정하고 싶으면 `SILVER=2`처럼 초기값을 설정해준다(Initializer).
    * 기본값으로 설정된 key와 쌍을 이루고, 그 이후에 선언된 값들은 기본값으로부터 +1 된다.
- 초기값을 string형으로 지정해줄 수도 있다.

## Class
- Class를 통해 특정 타입의 객체를 생성할 수 있다.
- 일반적으로 생성자함수, get함수, set함수로 이루어진다.
- Counstructor(생성자)에 명시적으로 접근제한자 및 속성명을 설정하면 속성의 정의와 할당을 생성자함수내부에서 모두 실행할 수 있다.
```
Class Cart{
  constructor(Private user:string){
    this.user = user;
  }
  
  function get():string{
    return this.user;
  }
  
  function set(name:string):void{
    this.user = name;
  }
}
```
- __Public Keyword__
  * default값이다. -> 명시하지 않으면 public으로 취급된다.
  * Class 외부에서 속성 메서드에 접근할 수 있다.
- __Private Keyword__
  * Class 외부에서의 속성, 메서드 접근을 제한한다.
  * 일반적으로 속성값을 private로 두고 내부의 Public get, set 메서드로 접근한다.
- __Protected Keyword__
  * 다른 Class에 extends를 통해 Class의 특정 속성과 메서드를 상속할 수 있다.
- extends를 통해 부모클래스를 상속받은 하위클래스 생성자는 부모클래스의 생성자를 불러올 수 있다. -> super()
- `Class 클래스명 implements 참조인터페이스`를 통해 참조할 수 있다.
- `Class 클래스명 extends 상위클래스 implements 참조인터페이스`를 통해 상위클래스와 참조인터페이스를 동시에 설정가능하다.
- __Abstract Class(추상클래스)
  * 특정 속성, 메서드를 하위 클래스에서 가지도록 지정가능
  * `abstract Class 클래스명{ abstract 상속할속성이나 메서드 }`로 작성한다.
  * 추상클래스는 인스턴스값을 만들 수 없다.
  
## Reference
- FastCampus Typescript 온라인 강좌(Teacher: Harry)
