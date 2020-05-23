# 함수를 파라미터로 전달하기

## Predicate 정의

파라미터를 받아서 **true** 나 **false** 를 반환하는 함수입니다.

형태는 **Predicate&lt;객체타입&gt;** 입니다.

## Predicate 예제

**Predicate** 인터페이스는 구현 후, 제네릭 타입에 따라 **test 함수**를 대입하여 사용합니다.

```java
public interface Predicate<T> {
    boolean test(T t);
}
```

음식의 종류에 대한 정보를 가지고 있 **Food** 클래스를 정의합니다.

```java
public class Food {
    private String type = "";
    public String getType(){
        return type;
    }
}
```

음식의 종류에 따라 필터링 해주는 **FoodUtil** 클래스를 정의합니다.

```java
public class FoodUtil {
    static List<Food> filterFoods (List<Food> refrigerator, Predicate<Food> p) {
        List<Food> filteredFoods = new ArrayList<>();
        for (Food food : refrigerator) {
            if (p.test(food)) {
                filteredFoods.add(food);
            }
        }
        return filteredFoods;
    }
}
```

### 1. 함수참조 사용하기

아래와 같이 **함수참조 ::** 을 이용하여 프레디케이트의 함수의 내용을 정의하여 사용할 수 있습니다.  
여기에서 중요한 것은 test 함수 대신 실행되는 **isFruit , isIcecream** 함수가 **boolean 을 리턴**하고, **Food 타입을 매개변수로 받는다**는 것입니다.  
**Predicate&lt;객체타입&gt; p** 에서 정의한 **객체타입과 동일한 Food**를 매개변수로 받게 되는 것입니다.

```java
public class Test {
    public static void main (String[] args) {
        List<Food> fruits = FoodUtil.filterFoods(re_home, Food::isFruit);
        List<Food> icecreams = FoodUtil.filterFoods(re_company, Food::isIcecream);
    }
    
    public static boolean isFruit(Food food){
        return "fruit".equals(food.getType());
    };
    
    public static boolean isIcecream(Food food){
        return "icecream".equals(food.getType());
    };    
}
```

### 2. 람다식 사용하기

위에서 **함수참조 ::** 를 사용하는 방법에 이어서 **람다식**을 사용하실 수도 있습니다.  
함수가 재사용을 할 필요가 없는 상황이라면 아래와 같이 **람다식**을 사용하는 방법을 추천합니다.

```java
public class Test {
    public static void main (String[] args) {
        List<Food> fruits = FoodUtil.filterFoods(
            re_home, 
            (Food food) -> "fruit".equals(food.getType())
        );
        
        List<Food> icecreams = FoodUtil.filterFoods(
            re_company, 
            (Food food) -> "icecream".equals(food.getType())
        );
    }
}
```

