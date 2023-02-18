# 프록시 패턴 (Proxy pattern)

소프트웨어 디자인 패턴 중 하나인 프록시 패턴에 대해 알아본다.



## 프록시 패턴이란?

어떤 객체를 사용하고자 할 때, 해당 객체를 직접적으로 참조하는 것이 아닌, 
**해당 객체를 대리하는 프록시 객체**를 통해 접근하는 방식이다.

> 일반적으로 프록시는 다른 무언가와 이어지는 인터페이스 역할을 한다.
>

![image](https://user-images.githubusercontent.com/70627979/213902347-0f5aefb3-3d54-4e70-9504-ad7a69d9f394.png)

<br>

## 필요한 이유

프록시 패턴을 사용하면 구현 클래스(or 객체)에 직접 접근하지 않고, 프록시를 통해 우회하여 접근할 수 있다. 즉, **흐름제어**가 가능해진다.

흐름제어가 가능해지면서 실제 메소드가 호출되기 이전에 필요한 기능을 구현 객체 변경없이 추가할 수 있게 된다.

예를 들어, 아래 이미지와 같이 방대한 양의 시스템 자원을 소비하는 거대한 객체가 있다고 가정해보자.
이런 경우 디비 쿼리들이 매우 느려질 수 있다.

![image](https://user-images.githubusercontent.com/70627979/213903304-cc84dbfd-61bb-4d43-afd2-97e33c372be5.png)

[이미지 출처](https://refactoring.guru/design-patterns/proxy)

<br>

문제를 해결하기 위해 지연 초기화를 위한 코드를 추가해야 하는데, 이를 모든 클래스마다 추가해주면 많은 코드 중복이 발생하게 된다.

그래서 지연 초기화 코드를 각 클래스(객체)에 넣는 방법이 아닌, 프록시 클래스(객체)에 넣는 방식을 선택하여 프록시에게 지연 초기화 및 캐싱 등의 역할을 위임할 수 있다.

![image](https://user-images.githubusercontent.com/70627979/213903309-81f1c001-1579-482f-8583-623d35e6c9f7.png)

<br>

> 흐름제어만 할 뿐 결과값을 조작하거나 변경시키면 안된다.

<br>

## 장단점

### 장점

- 클라이언트가 알지 못하는 상태에서 서비스 객체를 제어할 수 있다.
- 클라이언트가 신경 쓰지 않을 때, 서비스 객체의 수명 주기를 관리할 수 있다.
- 프록시는 서비스 객체가 준비되지 않거나 사용할 수 없을 때도 동작한다.
- 서비스나 클라이언트를 변경하지 않고 새 프록시를 도입할 수 있다. (*Open/Closed Principle*)

<br>

### 단점

- 프록시 클래스(객체)를 작성해야 하므로 코드가 복잡해질 수 있다.
- 서비스의 응답이 늦어질 수 있다.

<br>

## 예제

### Java

```java
import java.util.*;

interface Image {
    public void displayImage();
}

//on System A
class RealImage implements Image {
    private String filename;
    public RealImage(String filename) {
        this.filename = filename;
        loadImageFromDisk();
    }

    private void loadImageFromDisk() {
        System.out.println("Loading   " + filename);
    }

    @Override
    public void displayImage() {
        System.out.println("Displaying " + filename);
    }
}

//on System B
class ProxyImage implements Image {
    private String filename;
    private Image image;

    public ProxyImage(String filename) {
        this.filename = filename;
    }

    @Override
    public void displayImage() {
        if (image == null)
           image = new RealImage(filename);

        image.displayImage();
    }
}

class ProxyExample {
    public static void main(String[] args) {
        Image image1 = new ProxyImage("HiRes_10MB_Photo1");
        Image image2 = new ProxyImage("HiRes_10MB_Photo2");

        image1.displayImage(); // loading necessary
        image2.displayImage(); // loading necessary
    }
}
```

```
// 출력
Loading    HiRes_10MB_Photo1
Displaying HiRes_10MB_Photo1
Loading    HiRes_10MB_Photo2
Displaying HiRes_10MB_Photo2
```

<br>

### Javascript

자바스크립트에서는 [Proxy](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy) 생성자와 [Reflect](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Reflect) 빌트인 객체를 사용하여 Proxy 객체를 만들 수 있다.

```js
const person = {
  name: "John Doe",
  age: 42,
  nationality: "American"
};

const personProxy = new Proxy(person, {
  get: (obj, prop) => {
    console.log(`The value of ${prop} is ${Reflect.get(obj, prop)}`)
  },
  set: (obj, prop, value) => {
    console.log(`Changed ${prop} from ${obj[prop]} to ${value}`)
    Reflect.set(obj, prop, value)
  },
})

personProxy.name;
personProxy.age = 43;
personProxy.name = "Jane Doe";
```

```
// 출력
The value of name is John Doe 
Changed age from 42 to 43 
Changed name from John Doe to Jane Doe 
```

<br>

## 참고 자료

- https://ko.wikipedia.org/wiki/%ED%94%84%EB%A1%9D%EC%8B%9C_%ED%8C%A8%ED%84%B4
- https://www.patterns.dev/posts/proxy-pattern/
- https://refactoring.guru/design-patterns/proxy