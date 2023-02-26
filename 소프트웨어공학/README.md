# 소프트웨어공학

<details>
<summary><strong>💡 객체지향프로그래밍(OOP)의 특징</strong></summary>
    객체 지향 프로그래밍은 컴퓨터 프로그래밍 패러다임 중 하나로, 프로그래밍에서 필요한 데이터를 추상화시켜 상태와 행위를 가진 객체를 만들고 그 객체들 간의 유기적인 상호작용을 통해 로직을 구성하는 프로그래밍 방법이다. <br/><br/>
<strong>객체지향 프로그래밍의 특징</strong>
  <ul>
    <li>추상화 : "공통의" 속성이나 기능을 묶어 이름을 붙이는 것
		<ul>
      <li>여기서 말하는 추상화는 추상 클래스나 추상 클래스가 갖는 추상 메서드를 의미하기보다는 클래스를 설계하는 것 자체를 의미한다.</li>				</ul>
    <li>캡슐화 : 기능과 특성의 모음을 "클래스"라는 "캡슐"에 분류해서 넣는 것</li>
    	<ul>
        <li>캡슐화의 목적 2가지
          <ol>
            <li>코드를 재수정 없이 재활용하는 것</li>
            <li>접근 제어자를 통한 정보 은닉</li>
          </ol>
        </li>
    	</ul>
    </li>
  	<li>상속 : 부모클래스의 속성과 기능을 그대로 이어받아 사용할 수 있게 하고 기능의 일부분을 변경해야 할 경우 상속 받은 자식클래스에서 해당 기능만 다시 수정(정의)하여 사용할 수 있게 하는 것</li>
  	<li>다형성 : 하나의 변수명, 함수명 등이 상황에 따라 다른 의미로 해석될 수 있다.
      <ul>
        <li>즉 오버라이딩(Overriding), 오버로딩(Overloading)이 가능하다는 이야기이다. 
          <ol>
            <li>오버라이딩 : 부모클래스의 메서드와 같은 이름, 매개변수를 재정의 하는 것</li>
            <li>오버로딩 : 같은 이름의 함수를 여러개 정의하고, 매개변수의 타입과 개수를 다르게 하여 매개변수에 따라 다르게 호출할 수 있게 하는 것</li>
          </ol>
    		</li>
      </ul>
  	</li>
  </ul>
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
<summary><strong>💡 UI와 UX</strong></summary>
  <ul>
    <li><strong>UI</strong>
      <ul>
    		<li>User Interface의 약자로 사용자가 웹이나 앱 등을 사용할 때 마주하는 디자인, 레이아웃</li>
    		<li>사용자가 사용할 때 편하게 사용할 수 있도록 만족도를 높여야 한다.</li> 
      </ul>
    </li>
    <li><strong>UX</strong>
      <ul>
    		<li>User eXercise의 약자로 사용자가 웹이나 앱 등을 사용할 때의 경험을 분석하는 것.</li>
    		<li>통계 분석 등을 통해 유저들의 특성을 알아내어 적절하게 반영해야함.</li> 
        <li>ex) A 앱은 평균 사용자의 나이가 40대 이상이니 글씨 크기를 조금 더 키워야겠다.</li>
      </ul>
    </li>
  </ul>
</details>

<details>
<summary><strong>💡 private, public, protected</strong></summary>
  <ul>
    <li>public : 모든 접근을 허용. 클래스 등 모든 외부 접근을 허용한다.</li>
    <li>private : 외부에서 접근이 불가능. 오직 클래스 내부에서만 접근할 수 있다.</li>
    <li>protected : 기본적으로 private과 같이 외부에서 접근이 불가능하지만, 상속받은 클래스의 경우에는 접근할 수 있다.</li>
  </ul>
</details>

<details>
<summary><strong>💡 프로세스란</strong></summary>
  프로세스란 소프트웨어 시스템을 구축하기 위해 수행되는 작업의 단계이다.<br/>
  프로세스는 작업 결과와 검증 조건을 명확히 정의해야 한다.<br/>
  <ul>
    <li>프로세스의 특징
    	<ul>
        <li>요구명세서, 설계문서, 코드, 프로토타입, 특정 단계를 어떻게 수행할 것인가에 대한 정의이다.</li>
				<li>단계적인 작업의 틀을 정의한 것이다.</li>
        <li>무엇을 하는가에 중점을 둔다.</li>
        <li>결과물의 표현에 대하여 언급이 없다.</li>
        <li>패러다임 독립적이어야 한다.</li>
        <li>각 단계가 다른 방법론으로도 실현 가능해야 한다.</li>
        <li>요구명세서, 설계문서, 코드, 프로토타입, 특정 단계를 어떻게 수행할 것인가에 대한 정의이다.</li>
      </ul>
    </li>
    <li>프로세스의 사례
    	<ul>
        <li>폭포수 프로세스</li>
        <li>나선형 프로세스</li>
        <li>프로토타이핑 프로세스</li>
        <li>Unified 프로세스</li>
        <li>애자일 프로세스</li>
      </ul>
    </li>
  </ul>
