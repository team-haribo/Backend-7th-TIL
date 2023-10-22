## Overriding, Overloading

### Overriding

* 부모 클래스로부터 상속받은 메소드의 내용을 재정의(변경)하는 것을 오버라이딩이라고 한다.

* 오버라이딩은 메소드를 새로 만드는게 아니고 내용을 새로 정의하는 것이다. 그래서 다음과 같은 조건을 만족해야 한다.

    1. 자식 클래스의 오버라이딩 하려는 메소드는 부모 클래스의 메소드와 시그니처(이름, 매개변수, 반환타입)이 같아야한다.

    2. 접근 제어자는 부모클래스의 메소드보다 좁은 범위로 변경할 수 없다.
        * ex) 부모클래스가 public, 자식클래스가 protected인 경우 에러가 발생한다.

    3. 부모 클래스의 메소드보다 많은 수의 예외를 선언할 수 없다.

    4. 인스턴스 메소드를 static 또는 그 반대로 변경할 수 없다.

* 아래는 오버라이딩 예시 코드이다.

```java
class Car{
    void run(){
        System.out.println("차가 달립니다..");
    }
}

class Bus extends Car{
    @Override
    void run(){
        System.out.println("버스가 달립니다..");
    }
}

public class OverridingDemo{
    public static void main(String[] args){
        Car car = new Car();
        car.run();

        Bus bus = new Bus();
        bus.run();
    }
}

//실행 결과
차가 달립니다..
버스가 달립니다..
```

* 오버라이딩을 사용하면 공통되는 메소드를 부모 클래스에서 정의하고, 자식 클래스에서 재정의 하여 중복 코드를 줄일 수 있다.

### Overloading

* 메소드 오버로딩은 같은 메소드를 중복하여 정의하는 것이다. 원래는 클래스 내에 같은 이름의 메소드를 둘 이상 가질 수 없다.

* 하지만 매개변수의 개수나 타입을 다르게 하면 하나의 이름으로 메소드를 작성할 수 있습니다. 즉, 메소드 오버로딩은 서로 다른 시그니처를 갖는 여러 메소드를 같은 이름으로 정의하는 것이다.

```java
class Cal{
    public void add(int a, int b){
        System.out.println(a+b);
    }
    
    public void add(double a, double b){
        System.out.println(a+b);
    }

    public void add(String a, String b){
        System.out.println(a+b);
    }
}
```

* 위 코드 처럼 이름이 같지만 매개변수 갯수나 타입이 다르면 동일한 이름의 메소드를 여러개 만들 수 있다.

* 메소드 오버로딩을 사용하면 메소드에 사용되는 이름을 절약할 수 있다.

* 또한 메소드를 호출할 때 전달해야 할 매개변수의 타입이나 개수에 대해 신경을 쓰지 않고 호출할 수 있다.

* 메소드 오버로딩은 객체 지향 프로그래밍의 특징 중 하나인 다형성(polymorphism)을 구현하는 방법 중 하나입니다.