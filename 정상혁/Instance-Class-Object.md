## Instance-Class-Object

### 객체(Object)

* 객체는 물리적으로 존재하거나 추상적으로 생각할 수 있는 것 중에서 자신의 속성을 가지고 있고 다른 것과 식별 가능한 것을 말한다.

    * 물리적으로는 존재하는 자동차, 컴퓨터, 사람과 추상적으로 존재하는 강의, 주문 등이 모두 객체가 될 수 있다.

    * 사람이라는 객체는 이름, 나이, 성별 등과 같은 속성과 먹다, 걷다, 자다 등의 동작을 가진다. Java에서는 이러한 속성들을 필드(field), 동작들을 메소드(method)라고 부른다.

### 클래스(Class)

* 클래스란 Java에서 객체를 생성하기 위한 일종의 설계도이다. 클래스는 객체가 자기는 속성(필드)과 동작(메소드)로 이루어져 있다.

* 흔히 붕어빵(객체)를 만들기 위한 붕어빵 틀(클래스)이라고 비유를 한다. 클래스는 필드(filed), 생성자(Constructor), 메소드(Method)로 구성되어 있다. 이들은 생략될 수도 있고 하나 이상 작성될 수도 있다.

    * 필드는 객체의 데이터가 저장되는 곳이다.

    * 생성자는 객체가 실제로 생성될 때 초기화 역할을 담당한다.

    * 메소드는 객체의 동작에 해당하는 실행 블록이다.

* 사람이라는 객체를 클래스로 나타내면 아래와 같다.

```java
public class Person{
    //필드(field)
    String name;
    int age;
    char gender;
    
    //생성자(Constructor)
    Person(String name, int age, char gender){
        this.name = name;
        this.age = age;
        this.gender = gender;
    }
    
    //메소드(method)
    void eat(){
        System.out.println("냠냠");
    }
    
    void walk(){
        System.out.println("뚜벅뚜벅");
    }
    
    void sleep(){
        System.out.println("Zzz...");
    }
}
```

### 인스턴스(Instance)

* 클래스라는 붕어빵 틀에 의해 생성된 객체(붕어빵) 하나하나를 해당 클래스의 인스턴스(Instance)라고 부른다. Java 실행 시 클래스는 JVM 메모리의 클래스 영역에 로드되고 이 클래스를 사용하여 새로운 인스턴스를 생성할 수 있다.

* 즉, 인스턴스란 현실의 객체를 소프트웨어 내에서 구현한 실체라 볼 수 있다. 생성된 인스턴스들은 각자 고유의 특성을 가지고 독립적으로 존재한다.

* 아래는 인스턴스 예제 코드이다.

```java
public class PersonTest{
    public static void main(String[] args){
        // 객체 생성 = 인스턴스
        Person p1 = new Person("정상혁", "17", "M"); 
        Person p2 = new Person("방가온", "17", "F");
        
        // 메소드 사용
        p1.eat();
        p1.walk();
        p1.sleep();
        
        p2.eat();
        p2.walk();
        p2.sleep();
    }
}
```