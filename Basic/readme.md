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
<pre><code>
const str = `this is 
                  example`;
</code></pre>

- Object 타입에는 Primitive Value를 제외한 값을 모두 할당할 수 있다.
- Symbol은 객체 Property Key로 사용될 수 있다.
- tuple 형태를 정의할 수 있으며, 다음과 같이 inline annotation이 가능하다.
```
let tuple:[number, string];
let tuple3:[number, number, number];
```

## Interface
- 작성예정

## Reference
- FastCampus Typescript 온라인 강좌(Teacher: Harry)
