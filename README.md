---
description: 자바스크립트에서 클래스를 생성하는 다양한 방법과 Getter , Setter를 제대로 활용하기
cover: >-
  https://images.unsplash.com/photo-1552664730-d307ca884978?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
---

# 다양한 Class 생성 방법과 Getter Setter

**기록 ✍️**

#### author : jung yuha

#### first registered : 2022-09-01

#### last modified : 2022-09-24 Sat.

## \[1] getter , setter 없이 생성자에서 각 값에 null 할당하여 Class 선언하기&#x20;

getter , setter 없이 생성자에서 각 값에 널값을 **할당**하다면 처음 인스턴스가 생성될 때 a 와 b 값은 어떤 형태로 있을지 궁금했다.

#### 1. 클래스 선언하기

```javascript
// testClass.js
module.exports =  class testClass {
    constructor(){
        this.a = null;
        this.b= null;
    }
}
```

#### 2. 인스턴스 확인하기

```javascript
// main.js
const testClass = require('../class/testClass');

testClass1 = new testClass();
console.log(testClass1);
```

#### 3. 콘솔 결과

```
testClass { a: null, b: null }
```

### 결과

각 변수가 메모리에 할당되고 해당 값에 null값이 들어간다.

## \[2] getter , setter 없이 생성자에서 각 값에 null 주입하여 Class 선언하기&#x20;

getter , setter 없이 생성자에서 각 값에 널값을 **주입**하다면 처음 인스턴스가 생성될 때 a 와 b 값은 어떤 형태로 있을지 궁금했다.

#### 1. 클래스 선언하기

```javascript
// testClass.js
module.exports =  class testClass {
    constructor(a,b){
        this.a = a;
        this.b= b;
    }
}
```

#### 2. 인스턴스 확인하기

```javascript
// main.js
const testClass = require('../class/testClass');

var a = null;
var b = null;

testClass1 = new testClass(a,b);
console.log(testClass1);
```

#### 3. 콘솔 결과

```
testClass { a: null, b: null }
```

### 결과

각 변수가 메모리에 할당되고 해당 값에 null값이 들어간다.

## \[3] 생성자에서 각 값에 널값을 할당한 후 getter , setter 사용하기&#x20;

getter , setter가 있는 생성자에서 각 값에 널값을 **할당**한 후 처음 인스턴스가 생성된 후 a 와 b 값의 값을 설정할 때 a,b 값의 상태가 어떻게 변하는지 알아보자!

#### 1. 클래스 선언하기

```javascript
// testClass.js
module.exports =  class testClass {
    constructor(){
        this.a = null;
        this.b = null ;
    }

    set a(value){
        this._a = value;
    }

    get a(){
        return this._a;
    }

    set b(value){
        this._b = value;
    }

    get b(){
        return this._b;
    }
}
```

#### 2. 인스턴스 생성하기

```javascript
// main.js
const testClass = require('../class/testClass');

testClass1 = new testClass();

testClass1.a = 'a';
testClass1.b = 'b';

console.log(testClass1);
```

### 예상 결과

1. 각 변수 **a와 b**가 메모리에 할당되고 생성자에 의해 해당 값에 각각  null 값이 할당된다.
2. 아래 코드를 통해 getter , setter가 작동하면서 'a' 변수와  '\_b' 변수가 메모리에 할당되고 각각 'a'와 'b'값이 들어간다.

<pre class="language-javascript"><code class="lang-javascript"><strong>testClass1.a = 'a';
</strong>testClass1.b = 'b';</code></pre>

즉 , 아래와 같이 4개의 변수가 메모리에 할당될 줄 알았다.😅

```
testClass { a: null, b: null , _a : 'a' , _b : 'b' }
```

### 실제 결과

1. 각 변수 **a와 b**는 메모리에 할당되지 않았.
2. 아래 코드를 통해 getter , setter가 작동하면서 'a' 변수와  '\_b' 변수가 메모리에 할당되고 각각 'a'와 'b'값이 들어갔다.

```javascript
testClass1.a = 'a';
testClass1.b = 'b';
```

즉 , 아래와 같이 2개의 프로토타입('a'와 '\_b')이 객체에 존재한다.

<pre><code><strong>testClass { _a: 'a', _b: 'b' }</strong></code></pre>

## \[4] 생성자에서 각 값에 널값을 주입한 후 getter , setter 사용하기&#x20;

getter , setter가 있는 생성자에서 각 값에 널값을 **주입**한 후 처음 인스턴스가 생성된 후 a 와 b 값의 값을 설정할 때 a,b 값의 상태가 어떻게 변하는지 알아보자!

#### 1. 클래스 선언하기

```javascript
// testClass.js
module.exports =  class testClass {
    constructor(a,b){
        this.a = a;
        this.b = b ;
    }

    set a(value){
        this._a = value;
    }

    get a(){
        return this._a;
    }

    set b(value){
        this._b = value;
    }

    get b(){
        return this._b;
    }
}
```

#### 2. 인스턴스 생성하기

```javascript
// main.js
const testClass = require('../class/testClass');

var a = null;
var b = null;

testClass1 = new testClass(a,b);

testClass1.a = 'a';
testClass1.b = 'b';

console.log(testClass1);
```

### 예상 결과

1. 각 변수 **a와 b**가 메모리에 할당되고 생성자에 의해 해당 값에 각각  null 값이 할당된다.
2. 아래 코드를 통해 getter , setter가 작동하면서 'a' 변수와  '\_b' 변수가 메모리에 할당되고 각각 'a'와 'b'값이 들어간다.

```javascript
testClass1.a = 'a';
testClass1.b = 'b';
```

즉 , 아래와 같이 4개의 변수가 메모리에 할당될 줄 알았다.😅

```
testClass { a: null, b: null , _a : 'a' , _b : 'b' }
```

### 실제 결과

1. 각 변수 **a와 b**는 메모리에 할당되지 않았.
2. 아래 코드를 통해 getter , setter가 작동하면서 'a' 변수와  '\_b' 변수가 메모리에 할당되고 각각 'a'와 'b'값이 들어갔다.

```javascript
testClass1.a = 'a';
testClass1.b = 'b';
```

즉 , 아래와 같이 2개의 프로토타입('a'와 '\_b')이 객체에 존재한다.

<pre><code><strong>testClass { _a: 'a', _b: 'b' }</strong></code></pre>

## 결론

**getter, setter가 존재하는** 클래스 내부 환경에는 클래스 내부에서 선언한 변수와 **프로토타입**이 따로 있으며 **실질적으로 프로토타입의 값을 참조한다.**

**즉, 클래스의 변수를 참조할 때는 아래와 같이 변수명(a와 b)을 그대로 써도**\
**클래스 내부 프로토타입의 값('a'와 '\_b')이 참조되어 리턴된다.**

```javascript
testClass1.a = 'a';
testClass1.b = 'b';
```