</details>

<details>
<summary><strong>💡 소프트웨어 방법론이란</strong></summary>
  <ul>
    <li>소프트웨어 방법론의 특징
    	<ul>
        <li>프로세스의 구체적인 구현의 이름이다.	</li>
				<li>어떻게 하는가에 중점을 둔다.</li>
        <li>결과물을 어떻게 표현하는지 표시한다.</li>
        <li>패러다임에 종속적이다.</li>
        <li>각 단계의 절차, 기술, 가이드라인을 제시한다.</li>
      </ul>
    </li>
    <li>소프트웨어 방법론의 사례
    	<ul>
        <li>구조적 분석, 설계 방법론</li>
        <li>객체지향 방법론</li>
        <li>컴포넌트</li>
        <li>애자일 방법론</li>
      </ul>
    </li>
  </ul>
</details>

<details>
<summary><strong>💡 명령형 프로그래밍 vs 선언형 프로그래밍</strong></summary>
  <ul>
    <li>명령형 프로그래밍(Imperative Programming)
    	<ul>
        <li><strong>어떻게 목적을 달성할지</strong>에 초점이 맞추어져 있고, 프로그래밍의 상태와 그것을 변경시키는 구문의 관점에서 연산을 설명하는 프로그래밍 패러다임</li>
				<li>프로그래밍에 사용된 알고리즘에 대해서는 명시되어있고 목표에 대해서는 명시되어 있지 않다. </li>
        <li>컴퓨터가 수행할 명령들을 순서대로 써내려간다.</li>
        <li>C, C++, Java 등 보통 절차형, 객체지향 언어들은 명령형 프로그래밍 언어이다.</li>
      </ul>
    </li>
    <li>선언형 프로그래밍(Declarative Programming)
    	<ul>
        <li>선언형 프로그래밍은 두 가지의 뜻으로 통용되고 있다.
        	<ol>
            <li>어떤 방법으로 해야하는지 보다는 무엇을 할지에 초점이 맞추어져있는 프로그래밍 패러디임</li>
            <li>함수형, 논리형, 제한형 프로그래밍 언어로 쓰인 경우</li>
          </ol>
        </li>
        <li>대표적인 언어로는 SQL, HTML이 있다. 예를 들어 HTML 은 무엇을 웹에 나타낼지에 대해 고민하지, 어떤 방법으로 나타낼지는 고민하지 않는다.</li>
        <li>프로그램의 목표를 명시하고 사용된 알고리즘을 명시하지는 않는다. </li>
      </ul>
    </li>
  </ul>
</details>

<details>
<summary><strong>💡 TDD(Test Driven Developement)</strong></summary>
  <ul>
    <li>TDD의 정의 
    	<ul>
        <li>TDD란 Test Driven Development의 약자로 ‘테스트 주도 개발’을 의미한다.</li>
				<li>반복 테스트를 이용한 소프트웨어 방법론으로, 작은 단위의 테스트 케이스를 작성하고 이를 통과하는 코드를 추가하는 단계를 반복하고 구현하는 것을 의미한다. </li>
        <li>짧은 개발 주기의 반복에 의존하는 개발 프로세스이고, 애자일 방법론 중 하나인 XP(eXtream Programming)의 ‘Test-First’ 개념에 기반을 두고 있다.</li>
      </ul>
    </li>
    <li>TDD의 장점
    	<ul>
        <li>높은 코드 안전성 : 짧은 주기의 테스트 코드 개발-리팩토링 단계를 거치며 끊임없이 보완하고 철저한 모듈화를 통해 종속성과 의존성이 낮은 모듈로 조합된 소프트웨어 개발을 가능하게 하여 코드의 안정성을 높일 수 있다.</li>
         <li>재설계 시간의 단축 : 설계 단계에서 테스트 시나리오를 작성하기 때문에 무엇을 만들어야하는지 정의하고 생각하는 시간을 가질 수 있어 완성도 높은 설계로 이어진다.</li>
         <li>디버깅 시간의 단축 : 자동화된 단위테스트를 통해 특정 버그를 쉽게 찾을 수 있다,</li>
      </ul>
    </li>
    <li>TDD 단점
    	<ul>
        <li>생산성 저하 : 일반적인 개발 방식보다 개발 시간이 늘어날 수 밖에 없다. </li>
      </ul>
    </li>
  </ul>
</details>

