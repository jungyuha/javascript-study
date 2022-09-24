---
description: Sort를 사용하여 Object를 Key 기준으로 정렬하기
---

# Sort를 사용하여 Object를 Key 기준으로 정렬하기

## \[예사] 아래 객체를 'Key\` 기준으로 정렬하는 방법 ! <a href="#q-key" id="q-key"></a>

```javascript
{
   "a1": true,
   "a2": true,
   "a3": true,
   "a4": true,
   "a5": true
}
```

### 1.  Object.keys()로 key 배열 생성하기 <a href="#1-objectkeys-key" id="1-objectkeys-key"></a>

> Object.keys()로 객체 `key`들의 배열을 생성한다.

```js
Object.keys(obj);
// ["a1", "a2", "a3",....]
```

### 2.  sort()로 정렬 시도하기 <a href="#1-objectkeys-key" id="1-objectkeys-key"></a>

```js
Object.keys(object).sort()
```

### 3.  reduce 함수를 통해 새로운 객체로 만들기 <a href="#1-objectkeys-key" id="1-objectkeys-key"></a>

기존 객체 object\[key] 값을 새로운 객체 newObj\[key]로 복사한다.

```js
Object.keys(object).sort().reduce(
      (newObj,key) => {
         newObj[key] = object[key];
         return newObj;
      },
      {}
   );
```

### 4. . key값으로 정렬된 새로운 객체가 생성된다. <a href="#1-objectkeys-key" id="1-objectkeys-key"></a>
