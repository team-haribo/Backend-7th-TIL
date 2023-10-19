# MVC

MVC(model-view-controller)는 애플리케이션을 세 가지 역할로 구분한 개발 방법론이다. 

아래 그림과 같이 Controller를 사용자가 조작하면 Controller는 Model을 통해 데이터를 가져오고 그 데이터를 바탕으로 View를 통해 사용자에게 보여지게 된다.

<img src ='https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbDpdks%2FbtrjV9EuRJ3%2FegwkkBELr5i0oYOv4t9Qy1%2Fimg.png'>

이러한 개념을 웹에 적용하면

1. 사용자가 웹사이트에 접속한다.
2. Controller는 사용자가 요청한 웹페이지를 서비스하기 위해 모델을 호출한다.
3. Model은 데이터베이스나 파일과 같은 데이터 소스를 제어한 후 그 결과를 return 한다.
4. Controller는 Model이 리턴한 결과를 View에 반영한다.
5. 데이터가 반영된 view는 사용자에게 보여진다.

## 모델 (Model)

* Data, 정보들의 가공을 책임지는 컴포넌트를 의미한다.

* 에플리케이션의 정보, 데이터를 나타낸다. 데이터베이스, 처음의 정의하는 상수, 초기화 값, 변수 등을 뜻한다.

* 비즈니스 로직을 처리한 후 모델의 변경사항을 컨트롤러와 뷰에 전달한다.

#### 👉 규칙

* 사용자가 편집하길 원하는 모든 데이터를 알고 있어야 한다.

* 뷰나 컨트롤러에 대해서는 어떠한 정보도 알지 말아야 한다.

* 변경이 일어나면, 변경 통지에 대한 처리 방법을 구현해야만 한다.

## 뷰(View)

* 사용자에게 보여지는 부분, 유저 인터페이스(User interface)를 의미한다.

* MVC 패턴에서는 여러 개의 뷰가 존재할 수 있으며, 모델에게 질의하여 데이터를 전달받는다.

* 뷰는 받은 데이터를 화면에 표시해주는 역할을 가지고 있으며, 모델에게 전달받은 데이터를 별도로 저장하지 않아야 한다. 

* 사용자가 화면에 표시된 내용을 변경하면 모델에게 전달하여 모델을 변경해야 한다.

#### 👉 규칙 

* 모델이 가지고 있는 정보를 따로 저장해서는 안된다.

* 모델이나 컨트롤러와 같이 다른 구성요소들을 몰라야 된다.

* 변경이 일어나면 변경통지에 대한 처리방법을 구현해야만 한다.

## 컨트롤러 (Controller)

* 모델과 뷰 사이를 이어주는 브릿지 역할을 의미한다.

* 모델이나 뷰는 서로의 존재를 모르기 때문에, 변경 사항을 외부로 알리고 수신하는 방법만 있다.

    * 컨트롤러는 이를 중재하기 위해 모델과 뷰에 대해 알고 있어야 한다. 모델이나 뷰 로부터 변경 내용을 통지 받으면 이를 각 구성요소에게 통지해야 한다.

* 사용자가 어플리케이션을 조작하여 발생하는 변경 이벤트들을 처리하는 역할을 수행한다.

#### 👉 규칙

* 모델이나 뷰에 대해서 알고 있어야 한다.

* 모델이나 뷰의 변경을 모니터링 해야한다.

## Spring MVC

Spring MVC의 주요 구성요소는 Model, View, Controller지만, 이들이 유기적으로 동작하기 위해 아래와 같은 다양한 구성요소가 함께한다.

* DispatcherServlet(Front Controller)

* Handler(Controller)

* ModelAndView

* ViewResolver

<img src ='https://blog.kakaocdn.net/dn/bBqbyV/btrsysIeeyv/WP43RUhxvA9rQVmBfUQZHK/img.png'>

### DispatcherServlet

* Spring MVC에서 HTTP Request가 왔을 때 DispatcherServlet이라 불리는 서블릿이 HTTP Request를 처리할 Controller를 지정한다.

    * 서블렛이란?   클라이언트의 요청을 처리하고, 그 결과를 반환하는 Servlet 클래스의 구현 규칙을 지킨 자바 웹 프로그래밍 기술이다.

