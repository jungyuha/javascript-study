---
description: 객체에 해당 key값이 존재 유무 확인하기
---

# 객체에 해당 key값이 존재 유무 확인하기

**기록 ✍️**

#### author : jung yuha

#### first registered : 2022-10-03 Mon

#### last modified : 2022-10-03 Mon

## \[1] Object의 keys 이용하기

Object.keys는 객체의 키를 배열로 리턴한다.&#x20;

```javascript
const object_1 = {
    key_1:'cont 1',
    key_3:undefined
}

const isExist_1 = Object.keys(object_1).includes('key_1')
const isExist_2 = Object.keys(object_1).includes('key_2')
const isExist_3 = Object.keys(object_1).includes('key_3')

console.log(isExist_1) // true
console.log(isExist_2) // false
console.log(isExist_3) // true
```

위와 같이 undifined도 '존재한다.'로 판단한다.

## \[2] key in Object

최근 자바스크립트 기본을 다시 다지기 위해 읽는 [사이트](https://ko.javascript.info/)에 예제가 있었다.\
기본도 못하고 있다는 생각이 들어버렸다.. 방법은 간단했다.

```javascript
const object_1 = {
	key_1:'cont 1',
	key_3:undefined
}

console.log( 'key_1' in object_1 ) // true
console.log( 'key_2' in object_1 ) // false
console.log( 'key_3' in object_1 ) // true

Object.prototype.key_2 = undefined
console.log( 'key_2' in object_1 ) // true
```

위와 같이 Object의 프로토타입 체인으로 생성한 프로퍼티도 체크한다.

## \[3] Object.hasOwnProperty <a href="#4-objecthasownproperty" id="4-objecthasownproperty"></a>

* Object.hasOwnProperty는 **객체가 특정 프로퍼티를 소유했는지**를 알려준다.
* **프로토타입 체인을 통해 상속되지 않은 속성인지 또는 직접 속성인지를  boolean으로 반환**한다.

```javascript
const object_1 = {
	key_1:'cont 1',
	key_3:undefined
}

console.log( object_1.hasOwnProperty('key_1') ) // true
console.log( object_1.hasOwnProperty('key_2') ) // false
console.log( object_1.hasOwnProperty('key_3') ) // true

Object.prototype.key_2 = undefined

console.log( object_1.hasOwnProperty('key_2') ) // false
```

* **프로토타입 체인을 통해 상속되지 않은 속성인 key\_2는 false로 나온다.**
* 해당 객체의 직접적인 속성만을 검사 할 수 있다.\