<details>
<summary><strong>💡 컴파일과 런타임</strong></summary>
  <ul>
    <li>컴파일(Compile)
    	<ul>
        <li>개발자가 프로그램을 위해 작성한 소스코드를 다른 프로그램이나 기계가 처리하기 용이한 형태로 바꾸는 과정</li>
        <li>Java, C, C++ 같은 언어들이 컴파일 언어이고, 이들은 실행(런타임)이 되기 위해서는 반드시 컴파일 과정을 거쳐야 한다. 반면 Javascript, Python 같은 스크립트 언어들은 컴파일 과정없이 기계어로 변역되는 즉시 동작하도록 되어있다.</li>
        <li>컴파일 에러 : 프로그램이 컴파일링되는 과정에서 발생하는 에러로 일반적으로 컴파일 에러 발생시 문제를 일으킨 소스코드 라인을 알 수 있다.
        	<ul>
            <li>Syntax Error, Type 체크 에러, 파일 참조 오류 등</li>
          </ul>
        </li>
      </ul>
    </li>
    <li>런타임(Runtime)
    	<ul>
        <li>컴파일 과정을 마친 컴퓨터 프로그램이 실행되고 있는 환경 또는 동작되는 동안의 시간</li>
        <li>런타임 에러 : 소스코드가 실행 가능한 프로그램으로 성공적으로 컴파일 되었으나 프로그램의 실행 중에 발생하는 형태의 오류
        	<ul>
            <li>0 나누기 오류, Null 참조 오류, 메모리 부족 오류 등</li>
          </ul>
        </li>
      </ul>
    </li>
  </ul>
</details>

<details>
<summary><strong>💡 응집도와 결합도</strong></summary>
  <ul>
    <li><strong>응집도</strong>
    	<ul>
        <li>모듈 내부가 얼마나 강한 연관성으로 이어져 있는지를 나타내는 측정치</li>
        -> 각 구성요소들이 공통의 목적을 달성하기 위해 서로 얼마나 연관되어 있는지를 나타낸다.
        <li>모듈이 하나의 임무를 수행하는 정도를 나타내는 측정치로도 활용</li>
        <li>응집도가 높을수록 좋다.</li>
      </ul>
    </li>
    <li><strong>결합도</strong>
    	<ul>
        <li>하나의 모듈과 다른 모듈들과의 연관관계를 측정한 정도</li>
        <li>결합도가 높을수록 상호연계되어 있기 때문에 모듈의 변경이 어렵다.</li>
        <li>결합도가 낮을수록 좋다.</li>
      </ul>
    </li>
  </ul>
</details>

<details>
<summary><strong>💡 컴파일언어와 인터프리터 언어</strong></summary>
  <ul>
    <li><strong>컴파일 언어</strong>
    	<ul>
        <li>컴파일러를 이용하여 사용자가 작성한 고급언어를 기계어로 바꿔 객체모듈을 만들고 이 모듈을 링크, 로드 후 실행시키는 언어</li>
        <li>고급 언어(사용자 입력) → (컴파일러를 통해) 기계어로 번역 → (링크, 로드 하며)실행</li>
        <li>장점 : 한번 컴파일 해놓으면 반복 실행 시 빠르게 실행할 수 있다.</li>
        <li>단점
        	<ul>
            <li>컴파일 하는 과정(고급언어 → 기계어)이 오래 걸린다.</li>
            <li>각 운영체제에 맞춰서 컴파일러가 다르기 때문에 범용성이 떨어진다.</li>
          </ul>
        </li>
        <li>언어 : C/C++ , Java</li>
      </ul>
    </li>
    <li><strong>인터프리터 언어</strong>
    	<ul>
        <li>컴파일러를 사용하지 않고 사용자가 작성한 고급언어를 중간과정없이 변환 후 바로 실행하는 것.</li>
        <li>고급 언어(사용자 입력) → (인터프리터를 이용해) 번역 및 실행</li>
        <li>장점
        	<ul>
        		<li>기계어로 번역을 하지 않기 때문에 실행시간이 빠르다.</li>
            <li>따로 기계어파일로 변환하지 않기 때문에 메모리를 절약한다.</li>
            <li>운영체제에 종속되지 않는다.</li>
          </ul>
        </li>
        <li>단점 : 자주 실행시켜야 할때에는 항상 실행할 때마다 번역을 해야하므로 느리다.</li>
      </ul>
    </li>
  </ul>
</details>

<details>
<summary><strong>💡 라이브러리와 프레임워크의 차이</strong></summary>
  <ul>
    <li><strong>프레임워크</strong>
    	<ul>
        <li>개발자가 보다 편하게 원하는 개발을 할 수 있게 일정한 형태나 필요한 기능을 갖춘 뼈대나 기반구조</li>
      </ul>
    </li>
    <li><strong>라이브러리</strong>
    	<ul>
        <li>단순 활용가능한 도구(모듈, 클래스 등)들의 집합.</li>
      </ul>
    </li>
    <li><strong>차이점</strong>
    	<ul>
        <li>언뜻보면 비슷해 보이지만 가장 중요한 차이는 <strong>제어의 역전(IoC, Inversion of Control)</strong>이다.</li>
        <li>프레임워크의 경우에는 <strong>사용자가 수동적</strong>으로 흐름을 따라간다.</li>
        -> 프레임워크가 짜놓은 규칙을 따라 원하는 코드를 작성한다.
        <li>라이브러리는 <strong>사용자가 능동적</strong>으로 흐름을 제어한다.</li>
        -> 개발자가 필요한 부분에 라이브러리의 도구들을 호출해서 가져온다.
      </ul>
    </li>
  </ul>
</details>

