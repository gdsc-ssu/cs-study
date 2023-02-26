# 컴퓨터구조

<details>
<summary><strong>💡 폰 노이만 아키텍처 vs 하버드 아키텍처</strong></summary>
폰 노이만 아키텍처와 하버드 아키텍처는 컴퓨터 구조의 한 종류이다.
  <ul>
    <li>
      폰 노이만 아키텍처
      <ul>
        <li>존 폰 노이만이 제안한 구조로, 프로그램 내장 방식이라고도 부른다. </li>
        <li>메모리 안에 명령어(프로그램) 영역과 데이터 영역이 혼재되어 있는 형태이다.</li>
        <li>이전에는 컴퓨터의 하드웨어를 재배치해야만 소프트웨어를 교체할 수 있었지만, 폰 노이만 아키텍처를 도입함으로써 컴퓨터 프로그램 범용성이 크게 향상되었다.</li>
        <li>CPU가 명령어와 데이터에 동시 접근할 수 없고, 메모리의 값을 읽고 쓰는 구조이기 때문에 병목 현상이 생길 수 밖에 없다. </li>
      </ul>
    </li>
    <li>
    	하버드 아키텍처
      <ul>
        <li>폰 노이만 구조의 문제점을 극복하기 위해 명령어 메모리와 데이터 메모리가 분리되어 병렬적으로 작업이 처리되도록 구현한 구조이다. </li>
        <li>명령을 읽는 작업과 데이터를 읽는 작업을 동시에 할 수 있어 속도가 더 빠르다. </li>
        <li>회로 구조가 복잡하고 메모리가 공간을 많이 차지하게 된다. </li>
      </ul>
    </li>
    <li>현대 컴퓨터는 CPU 외부적으로는 폰 노이만 구조를, 내부는 하버드 구조를 적용하는 하이브리드 구조를 도입하여 속도를 향상시켰다. </li>
  </ul>
  <img src="https://user-images.githubusercontent.com/70627979/221409501-f9fb52b9-d127-4723-ac05-5be69d9cf7be.png" alt="image" style="zoom:50%;" />
</details>

<details>
<summary><strong>💡 CISC vs RISC</strong></summary>
  <ul>
    <li>
      CISC(Complex Instruction Set Computer)
      <ul>
        <li>연산을 처리하는 복잡한 명령어들을 수백개 이상 탑재하고 있는 프로세서이다. </li>
        <li>명령어마다 실행하는 시간이 다르다.</li>
        <li>복합 명령을 가짐으로써 하위 호환성이 높지만, 전력 소모가 크고 속도가 느리며 비싸다.</li>
      </ul>
    </li>
    <li>
    	RISC(Reduced Instruction Set Computer)
      <ul>
        <li>사용 빈도가 높은 20%의 명령어를 기반으로 최소한의 명령어 세트를 구성한 프로세서이다. </li>
        <li>명령어마다 실행하는 시간이 동일하다.</li>
        <li>하드웨어가 간단한 대신 소프트웨어가 복잡하고 크기가 커졌다.</li>
        <li>호환성이 부족하지만, 전력 소모가 적고 속도가 빠르며 가격이 저렴한 편이다. </li>
      </ul>
    </li>
  </ul>
</details>

<details>
<summary><strong>💡 API, ABI, ISA란 무엇인가</strong></summary>
  <ul>
    <li>
      ISA(Intruction Set Architecture)
      <ul>
        <li>마이크로 프로세서가 인식해서 기능을 이해하고 실행할 수 있는 기계어 명령어 셋이다.</li>
        <li>C언어 등으로 작성된 프로그램이 ISA 규칙에 맞게 적절히 기계어로 번역되면CPU가 이를 읽고 해석한 후 실행한다. </li>
        <li>하나의 CPU는 하나의 ISA만 사용한다. </li>
      </ul>
    </li>
    <li>
    	ABI(Application Binary Interface)
      <ul>
        <li>특정 아키텍처에서 두 개 이상의 소프트웨어 간의 바이너리 인터페이스를 정의한다.</li>
        <li>ABI가 호환되어야 프로그램을 실행시킬 수 있다. mac 환경에서 window 응용 프로그램을 실행할 수 없는 이유가 바로 ABI가 호환되지 않기 때문이다.</li>
        <li>ex) Windows 와 Windows RT와의 관계</li>
      </ul>
    </li>
    <li>
    	API(Application Programming Interface)
      <ul>
        <li>코드 레벨에서 다른 소프트웨어와 통신하는 인터페이스를 정의한다.</li>
      </ul>
    </li>
  </ul>
</details>

<details>
<summary><strong>💡 고정 소수점과 부동 소수점</strong></summary>
  컴퓨터에서는 실수를 고정 소수점 과 부동 소수점 으로 표현한다.
  <ol>
    <li>
      고정 소수점 (Fixed Point)
      <ul>
        <li>소수점이 찍힐 위치를 미리 정해놓고 소수를 표현 (정수 + 소수)</li>
        <li>ex) 3.141592 (부호, 정수부, 소수부)</li>
        <li>장점 : 실수부를 정수부와 소수부 만으로 표현하여 비교적 단순하다.</li>
        <li>단점 : 표현의 범위가 한정적이다. (정수부 : 15bit, 소수부 : 16bit)</li>
      </ul>
      <img src="https://user-images.githubusercontent.com/70627979/221410024-d2b43e01-b843-4902-a068-b35bfca3d1cf.png" alt="image" style="zoom:70%;" />
    </li>
    <li>
    	부동 소수점(Floating Point)
      <ul>
        <li>
        	실수부를 가수부 와 지수부 로 표현한다.
          <ul>
            <li>가수부 : 실수의 실제 값 표현</li>
            <li>지수부 : 크기를 표현, 가수의 어디 쯤 소수점이 있는지 표현</li>
          </ul>
        </li>
        <li>
          지수의 값에 따라 소수점이 움직이는 방식을 활용한 실수 표현 방법이다.
          <ul>
            <li>소수점의 위치가 고정되어 있지 않는다.</li>
          </ul>
        </li>
        <li>장점 : 표현할 수 있는 수의 범위가 넓음</li>
        <li>단점 : 오차 발생의 가능성 존재</li>
      </ul>
      <img src="https://user-images.githubusercontent.com/70627979/221410074-058fb865-c8cb-498a-936b-94aff9b98cc1.png" alt="image" style="zoom:70%;" />
    </li>
  </ol>
</details>