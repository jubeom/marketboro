# Naming Convention 정리
식별자의 이름을 지을 때 지켜야 할 규칙에 대해 정리하려고 합니다.

## 카멜 표기법(Camel Case : 낙타 표기법)
두단어 이상의 변수명을 표현할 때, 두번째 단어부터 첫 글자를 대문자로 표기하는 방법
 
`marketBoro`, `camelCase`, `myCompany` 

## Package
lowercase 사용하며, 표준패턴을 따름

`com.marketboro.gred.admin.goods`

 
## Class(UpperCamel Case)
대문자로 시작하고, 명사사용
  ```java
public class GoodsController {}
public class StudentService {}
public class BookRepository {}
public class GoodsModel {}
public class GlobalExceptionHandler {}
  ```

## Method
* 입력
``` java
public void insertGoods(dto)
public void insertStudentAgeAndName(Integer age, String name)
```
* 조회(속성에 접근하는 메소드명의 접두사는 'get', 'set'을 사용)
  * controller, service 에서 사용
    ```java
    public List<GoodsModel> getGoodsList()
    public List<GoodModel> getGoodsList(Integer goodsId, Pageable pageable)
    public List<StudentModel> getStudentList()
    public Book getBookName()
    ```
  * repository 조회시 사용
       ```java
        public List<GoodsModel> findGoods()
        public List<GoodsModel> findGoods(Integer goodsId, Pageable pageable)
        public List<StudentModel> findStudent()
        public Book findOneBookName()
       ```
* 수정
```java
public void updateGoodsCategoryName(Integer goodsId, String name)
public void updateStudentName(Integer goodsId, name)
public void updateStudentAge(Integer goodsId, Integer age)
```

* 삭제
```java
public void deleteByGoodsId(Integer goodsId)
public void deleteByName(String name)
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
![image](https://user-images.githubusercontent.com/57780013/69030161-1bcbf400-0a1a-11ea-9b11-83394eb64d6e.png)
## Java
* JOOQ 테이블에 as(Alias) 사용은 경우에 따라 사용
```java
GoodsCategory goodsCategory = GoodsCategory.GOODS_CATEGORY.as("goodsCategory");
```
* JOOQ 테이블 select시, 전체컬럼 조회가 아닌 필요한 컬럼만 조회
```` java
dSLContext
.select(goodsCategory.goodsId, goodsCategory.name)
.from(goodsCategory)
````

## Test
* 컨트롤러에 대해 테스트를 기본적으로 하고, 필요시 서비스에 대한 테스트 케이스도 작성 
