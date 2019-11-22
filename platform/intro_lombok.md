## Lombok

[Lombok](https://projectlombok.org/)은 자바 애플리케이션을 컴파일 할 때 해당하는 코드를 생성해주는 라이브러리입니다.  
반복되는 코드를 줄여 개발의 편의성을 제공합니다. :rocket:

### 사용법

1. Lombok 플러그인을 설치합니다.
![image](https://user-images.githubusercontent.com/20104232/68910915-c03e0400-0796-11ea-8b84-48701488b7b5.png)
2. Build, Excution, Deployment > Compiler > Annotation Processors > Enable annotation processing :white_check_mark:
![image](https://user-images.githubusercontent.com/20104232/68911059-275bb880-0797-11ea-9d3d-2ad66202bf83.png)
3. `build.gradle`에 의존성을 추가합니다.
``` gradle
dependencies {
    compileOnly 'org.projectlombok:lombok'
    annotationProcessor 'org.projectlombok:lombok'
}
```


### 어노테이션

Lombok이 제공하는 유용한 어노테이션 목록입니다. :thumbsup:

* [생성자](https://projectlombok.org/features/constructor)
  * `@NoArgsConstructor`
    * 매개변수가 없는 생성자를 만듭니다.
    ``` java
    class MyClass {

        private final int a;
        private int b;
        private int c;

        public MyClass() {
        }
    }
    ```
  * `@RequiredArgsConstructor`
    * `final` 키워드가 붙은 멤버변수를 매개변수로 하는 생성자를 만듭니다.
    ``` java
    class MyClass {

        private final int a;
        private int b;
        private int c;

        public MyClass(int a) {
            this.a = a;
        }
    }
    ```
  * `@AllArgsConstructor`
    * 모든 멤버변수를 매개변수로 하는 생성자를 만듭니다.
    ``` java
    class MyClass {

        private final int a;
        private int b;
        private int c;

        public MyClass(int a, int b, int c) {
            this.a = a;
            this.b = b;
            this.c = c;
        }
    }
    ```
* [`@Builder`](https://projectlombok.org/features/Builder)
  * 클래스나 생성자 메소드에 사용해 객체의 생성을 유연하게 할 수 있습니다.
  * `@Builder.Default` 를 이용해 기본값을 지정할 수 있습니다.
  ``` java
  MyClass myClass = MyClass.builder()
    .a(20)
    .b(30)
    .build;
  ```
* [`@Getter` / `@Setter`](https://projectlombok.org/features/GetterSetter)
  * 멤버 변수의 get, set 메소드를 생성합니다.
  ``` java
  // lombok
  @Getter
  @Setter
  private int a = 10;

  // vanilla
  public int getA() { return a; }
  public void setA(int a) { this.a = a; }
  ```
* [`@ToString`](https://projectlombok.org/features/ToString)
  * toString 메소드를 생성합니다.
  * `@ToString.Exclude` 를 이용해 제외될 필드를 지정할 수 있습니다.
  ``` java
  @ToString
  class MyClass {

      private final int a = 10;
      private int b = 20;
      private c = 30;
  }

  myClass.toString(); // MyClass(a=10, b=20, c=30)
  ```
* [`@EqualsAndHashCode`](https://projectlombok.org/features/EqualsAndHashCode)
  * equals와 hashCode 메소드를 생성합니다.
  * 비교에 사용하기 위해 `EqualsAndHashCode.Include`와 `EqualsAndHashCode.Exclude`를 사용할 수 있습니다.
* [`@Data`](https://projectlombok.org/features/Data)
  * `@Getter`, `@Setter`, `@RequiredArgsConstructor`, `@ToString`, `@EqualsAndHashCode`, `@Value` 를 한번에 사용할 수 있습니다.
* [`@Value`](https://projectlombok.org/features/Value)
  * 멤버변수에 `private final` 키워드를 더하고 `@Data` 어노테이션과 같은 역할을 합니다. (setter 생성 :x:)
  * `@NonFinal` 어노테이션으로 final 변수가 되지않도록 하고, [`@With`](#With) 어노테이션으로 액세스 레벨을 지정할 수 있습니다.
* <a name="With">[`@With`](https://projectlombok.org/features/With)</a>
  * 필드의 값과 같으면 현재 상태의 객체를, 다르면 새로운 객체를 생성해 응답합니다.
* [`@CleanUp`](https://projectlombok.org/features/Cleanup)
  * 리소스를 사용 후(finally) `close()` 메소드를 호출합니다.
  * stream을 사용할 때 유용합니다.
* [`@NonNull`](https://projectlombok.org/features/NonNull)
  * 메소드 파라미터의 null을 체크하고 null인 경우 `NullPointerException` 을 발생시킵니다.