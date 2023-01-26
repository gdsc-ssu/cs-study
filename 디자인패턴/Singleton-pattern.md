# 싱글톤 패턴(Singleton pattern)
## ✅ 싱글톤 패턴이란?
싱글톤 패턴은 애플리케이션이 시작될 때 어떤 클래스가 **최초 한번만 메모리를 할당(static)하고**,     
이후로는 해당 메모리에 인스턴스를 만들어 사용하는 디자인 패턴이다.    
즉 **하나의 인스턴스만 생성**하여 인스턴스가 필요할 때,     
똑같은 인스턴스를 만드는 것이 아닌 **기존의 인스턴스를 활용**하는 방법이다.    

## ✅ 싱글톤 패턴의 필요성
인스턴스를 여러 개 생성하였을 때 자원을 낭비하게 되거나, 버그를 발생시키는 상황을 미연에 방지하고자 등장한 디자인 패턴이다.    
그 해결책으로 오직 하나의 인스턴스만을 생성하고 사용하도록 하는 것이 싱글톤 패턴의 목적이다.    

- 싱글톤 패턴을 많이 사용하는 경우 : **공통된 객체를 여러개 생성해 사용하는 상황**
    - 커넥션 풀
    - 스레드 풀
    - 캐시
    - 로그 기록 객체
    - 디바이스 설정 객체
    - 인스턴스가 절대적으로 한 개만 존재하는 것을 보증하고자 할 때
    - 안드로이드 앱 : 각 액티비티, 클래스마다 주요 클래스를 하나하나 전달하는 것의 번거로움을 해소하고자 싱글톤 클래스 생성    
    → 어디서든 접근하기 쉽도록 설계

## ✅ 싱글톤 패턴 맛보기
- java 코드로 싱글톤 패턴 이해하기
```java
public class Singleton {

    private static Singleton instance = new Singleton();
    
    private Singleton() {
        // 생성자는 외부에서 호출하지 못하도록 private 으로 지정해야 한다.
    }

    public static Singleton getInstance() {
        return instance;
    }

    public void say() {
        System.out.println("hi, there");
    }
}
```

- javascript 코드로 싱글톤 패턴 이해하기
```js
var singleton = (function() {
  var instance;
  var a = 'hello';
  function initiate() {
    return {
      a: a,
      b: function() {
        alert(a);
      }
    };
  }
  return {
    getInstance: function() {
      if (!instance) {
        instance = initiate();
      }
      return instance;
    }
  }
})();
var first = singleton.getInstance();
var second = singleton.getInstance();
console.log(first === second); // true;
```

## ✅ 싱글톤 패턴의 장점
1. **메모리 측면**에서의 이점    
2. **데이터 공유** 측면에서의 이점    

### ▶️ 메모리 측면에서의 이점
OOP의 경우 객체 생성 시마다 메모리 영역을 할당받아야 한다.    
최초 한 번의 `new` 연산자를 통해 객체를 생성할 경우 **고정된 메모리 영역**를 사용하기에,    
추후 해당 객체로의 접근 시 **메모리 낭비를 방지**할 수 있다.    

### ▶️ 데이터 공유 측면에서의 이점
싱글톤 인스턴스는 **전역으로 사용되는 인스턴스**이므로 다른 클래스의 인스턴스가 접근해 사용할 수 있다.    
이 때 동시에 싱글톤 인스턴스에 접근하여 동시성 문제가 발생할 수 있으므로 유의해야 한다.    
[인스턴스의 동시성 문제 - 동시성 이슈](https://techvu.dev/143)    

## ✅ 싱글톤 패턴의 단점
1. **많은 코드의 작성** 필요        
2. **테스트**의 어려움    
3. **클라이언트가 구체 클래스에 의존**하는 문제    
4. **자식 클래스**를 만들 수 없음    
5. **내부 상태 변경**의 어려움    

### ▶️ 많은 코드의 작성 필요
싱글톤 패턴 구현을 위해 작성해야 할 코드 자체가 많이 필요하다.    
정적 팩토리 메서드에서 객체 생성 확인 및 생성자 호출의 경우 멀티 스레딩 환경에서 발생할 수 있는 동시성 문제 해결을 위해 `synchronized` 키워드를 사용해야 한다.    

### ▶️ 테스트의 어려움
싱글톤 인스턴스들은 자원을 공유하고 있다.    
테스트가 격리된 환경에서 수행되기 위해 **매번 인스턴스의 상태를 초기화**시켜주어야 한다.    

### ▶️ 클라이언트가 구체 클래스에 의존하는 문제
`new`키워드를 직접 사용해 클래스 내에서 객체를 생성하는 싱글톤 패턴은 SOLID원칙 중 DIP를 위반하며 OCP 원칙을 위반할 가능성이 높다.    
[객체지향 개발의 5대 원리 : SOLID 원칙](https://www.nextree.co.kr/p6960/)    

## 📌 참고 자료
- https://gyoogle.dev/blog/design-pattern/Singleton%20Pattern.html
- https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/DesignPattern#singleton
- https://tecoble.techcourse.co.kr/post/2020-11-07-singleton/
- https://www.zerocho.com/category/JavaScript/post/57541bef7dfff917002c4e86
- https://devmoony.tistory.com/43