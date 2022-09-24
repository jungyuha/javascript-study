# Getter,Setter 원리

## 💡 Class 생성자에서 값을 할당하는 부분은 실제로 해당 변수에 값을 할당하는 게 아니다 !

아래에서 차근차근 살펴보도록 하자 !

## \[1] Getter,Setter가 있는 class의 변수를 참조하는 과정

### Getter,Setter가 있는 class 예시

#### 1. 클래스 선언

<pre class="language-java"><code class="lang-java">// testClass.js
module.exports =  class testClass {
    constructor(){
        this.a = null;
        this.b= null;
    }
<strong>    set a(value){
</strong>        this._a = value;
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
}</code></pre>

#### 2. 인스턴스 생성

```javascript
// main.js
const testClass = require('../class/testClass');

testClass1 = new testClass();
console.log(testClass1);
```

#### 3. 결과

a , b는 확인할 수 없고 프로토타입만이 존재한다.

```
testClass { _a: null, _b: null }
```

### this.a 와 this.b에 숨겨진 동작&#x20;

#### 내가 잘못 생각했던 부분

a와 b라는 이름을 가진 변수가 메모리에 할당되고 this.a =  null; this.b = null; 을 통해 다음과 같은 모양의 클래스가 나올 줄 알았다.

```
testClass { a: null, b: null }
```

#### 실제 동작

실제로는 this.a  = null; 라는 명령어가 a 를 직접 메모리에 할당하여 값을 주는 게 **아니었다.**

⭐️⭐️⭐️⭐️⭐️ **this.a 와 this.b 는 사실 set a , set b 메서드 인 것이었다 !** ⭐️⭐️⭐️⭐️⭐️

<pre class="language-javascript"><code class="lang-javascript"><strong>    set a(value){
</strong>        this._a = value;
    }
    set b(value){
        this._b = value;
    }</code></pre>

**즉 , 애초에 a와 b는 생성자가 실행될 때부터 할당되지 않고 바로 setter 내에 있는 this.\_**_**a와 this.\_b 문을 통해 \_a와 \_b가 할당된 것이다.**_

_이 때 \_a와 \_b에 대한 getter ,setter는 없으므로  **\_a와 \_b가 할당이 될 수 있는 것이다.**_

{% hint style="info" %}
🤔 **만약 **_**\_a와 \_b에 대한 setter가 또 있었다면?**_

_**\_a와 \_b가**_ ⭐️_**할당되지 않고**_ ⭐️ _**\_a와 \_b에 대한 setter 가 실행된다.**_
{% endhint %}

## ⭐️결론⭐️

**setter가 있는 클래스 내의 변수를 참조할 땐 해당 변수의 Setter가 존재할 시 직접 메모리에서 참조되지 않고 Setter가 실행된다.**

**Setter가 없으면 그제서야 해당 변수가 참조된다.**



















때&#x20;
