# Getter,Setter μλ¦¬

## π‘ Class μμ±μμμ κ°μ ν λΉνλ λΆλΆμ μ€μ λ‘ ν΄λΉ λ³μμ κ°μ ν λΉνλ κ² μλλ€ !

μλμμ μ°¨κ·Όμ°¨κ·Ό μ΄ν΄λ³΄λλ‘ νμ !

**κΈ°λ‘ βοΈ**

#### author : jung yuha

#### first registered : 2022-09-01

#### last modified : 2022-09-24 Sat.

## \[1] Getter,Setterκ° μλ classμ λ³μλ₯Ό μ°Έμ‘°νλ κ³Όμ 

### Getter,Setterκ° μλ class μμ

#### 1. ν΄λμ€ μ μΈ

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

#### 2. μΈμ€ν΄μ€ μμ±

```javascript
// main.js
const testClass = require('../class/testClass');

testClass1 = new testClass();
console.log(testClass1);
```

#### 3. κ²°κ³Ό

a , bλ νμΈν  μ μκ³  νλ‘ν νμλ§μ΄ μ‘΄μ¬νλ€.

```
testClass { _a: null, _b: null }
```

### this.a μ this.bμ μ¨κ²¨μ§ λμ&#x20;

#### λ΄κ° μλͺ» μκ°νλ λΆλΆ

aμ bλΌλ μ΄λ¦μ κ°μ§ λ³μκ° λ©λͺ¨λ¦¬μ ν λΉλκ³  this.a =  null; this.b = null; μ ν΅ν΄ λ€μκ³Ό κ°μ λͺ¨μμ ν΄λμ€κ° λμ¬ μ€ μμλ€.

```
testClass { a: null, b: null }
```

#### μ€μ  λμ

μ€μ λ‘λ this.a  = null; λΌλ λͺλ Ήμ΄κ° a λ₯Ό μ§μ  λ©λͺ¨λ¦¬μ ν λΉνμ¬ κ°μ μ£Όλ κ² **μλμλ€.**

β­οΈβ­οΈβ­οΈβ­οΈβ­οΈ **this.a μ this.b λ μ¬μ€ set a , set b λ©μλ μΈ κ²μ΄μλ€ !** β­οΈβ­οΈβ­οΈβ­οΈβ­οΈ

<pre class="language-javascript"><code class="lang-javascript"><strong>    set a(value){
</strong>        this._a = value;
    }
    set b(value){
        this._b = value;
    }</code></pre>

**μ¦ , μ μ΄μ aμ bλ μμ±μκ° μ€νλ  λλΆν° ν λΉλμ§ μκ³  λ°λ‘ setter λ΄μ μλ this.\_**_**aμ this.\_b λ¬Έμ ν΅ν΄ \_aμ \_bκ° ν λΉλ κ²μ΄λ€.**_

_μ΄ λ \_aμ \_bμ λν getter ,setterλ μμΌλ―λ‘  **\_aμ \_bκ° ν λΉμ΄ λ  μ μλ κ²μ΄λ€.**_

{% hint style="info" %}
π€ **λ§μ½ **_**\_aμ \_bμ λν setterκ° λ μμλ€λ©΄?**_

_**\_aμ \_bκ°**_ β­οΈ_**ν λΉλμ§ μκ³ **_ β­οΈ _**\_aμ \_bμ λν setter κ° μ€νλλ€.**_
{% endhint %}

## β­οΈκ²°λ‘ β­οΈ

**setterκ° μλ ν΄λμ€ λ΄μ λ³μλ₯Ό μ°Έμ‘°ν  λ ν΄λΉ λ³μμ Setterκ° μ‘΄μ¬ν  μ μ§μ  λ©λͺ¨λ¦¬μμ μ°Έμ‘°λμ§ μκ³  Setterκ° μ€νλλ€.**

**Setterκ° μμΌλ©΄ κ·Έμ μμΌ ν΄λΉ λ³μκ° μ°Έμ‘°λλ€.**



















λ&#x20;
