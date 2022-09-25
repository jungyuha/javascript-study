---
cover: >-
  https://images.unsplash.com/photo-1519389950473-47ba0277781c?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
---

# 프로토타입의 원리와 함께 class 변수 값 가공하기(작성중)

**기록 ✍️**

#### author : jung yuha

#### first registered : 2022-09-01

#### last modified : 2022-09-24 Sat.

## 내가 Class에서 변수값을 계산하다가 헤맨 이유&#x20;

1. **생성자를 통해 a , b, c 변수값을 초기화** 를 하고난 뒤에
2. 값이 할당된 a,b,c 값을 통해 복잡하게 계산된 d , e , f 변수를 클래스 내부에서 새로 할당하고 싶었다.

이 때, d ,e ,f는 외부에서 값을 변경할 일도 없고 따로 내부에서 계산된 값을 할당하려고 getter , setter를 설정하지 않았다.

아래와 같이 말이다.

```javascript
// testClass
module.exports =  class testClass {
    constructor(a,b,c){
        this.a = a;
        this.b = b;
        this.c = c;
        
        this.d = null;
        this.e = null;
        this.f = null;
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
    set c(value){
        this._c = value;
    }

    get c(){
        return this._c;
    }
    
    setDefValue(){
        this.d = this.a + this.b ;
    }
}
```

### Bio

{% hint style="info" %}
**Good to know:** Encourage employees to write a succinct bio that can help new hires learn about them and how they like to work.
{% endhint %}

## Rima Paterson

👋 CTO — 💌 rima@company.com — 🇳🇱 Amsterdam (GMT+1)

![](https://images.unsplash.com/photo-1502764613149-7f1d229e230f?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8\&ixlib=rb-1.2.1\&auto=format\&fit=crop\&w=2972\&q=80)

### Bio

{% hint style="info" %}
**Good to know:** Encourage employees to write a succinct bio that can help new hires learn about them and how they like to work.
{% endhint %}

## Stefan Barr

👋 Head of Product — 💌 stefan@company.com — 🇫🇷 Marseille (GMT+1)

![](https://images.unsplash.com/photo-1601935111741-ae98b2b230b0?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8\&ixlib=rb-1.2.1\&auto=format\&fit=crop\&w=2970\&q=80)

### Bio

{% hint style="info" %}
**Good to know:** Encourage employees to write a succinct bio that can help new hires learn about them and how they like to work.
{% endhint %}
