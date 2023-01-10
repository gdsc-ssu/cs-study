# 🍳 해시(Hash)

> 등장한지 아주 오래되었지만, 아직까지 연구되는 자료구조이다.
> 블록체인 기술에서 유용하게 사용된다고 한다.

해시를 쉽게 표현하자면 속도가 굉장히 빠른 ~~그리고 그것을 위해 리소스를 포기한~~ 자료구조라고 할 수 있다.<br/>
![image](https://velog.velcdn.com/images/igun0423/post/de13659d-b025-4de3-8092-cb12d575f1b5/image.png)<br/>
우선 위의 이미지를 보면 `Hash Function`과`Hashes`가 등장하는 것을 볼 수 있다.
결국 해시(Hash)란, 총 아래의 용어를 통합하여 일컫는 말이다.

- 해시 함수(Hash Function)
  - 해시 값(Hashes)
  - 해시 테이블(Hash Table)

그렇다면 왜 해시 값(Hashes)와 해시 테이블(Hash Table)이 해시 함수(Hash Function) 하위에 존재하는가?<br/>
이는 `해시(Hash)`가 동작하는 과정인 `해싱(Hashing)`을 보면 알 수 있다.

## 해싱(Hashing)

데이터가 `해시함수(Hash Function)`를 거쳐 고유한 `해시 값(Hashes)`으로 변환되고, 이 값은 `해시 테이블(Hash Table)`의 Index가 된다.
이 것이 `해싱(Hashing)`의 요약이다.

## 해시 함수(Hash Function)

해시 함수의 가장 중요한 점은, **입력 데이터를 반환하여 고유한 인덱스를 만들어낸다는 것이다.**<br/>
![](https://velog.velcdn.com/images/igun0423/post/d9b65639-1d86-4192-9853-aebe5cc8d3ec/image.png)<br/>

- 위 이미지와 같이, 어떤 연산을 거쳐서 **고유한 값**을 전달해야한다.
- 하지만 누구나 상상할 수 있는 가정이 있다.
- 만약, `해시 함수(Hash Function)`을 거친 데이터가 중복된다면?
  - `해시 테이블(Hash Table)`은 Key-Value의 형태인데, Value에 두개 이상의 값이 들어갈 수 있는가?

이를 위한 아주 다양한 `해시 알고리즘(Hash Algorithm)`이 존재한다.

### ✅ Division Method

_index = Key % 테이블 크기(테이블의 크기는 소수)_
대표적인 해시 함수 알고리즘이다.

### ✅ Digit Folding

Key의 문자열을 아스키코드로 변환하여 그 값을 모두 합한 값.
이 때, Index 값이 테이블의 크기를 넘어가면 `Division Method` 적용.

### ✅ Multiplication Method

- K : 숫자로 된 Key 값
- A : 0과 1 사이의 실수
- m : 2의 제곱수

_index = (K \* A mod 1) \* m_

> 이외에도 굉장히 많은 해시 함수 알고리즘이 존재한다고 한다.

## 충돌(Collision)

위에서 언급했던 가정처럼, Index값이 충돌(Collision)하는 경우 해결할 수 있는 방법이 필요하다.

### ✅ 분리 연결법(Separate Chaining)

![](https://velog.velcdn.com/images/igun0423/post/c3d5a4eb-39f8-465b-b760-afbcca47cfeb/image.png)<br/>

이름의 **Chain**에서부터 느낌이 오듯, `분리 연결법(separate Chaining)`은 버킷 내부의 데이터에 `연결 리스트(Linked List)` `트리`등의 자료구조를 적용하여 이어주는 방법이다.

이러한 Chaining 방식은 테이블 자체의 Resizing이 필요하지 않고, 원소를 쉽게 추가하고 삭제할 수 있다는 장점이 있다.

하지만 ~~안그래도 리소스 포기한 해시테이블~~ 리소스를 더 많이 필요로할 수 있다는 단점이 존재한다.

### ✅ 개방 주소법(Open Addressing)

`개방 주소법(Open Addressing)`은 버킷 내부에 빈자리에 먼저 데이터를 채워주며 테이블을 효율적으로 관리하는 방법이다.

**1. Linear Probing** - 현재 Index부터, 고정 값 만큼 이동하여 차례대로 데이터를 채워주는 방법

**2. Quadratic Probing** - n 번째 충돌의 경우, n^2만큼 이동하여 데이터를 채워주는 방법. 가령 1번 째는 1만큼, 2번째는 4만큼...

**3. Double Hasing Probing** - 해시된 값을 한 번 더 해싱하여 해시의 규칙을 없애는 방법. 새로운 테이블을 할당하고 연산하는 과정에서 더 많은 비용이 필요하게 된다.

## 해시 테이블(Hash Table)

### 장점

- 인덱스(index)로 인해 검색, 삽입, 삭제가 빠르다.
  - 데이터 캐싱에 많이 사용된다.
- `키(Key)`와 `해시값(Hashes)`사이에 연관성이 없기 때문에 보안이 뛰어나다.
  - 최근 블록체인의 핵심 기술
- 중복 제거에 용이하다.

### 단점

- 공간 복잡도가 크다.
- 데이터에 순서가 있는 경우, 어울리지 않는다.
- 해시 함수 의존도가 높다.

### 시간 복잡도

|      | 평균 | 최악 |
| ---- | ---- | ---- |
| 검색 | O(1) | O(n) |
| 삽입 | O(1) | O(n) |
| 삭제 | O(1) | O(n) |

# 자바스크립트와 해시(Hash)

## 기본 구조

```javascript
class HashTable {
  constructor(length) {
    this.table = new Array(length);
    this.size = 0;
  }
}
```

테이블의 크기(소수)를 받아 생성한다.

## 해시함수

```javascript
  _hash(key) {
    //Digit Folding 해시 알고리즘
    //해시 함수
    let hash = 0;
    for (let i = 0; i < key.length; i++) {
      hash += key.charCodeAt(i);
    }
    return hash % this.table.length;
  }
```

위에서 언급했던 세 가지 해시 알고리즘 중, `Digit Folding`을 사용하여 해시 함수를 구현하였다.

## set get remove

```javascript

  set(key, value) {
    const index = this._hash(key); //해시함수를 통해 고유한 해시 값 반환
    if (this.table[index]) {
      //충돌이 발생하는 경우, Separate Chaining 방식으로 해결
      for (let i = 0; i < this.table[index].length; i++) {
        if (this.table[index][i][0] === key) {
          this.table[index][i][1] = value;
          return;
        }
      }
      this.table[index].push([key, value]);
    } else {
      this.table[index] = [];
      this.table[index].push([key, value]);
    }
    this.size++;
  }

  get(key) {
    const index = this._hash(key);
    if (this.table[index]) {
      //Chain으로 이어져있는 것도 확인해야한다.
      for (let i = 0; i < this.table.length; i++) {
        if (this.table[index][i][0] === key) {
          return this.table[index][i][1];
        }
      }
    }
    return undefined;
  }

  remove(key) {
    const index = this._hash(key);

    if (this.table[index] && this.table[index].length) {
      for (let i = 0; i < this.table.length; i++) {
        if (this.table[index][i][0] === key) {
          this.table[index].splice(i, 1);
          this.size--;
          return true;
        }
      }
    } else {
      return false;
    }
  }
```

세 메소드 모두 충돌을 고려하여야한다.
충돌의 해결 방식으로, 위 코드에서는 `Separate Chaining`을 이용했다.

## 전체 코드

```javascript
class HashTable {
  constructor(length) {
    this.table = new Array(length);
    this.size = 0;
  }

  _hash(key) {
    //Digit Folding 해시 알고리즘
    //해시 함수
    let hash = 0;
    for (let i = 0; i < key.length; i++) {
      hash += key.charCodeAt(i);
    }
    return hash % this.table.length;
  }

  set(key, value) {
    const index = this._hash(key); //해시함수를 통해 고유한 해시 값 반환
    if (this.table[index]) {
      //충돌이 발생하는 경우, Separate Chaining 방식으로 해결
      for (let i = 0; i < this.table[index].length; i++) {
        if (this.table[index][i][0] === key) {
          this.table[index][i][1] = value;
          return;
        }
      }
      this.table[index].push([key, value]);
    } else {
      this.table[index] = [];
      this.table[index].push([key, value]);
    }
    this.size++;
  }

  get(key) {
    const index = this._hash(key);
    if (this.table[index]) {
      //Chain으로 이어져있는 것도 확인해야한다.
      for (let i = 0; i < this.table.length; i++) {
        if (this.table[index][i][0] === key) {
          return this.table[index][i][1];
        }
      }
    }
    return undefined;
  }

  remove(key) {
    const index = this._hash(key);

    if (this.table[index] && this.table[index].length) {
      for (let i = 0; i < this.table.length; i++) {
        if (this.table[index][i][0] === key) {
          this.table[index].splice(i, 1);
          this.size--;
          return true;
        }
      }
    } else {
      return false;
    }
  }

  display() {
    this.table.forEach((values, index) => {
      const chainedValues = values.map(
        ([key, value]) => `[ ${key}: ${value} ]`
      );
      console.log(`${index}: ${chainedValues}`);
    });
  }
}

const ht = new HashTable(127);

ht.set("Dogo", 111);
ht.set("Kitty", 150);
ht.set("Honey", 192);

ht.display();
/**
7: [ Honey: 192 ]
12: [ Dogo: 111 ] 
25: [ Kitty: 150 ]
 */

console.log(ht.size); // 3

ht.remove("Kitty");
ht.display();
/**
7: [ Honey: 192 ]
12: [ Dogo: 111 ]
*/
```

# Reference

[[자료구조] 해시 테이블(Hash Table) 이란? , 해시 알고리즘 , 해시 함수](https://code-lab1.tistory.com/14)
[[자료구조] Hash/HashTable/HashMap](https://hee96-story.tistory.com/48)
[JavaScript Hash Table – Associative Array Hashing in JS](https://www.freecodecamp.org/news/javascript-hash-table-associative-array-hashing-in-js/)
