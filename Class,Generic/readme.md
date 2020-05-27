# Class, Generic
Typescript의 Class, Generic에 대한 설명입니다.
<br>

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

## Generic
- 작성예정

<br/>

> 👉[목차로 돌아가기](https://github.com/ss-won/TypeScript)
> > 👉 다음장 : [고급타입](https://github.com/ss-won/TypeScript/tree/master/AdvancedType)
<br/>

## Reference
- FastCampus Typescript 온라인 강좌(Teacher: Harry)