* DispatcherServlet은 HTTP Request를 처리할 Controller를 적절히 분배하는 Controller이다.

    * 이와 같이 앞쪽에서 처리하는 컨트롤러를 두는 패턴을 Front Controller 패턴이라고 한다.

### Controller(Handler)

* DispatcherServlet에 의해 배정된 Controller는 HTTP Request를 처리하고, HTTP Request의 메세지를 처리해 필요한 데이터를 뽑아 Model에 저장한다.

* 또한 HTTP Request에 따라서 HTTP가 보여줄 View Name을 지정한다. 이곳에서 View Name 뿐만 아니라 직접 View를 반환할 수도 있다.

#### annotation

* Spring Controller에서 사용하는 어노테이션으로는 @RequestMapping, @RequestParam, @RequestBody 등이 있다.

* @RequestMapping은 특정 URI로 요청이 올 때 어떤 메소드로 처리할지 매핑해주는 어노테이션이다. 옵션에 따라 주소를 정하거나 매핑의 방식을 정할 수 있다.

    * @RequestMapping중에서도 GET방식으로 구체화된 @GetMapping, POST방식으로 구체화된 @PostMapping이 있다.

* @RequestParam은 클라이언트가 요청한 URL이 파라미터 값과 이름이 함꼐 전달할 때 쿼리스트링에서 파라미터 값을 가져오는 어노테이션이다.

* @RequestBody는 포스트맨이나 프로그램에서 Post방식이나 Put방식으로 객체를 전송할 때 그것을 받아오기 위해 사용할 수 있는 어노테이션이다.

### ModelAndView

* Controller에 의해 반환된 Model과 View가 Wrapping된 객체이다.

* Model은 Map자료구조로, HTTP Request 속의 데이터를 파싱하여 Key-Value 쌍으로 만들어 저장한다. 이 Model은 이후에 View를 그리기 위해 사용된다.

```java 
public ModelAndView(String viewName, @Nullable Map<String, ?> model){
    this.view = viewName;
    if(model!=null){
        getModelMap().addAllAttributes(model);
    }
}
```

* ModelAndView 내부에는 View 혹은 View Name이 있는데, View가 지정되더라도 데이터가 세팅된 View가 지정되지 않는다.

### ViewResolver

* ModelAndView를 처리하여 View를 그린다. View는 사용자에게 보여줄 완성된 View 이며, 여기서 그려지는 View가 그대로 유저에게 반환된다.

    * 우리가 특정한 url로 들어갔을 때 우리에게 보여지는 View가 바로 ViewResolver에서 만들어지는 View이다.

### 예외 처리

#### @ExceptionHandler

* 컨트롤러에서 예외가 발생했을 때, 예외를 처리하는 메소드를 지정하는 어노테이션이다.

* 보통 예외 처리는 try-catch 블록 안에서 하게되지만, 컨트롤러에서 예외가 발생한 경우에 별도로 @ExceptionHandler를 사용해 예외 처리 메소드를 정의해야 한다.

* 예시로 사용자가 로그인을 시도할 때 인증 오류가 발생하였다면, 서버는 인증 오류에 대한 예외를 return 할 것이고, @ExceptionHandler를 사용하여 예외처리 메소드를 지정해주면, 서버 인증 오류에 대한 예외가 발생한 경우에 서버는 정의된 메소드를 호출하여 예외를 처리할 수 있다.

* 결과적으로 **불필요한 중복 코드를 피하고, 간결하고 유지보수가 가능한 코드**를 만들 수 있다.

## Spring MVC의 장점

* 여러 개발자가 역할을 나누어 모델, 컨트롤러, 뷰를 동시에 개발할 수 있다. 이를 통해 개발시간 단축과 역할분리가 가능하다.

* 중복코드를 없앨 수 있고, 확장성과 유연성이 뛰어나다. 만약 Java코드로 로직을 설계한 것이 웹, 앱으로 배포된다면, View 부분만 바꿀 수 있다.

* 각 컴포넌트 별로 나누어져 있기 때문에 유지보수에 용이하다.