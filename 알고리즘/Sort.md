# 🧩 Sort(정렬)

> 기초적인 정렬 방식 3가지와 함께, 이를 `Javascript`로 구현한다.

`정렬`이란, 무작위로 섞여있는 데이터를 어떤 기준에 대하여 순서대로 나열하는 것을 의미한다.

## 🐾 정렬의 목적

1. 무작위 데이터의 순차적 나열
2. 데이터 분포도의 중위값 찾기
3. 중복값 찾기
4. 이진탐색

일반적으로 프로그래밍 언어에서 정렬 메소드를 제공한다.<br/>
그럼에도, **정렬 알고리즘을 직접 구현하는 것에는 크게 두 가지 이유가 있다.**

1. 정렬 메소드가 최적의 퍼포먼스를 보장하지 않는다.
2. 상황에 따라 효율적인 정렬 알고리즘이 달라진다.

## 1️⃣ Bubble Sort

![Bubble_sort_animation](https://user-images.githubusercontent.com/44965706/216213964-207e797e-8778-4fee-ba30-b4e982e00d42.gif)

1. 데이터를 2개씩 묶어서 비교한다.
2. 더 큰 데이터가 오른쪽에 위치할 수 있도록 순서를 변경한다.
3. 한 바퀴를 돌았을 때, 가장 큰 값이 결정된다.
   - 리스트의 가장 오른쪽 값이 결정된다.

**즉, n번째 정렬이 끝나면 - 뒤에서부터 n번째 자리의 데이터가 결정된다.**

### 👍 Best Case

- 모든 값이 정렬된 경우
- 시간 복잡도는 **O(n)**

### 👎 Worst Case

![BubbleSort_worst_case](https://user-images.githubusercontent.com/44965706/216212227-de3dea56-c75c-4aa2-90b7-985d16be1d83.gif)

- 모든 값이 역정렬 되어있는 경우
- 시간 복잡도는 **$O(n^2)$**
  - 각 자리를 찾기 위해 n번의 순회한다.
  - 순회 동안, 요소 개수 만큼 또 순회를 해야한다.

### ✅ 장점

- `in place` 알고리즘으로, 메모리가 절약된다.
  - 정렬 과정에서 추가적인 메모리 공간이 아닌, 기존의 공간 내에서 해결한다.
- 구현이 쉽다.
  - 이미 정렬된 경우, 시간 복잡도가 낮기 때문에 **정렬 확인용**으로도 사용된다.

### ✅ 단점

- 자료의 개수가 많아질수록 성능이 매우 떨어진다.
  - 가령, `1,000개`의 데이터가 있는데 최악의 경우라면 `1,000,000번`의 탐색을 해야한다.

### ✅ Stable

- 중복된 데이터가 있다면, 위치를 바꾸지 않는다.
  - `Stable`이란, 중복 데이터가 있는 경우에 정렬이 끝난 후에도 순서가 유지되는 것을 의미한다.

### 💻 구현

```javascript
const bubbleSort = (array) => {
  const length = array.length;
  let i, j, temp;
  for (i = 0; i < length - 1; i++) {
    // 0번째 인덱스부터 끝까지 순차적으로 탐색
    for (j = 0; j < length - 1 - i; j++) {
      // 다음 요소와 비교하기 위한 탐색
      // length에서 1은 마지막 요소를 빼기 위함
      // i는 각 탐색이 끝날 때마다 마지막 데이터가 정렬되었으니 빼기 위함
      if (array[j] > array[j + 1]) {
        // 두 수를 비교하여 앞 수가 뒷 수보다 크면
        temp = array[j]; // 두 수를 서로 바꿔준다
        array[j] = array[j + 1];
        array[j + 1] = temp;
      }
    }
  }
  return array;
};

let arr = [9, 7, 8, 10, 5, 1, 3, 4, 2, 6];
console.log(arr);
const newArr = bubbleSort(arr);
console.log(newArr);
```

## 2️⃣ Insertion Sort

![Insertion_sort_animation](https://user-images.githubusercontent.com/44965706/216215780-471283fc-2690-405e-b129-e1b59bbc77e6.gif)

1. 왼쪽에서 오른쪽으로 포커스를 이동한다.
2. 각 요소를 왼쪽의 요소들과 비교한다.
3. 알맞은 자리에 삽입하여 정렬한다.

**삽입정렬은, 항상 왼쪽의 요소들이 정렬되어있다는 가정하에 실행된다.**

### 👍 Best Case

- 모든 값이 정렬된 경우
- 시간 복잡도는 **O(n)**

### 👎 Worst Case

- 모든 값이 역정렬 되어있는 경우
- 시간 복잡도는 **O(n^2)**

### ✅ 장점

- `Bubble Sort`와 동일하다.

### ✅ 단점

- `Bubble Sort`와 동일하다.

### ✅ Stable

- `Bubble Sort`와 동일하다.

### 💻 구현

```javascript
const insertionSort = (array) => {
  const length = array.length;
  let i;
  for (i = 1; i < length; i++) {
    let cur = array[i];
    let left = i - 1;

    while (left >= 0 && array[left] > cur) {
      array[left + 1] = array[left];
      left--;
    }
    array[left + 1] = cur;
  }
  return array;
};
console.log(insertionSort(arr));
```

## 3️⃣ Selection Sort

![220px-Selection_sort_animation](https://user-images.githubusercontent.com/44965706/216218977-de60d7f7-b0f7-44cf-b35e-d2333ed9de2d.gif)

1. 리스트의 요소들 중 최소값을 찾는다.
2. 최소값을 리스트의 첫 번째 값과 변경한다.
3. 첫 번째 값을 제외하고 다시 순회하며 최소값을 찾는다.
4. 반복한다.

**즉, n번째 정렬이 끝나면 - 앞에서부터 n번째 자리의 데이터가 결정된다.**

### 👍👎 Case

- 모든 값이 정렬되어있거나, 역정렬 되어있는 경우
  - 모두 **O(n^2)** 의 시간 복잡도를 갖는다.

### ✅ 장점

- `in place` 알고리즘으로, 메모리가 절약된다.
- 알고리즘이 직관적이고, 구현이 쉽다.
- 실제로 교환되는 회수가 적은편이기 때문에, 많은 교환이 일어나야하는 자료 상태에서 효율적이다.

### ✅ 단점

- 시간 복잡도가 **O(n^2)** 이다.
  - 성능이 매우 떨어진다.
  - 비효율적인 정렬 방식이다.

### ✅ Unstable

- 데이터가 중복된 경우에도 위치가 변경될 수 있다.

### 💻 구현

```javascript
//선택정렬
const selectionSort = (array) => {
  const length = array.length;
  let i, j;
  for (i = 0; i < length; i++) {
    let minIndex = i;
    for (j = i + 1; j < array.length; j++) {
      if (array[minIndex] > array[j]) {
        minIndex = j;
      }
    }
    if (minIndex !== i) {
      let swap = array[minIndex];
      array[minIndex] = array[i];
      array[i] = swap;
    }
  }
  return array;
};
console.log(selectionSort(arr));
```

# Reference

- [Bubble Sort - Wikipedia](https://en.wikipedia.org/wiki/Bubble_sort)
- [Insertion Sort - Wikipedia](https://ko.wikipedia.org/wiki/%ED%8C%8C%EC%9D%BC:Insertion_sort_animation.gif)
- [[JS/Sorting] 버블 정렬, 삽입 정렬, 선택 정렬 자바스크립트로 구현하기 (Bubble Sort, Insertion Sort, Selection Sort in JavaScript)](https://im-developer.tistory.com/133)
