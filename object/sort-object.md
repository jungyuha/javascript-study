---
description: Sort를 사용하여 Object를 특정 요소 기준으로 정렬하기
---

# Sort를 사용하여 Object를 특정 요소 기준으로 정렬하기

**기록 ✍️**

#### author : jung yuha

#### first registered : 2022-09-25 Sun.

#### last modified : 2022-09-25 Sun.

## \[예시 배열]

```javascript
let sortArray = [
    {name:'cara11', age:28},
    {name:'cara12', age:21},
    {name:'cara13', age:20},
    {name:'cara14', age:64},
    {name:'cara15', age:57},
];
```

### 1. 기존 객체 복사하(deep copy)

정렬하기 전과 정렬 후의 객체를 비교하기 위해서 정렬전의 객체를 복사(deep copy)해 준다.

이 때 객체의 함수는 복사하지 않는다.

```javascript
let beforeArray = JSON.parse(JSON.stringify(sortArray));
```

객체의 함수까지 복사하려면 아래와 같이 쓴다.

```javascript
let beforeArray = {...sortArray};
```

### 2. 객체 요소 age를 기준으로 정렬하기

```javascript
sortArray.sort((a,b)=>{
    if(a.age>b.age) {
        return 1;
    }
    if(a.age<b.age) {
        return -1;
    }
    return 0;
});
```

### 3.테스트

```javascript
console.log('>>> before');
console.log(beforeArray);
 
console.log('>>> after');
console.log(sortArray);
```

![](<../.gitbook/assets/image (1).png>)
