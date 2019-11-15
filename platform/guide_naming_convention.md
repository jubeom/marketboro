# Naming Convention 정리
식별자의 이름을 지을 때 지켜야 할 규칙에 대해 정리하려고 합니다.

## 카멜 표기법(Camel Case : 낙타 표기법)
두단어 이상의 변수명을 표현할 때, 두번째 단어부터 첫 글자를 대문자로 표기하는 방법
 
`marketBoro`, `camelCase`, `myCompany` 

## Package
lowercase 사용  

`com.marketboro.gred.admin.goods`

 
## Class
단수로 생성  
  ```java
public class GoodsController {}
public class StudentService {}
public class BookRepository {}
public class GoodsModel {}
public class GlobalExceptionHandler {}
  ```

## Method
* 조회
  * controller, service 에서 사용
    ```java
    public List<GoodsModel> getGoodsList()
    public List<StudentModel> getStudentList()
    public Book getBookName()
    ```
  * repository 조회시 사용
       ```java
        public List<GoodsModel> findGoods()
        public List<StudentModel> findStudent()
        public Book findOneBookName()
       ```

## Variable
```java
private Integer studentId;
private String studentName;
private Integer count;
```

## Comment
```java
**
* Created by hayun.lee@marketboro.com on 2019-11-15.
*/
```