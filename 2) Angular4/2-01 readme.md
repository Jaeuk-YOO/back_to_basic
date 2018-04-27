2.01 식별자, 원시타입, 이스케이프 (18-04-26)
==

* 식별자 : 어렵게 생각하지 말자. 식별자는 변수 할당할 때, 함수 선언할 때 쓰는 글자를 말한다.
```js
    var this_is_var;
    let thisIsLet;
    const THISISCONST;
    // 이런 식으로 의미없이 대문자로 선언하면 등짝 스매싱당한다.
```
* 타입 : 종류들을 일단 알아만두자.  
primitive 원시타입 : number, string, boolean, null, undefined, symbol  
object 객체타입 : Array, Date, Regexp, Map, WeakMap, Set, Weakset

* 이스케이프 : 특수문자 앞에 역슬래시를 써서 특수문자를 문자 자체로 처리하는 경우.
```js
    var example1 = "She said, "Hello world, Hello Javascript!" Sam is crying."
    //위의 경우는 string처리가 제대로 되지 않아 string으로 인식하지 못하는 경우가 생긴다. 가운데 구문이 그렇다.

    var example2 = "She said, \"Hello world, Hello Javascript!\" Sam is crying."
    // 이 경우는 특수문자 앞에 역슬래시가 붙어서 처리되었다. 문자 자체로 처리되었다.
```  

* ES의 변수, 상수 특징 :  
```let```, ```const``` 기존에 없었던 변수와 상수 선언 방식들. ```const```는 javascript에서는 아예 다루지 않았다.    

    0) ```let```은 함수 호이스팅을 할 때 나올 것이기에 추후 설명하도록 한다.
    1) ```const```는 선언 후에는 할당된 값의 변경이 불가능하다. 상수이기 때문이다.
    2) ```__``` 언더바 두개로 시작하는 경우, 아주 특별한 경우에만 선언할 때 밑줄 두개로 시작하는데, 나만의 변수 카테고리를 만드는 경우는 밑줄로 만들어서 활용한다. rails의 helper의 느낌인 것 같다.