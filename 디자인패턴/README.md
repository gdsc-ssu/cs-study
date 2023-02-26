# 디자인패턴

<details>
<summary><strong>💡 MVC 패턴이란</strong></summary>
    MVC(Model-View-Controller)는 데이터, 사용자 인터페이스, 논리 제어를 구현하는데 널리 사용되는 소프트웨어 디자인 패턴이다. 소프트웨어의 비즈니스 로직과 화면을 구분, 즉 "관심사 분리"에 중점을 두고 있다.
  <ul>
    <li>Model: 데이터와 비즈니스 로직 관리</li>
    <li>View: 레이아웃과 화면 처리</li>
    <li>Controller: 명령을 Model과 View로 라우팅</li>
  </ul>
  <img src="https://user-images.githubusercontent.com/70627979/221409309-01e157c8-937d-4dbb-8cef-f610fa067359.png" alt="image" style="zoom: 25%;" />
</details>

<details>
<summary><strong>💡 SOLID 원칙</strong></summary>
  <ul>
    <li>SRP(Single Responsibility Principle): 단일 책임 원칙</li>
    <li>OCP(Open Closed Priciple): 개방 폐쇄 원칙</li>
    <li>LSP(Listov Substitution Priciple): 리스코프 치환 원칙</li>
    <li>ISP(Interface Segregation Principle): 인터페이스 분리 원칙</li>
    <li>DIP(Dependency Inversion Principle): 의존 역전 원칙</li>
  </ul>
</details>

<details>
<summary><strong>💡 Singleton 패턴이란</strong></summary>
    싱글톤 패턴은 애플리케이션이 시작될 때 어떤 클래스가 <strong>최초 한번만 메모리를 할당(static)</strong>하고, 이후로는 해당 메모리에 인스턴스를 만들어 사용하는 디자인 패턴이다.<br/>
  즉, <strong>하나의 인스턴스만 생성</strong>하여 인스턴스가 필요할 때, 똑같은 인스턴스를 만드는 것이 아닌 <strong>기존의 인스턴스를 활용</strong>하는 방법이다.<br/>
  <ul>
    <li>싱글톤 패턴의 장점
    	<ol>
        <li><strong>메모리</strong> 절약</li>
        <li><strong>데이터 공유</strong> 측면에서의 이점</li>
      </ol>
    </li>
    <li>싱글톤 패턴의 단점
    	<ol>
        <li><strong>많은 코드의 작성</strong> 필요</li>
        <li><strong>테스트의</strong> 어려움</li>
        <li><strong>클라이언트가 구체 클래스에 의존</strong>하는 문제</li>
        <li><strong>자식 클래스</strong>를 만들 수 없음</li>
        <li><strong>내부 상태 변경</strong>의 어려움</li>
      </ol>
    </li>
  </ul>
</details>

<details>
<summary><strong>💡 Strategy 패턴이란</strong></summary>
  <ul>
    <li><strong>행위(Behavioral)</strong>를 클래스로 캡슐화하여 동적으로 바꿀 수 있도록 하는 패턴을 말한다.
    	<ul>
        <li>동일한 문제를 해결할 수 있는 알고리즘들이 캡슐화 되어있다.</li>
        <li>필요할 때 서로 교체할 수 있다.</li>
        <li>결국, 동일한 문제를 다른 알고리즘을 통해 해결할 수도 있게된다.</li>
      </ul>
    </li>
    <li><strong>전략(Strategy)</strong>을 쉽게 바꿀 수 있다.
    	<ul>
        <li>게임 프로그래밍에서 유용하게 사용된다.
        	<ul>
            <li>게임에서는, 캐릭터의 상황에 따라 공격이나 이동 방식이 바뀐다.</li>
            <li>이 때, <strong>Strategy 패턴</strong>이 유용하게 사용된다.</li>
          </ul>
        </li>
        <li>역할 및 작업
        	<ul>
            <li>Strategy
            	<ul>
                <li>인터페이스나 추상 클래스</li>
                <li>외부에서 동일한 방식으로 알고리즘을 호출하는 방식을 명시한다.</li>
              </ul>
            </li>
          </ul>
        </li>
        <li>ConcreteStrategy
        	<ul>
            <li>알고리즘을 실제로 구현한 클래스</li>
          </ul>
        </li>
        <li>Context
          <ul>
            <li>패턴을 이용하여 역할을 수행한다.</li>
            <li>상황에 따라, 동적으로 전략이 변경될 수 있도록 <strong>setter 메서드(집약관계)</strong>를 제공한다.</li>
          </ul>
        </li>
      </ul>
    </li>
  </ul>
</details>

<details>
<summary><strong>💡 Template Method 패턴이란</strong></summary>
  <ul>
    <li>일부를 <strong>서브 클래스</strong>로 캡슐화하여, <strong>구조의 변경 없이 특정 단계의 내역만 바꾸는 패턴</strong>을 의미한다.
    	<ul>
        <li>전체적으로는 동일하다.</li>
        <li>부분적으로는 다르다.
        	<ul>
            <li>코드 중복을 최소화할 때 유용하다.</li>
            <li>동일한 기능은 상위 클래스에, 확장 및 변화가 필요한 부분은 서브 클래스에 구현한다.</li>
            <li>전체적인 알고리즘 재사용에 유리하다.</li>
          </ul>
        </li>
      </ul>
    </li>
    <li>역할 및 작업
    	<ul>
        <li>AbstractClass
        	<ul>
            <li>템플릿 및 메서드를 정의하는 클래스</li>
            <li>하위 클래스에는 공통 알고리즘을 정의한다.</li>
            <li>하위 클래스에서 구현될 기능을 <strong>primitive 메서드</strong> <strong>hook 메서드</strong>로 정의한다.</li>
          </ul>
        </li>
        <li>ConcreteClass
        	<ul>
            <li>상속받은 <strong>primitive 메서드</strong> <strong>hook 메서드</strong>를 구현하는 클래스</li>
            <li>서브 클래스에 적합하게 메서드를 오버라이드한다.</li>
          </ul>
        </li>
      </ul>
    </li>
  </ul>
</details>