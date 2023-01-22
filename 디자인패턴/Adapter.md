# 어댑터 패턴

## 📌 어댑터 패턴이란?

- 호환성이 없는 기존 클래스의 인터페이스를 변환하여 사용자가 기대하는 인터페이스 형태로 변환시키는 패턴이다.
    - 예) 전기 플러그 → 나라마다 서로 다른 플러그의 경우 어댑터를 사용하여 변환시킬 수 있다.
        
        ![Untitled](https://user-images.githubusercontent.com/85864699/213905334-f5fbaa48-53e0-445f-bdd4-829b7c206528.png)
        
- 코드의 재활용성이 증가하고 기존의 코드를 수정하지 않아도 된다는 장점이 있다.

## 📌 언제 사용할까?

- 외부 구성요소를 기존 시스템에서 재사용하고 싶지만 호환되지 않는 경우에 사용한다.
- 애플리케이션이 클라이언트가 기대하는 인터페이스와 호환되지 않는 경우에 사용한다.
- 원본 코드를 수정하지 않고 애플리케이션에서 레거시 코드를 재사용하려는 경우에 사용한다.

## 📌 어댑터 패턴의 요소

- 문제 상황 : 사용 객체의 API가 서로 다르다.
- 해결 방안 : 함수를 변환하는 객체를 중간에 넣는다.
- 결과 : 변경을 최소화 한다.
- 예시
    - 가정1 : 기존 소프트웨어 시스템에서 새로운 업체에서 제공한 클래스 라이브러리를 사용해야한다.
        
        ![Untitled](https://user-images.githubusercontent.com/85864699/213905336-d7a6d603-684b-4933-b323-aa73500a849e.png)
        
        해결방안 : 기존 코드를 바꿀 수 없다면 업체에서 사용하는 인터페이스를 기존에 사용하던 인터페이스에 적용시켜주는 클래스를 만들어 사용한다. 이 경우 어댑터는 클라이언트로부터 요청을 받아서 업체에서 제공하는 클래스에서 수용할 수 있는 형태로 변환시켜주는 중개인 역할을 한다.
        
        ![Untitled](https://user-images.githubusercontent.com/85864699/213905340-fa7bc606-5785-4904-ba1f-80892124ee38.png)
        

## 📌 [예시 1] 오리의 탈을 쓴 칠면조

### Duck interface & Mallard Duck class

```java
public interface Duck {
    public void quack();
    public void fly();
}

public class MallardDuck implements Duck {
    public void quack() {
        System.out.println("Quack");
    }
    public void fly() {
        System.out.println("I'm flying");
    }
}
```

### Turkey interface & WildTurkey class

```java
public interface Turkey {
    public void gobble();
    public void fly();
}

public class WildTurkey implements Turkey {
    public void gobble() {
        System.out.println("Gobble gobble");
    }
    public void fly() {
        System.out.println("I'm flying a short distance");
    }
}
```

**Duck 객체가 모자라서 Turkey 객체를 대신 사용해야하는 상황에서 어떻게 어댑터를 구현할 수 있을까?**

```java
public class TurkeyAdapter implements Duck {
    Turkey turkey;
    public TurkeyAdapter(Turkey turkey) {
        this.turkey = turkey;
    }
    public void quack() {
        turkey.gobble();
    }
    public void fly() {
        for (int i = 0; i < 5; i++) {
            turkey.fly();
        }
    }
}
```

아래는 TurkeyAdapter를 사용하는 모습을 도식화한 그림이다.

![Untitled](https://user-images.githubusercontent.com/85864699/213905344-843f2efa-933c-4109-a4d3-d91e7f72b3b1.png)

```java
public class DuckTestDrive {
  public static void main(String[] args) {
    MallardDuck duck = new MallardDuck();
    WildTurkey turkey = new WildTurkey();
    Duck turkeyAdapter = new TurkeyAdapter(turkey);
    
    System.out.println("The Turkey says…");
    turkey.gobble();
    turkey.fly();
    System.out.println("\nThe Duck says…");
    testDuck(duck);
    System.out.println("\nThe TurkeyAdapter says…");
    testDuck(turkeyAdapter);
  }
  static void testDuck(Duck duck) {
    duck.quack();
    duck.fly();
  }g
}
```

## 📌 [예시 2] 안드로이드에서 어댑터 패턴 (참고로만 보세요!)

- 안드로이드에서의 어댑터는 **뷰(Client)**와 **데이터 셋(Adaptee)**를 연결해주는 역할을 한다.
- 어댑터는 데이터 아이템에 접근할 수 있도록 하며, 데이터 셋 속 아이템의 뷰를 그리는 역할도 담당한다.

![Untitled](https://user-images.githubusercontent.com/85864699/213905346-43b7ac47-7a8d-4e95-8647-f2179434fa51.png)

- 예를 들어 저런 리스트 목록 화면을 만든다고 가정하면 데이터를 올리는 부분에서 뷰와 데이터를 연결해주는 다리 역할을 하는 것이 어댑터이다.
- data ← Adapter → AdapterView의 흐름으로 이루어져 있다.
- 안드로이드 코드 예시
    
    ![Untitled](https://user-images.githubusercontent.com/85864699/213905349-23e805c8-711f-4ad8-ac2f-643cdb996c76.png)
    
    ![Untitled](https://user-images.githubusercontent.com/85864699/213905353-3842de9c-2492-4e0a-9c4b-a32a54ead48d.png)
    
    - 리스트 뷰에 들어가는 아이템들을 나타내는 xml파일인  rv_item.xml
        
        ```java
        <LinearLayout
            xmlns:android="http://schemas.android.com/apk/res/android"
            android:layout_width="match_parent"
            android:layout_height="match_parent">
            
            <TextView
                android:text="rv"
                android:textSize="20sp"
                android:layout_margin="20dp"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"/>
        
        </LinearLayout>
        ```
        
    - 데이터들이 모아져 있는 List가 있는 [MainActivity.](http://MainActivity.java)kt 파일
        - 여기서는 데이터 관리 뿐만 아니라 리사이클러뷰(리스트뷰라고 생각하면 됩니다)와 어댑터를 연결한다.
        
        ```java
        class MainActivity : AppCompatActivity() {
            override fun onCreate(savedInstanceState: Bundle?) {
                super.onCreate(savedInstanceState)
                setContentView(R.layout.activity_main)
        
                val items=mutableListOf<String>()
                items.add("a")
                items.add("b")
                items.add("c")
        
                //activity_main에 있는 RecyclerView와 연결
                val rv=findViewById<RecyclerView>(R.id.rv)
                val rvAdapter=RVAdapter(items)
                rv.adapter=rvAdapter
        
                rv.layoutManager=LinearLayoutManager(this)
            }
        }
        ```
        
    - 아이템들이 들어있는 rv_item.xml과 MainActivity의 list안에 있는 데이터들을 연결해주는 RVAdapter.java
        
        ```java
        class RVAdapter(val items:MutableList<String>):RecyclerView.Adapter<RVAdapter.ViewHolder>(){
        
            // 리사이클러뷰의 아이템 불러오기
            override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): RVAdapter.ViewHolder {
                val view=LayoutInflater.from(parent.context).inflate(R.layout.rv_item,parent,false)
                // 뷰 홀더에 뷰 넣어주기
                return ViewHolder(view)
            }
        
            override fun onBindViewHolder(holder: RVAdapter.ViewHolder, position: Int) {
                holder.bindItem(items[position])
            }
        
            //전체 리사이클러뷰의 개수
            override fun getItemCount(): Int {
                return items.size
            }
        
            //뷰 홀더 만들기
            inner class ViewHolder(itemView: View) :RecyclerView.ViewHolder(itemView){
                fun bindItem(item:String){
                    //item은 onBindViewHolder에서 넘겨준 items[postion]값 즉, 리스트 안의 원소들 (a,b,c)
                    val rv_text=itemView.findViewById<TextView>(R.id.rvItem)
                    rv_text.text=item
                }
            }
        
        }
        ```
        

## 참고 자료

[https://dev-cini.tistory.com/27](https://dev-cini.tistory.com/27)

[https://wellsw.tistory.com/240](https://wellsw.tistory.com/240)

[https://codingsmu.tistory.com/59](https://codingsmu.tistory.com/59)

[https://velog.io/@haero_kim/우리는-이미-어댑터-패턴을-알고-있다](https://velog.io/@haero_kim/%EC%9A%B0%EB%A6%AC%EB%8A%94-%EC%9D%B4%EB%AF%B8-%EC%96%B4%EB%8C%91%ED%84%B0-%ED%8C%A8%ED%84%B4%EC%9D%84-%EC%95%8C%EA%B3%A0-%EC%9E%88%EB%8B%A4)

헤드퍼스트 디자인 패턴
