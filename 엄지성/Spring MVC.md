# Spring MVC
## Spring MVC란?

* Model, View, Controller 세가지 구성요소를 사용한다.

* 클라이언트가 보내는 HTTP 요청들을 처리하고 요청을 이용해 데이터를 처리하고 View를 이용해 html과 JSP를 return하는 프레임워크이다.

## Spring MVC의 구조

> 주요 구조는 Controller, Model, View이지만 그 구성요소들을 유연하게 동작시키기 위해 다양한 것들이 존재한다.

* DispatcherServlet(Front Controller)

* Handler(Controller)

* ModelAndView

* ViewResolver

### DispatcherServlet

* HTTP 요청이 들어오면 가장 먼저 처리하는 Controller

* 클라이언트가 HTTP Request를 보내면 DispatcherServlet에 들어가 그 요청에 맞는 Controller를 지정해준다.

### Controller(Handler)

* DispatcherServlet에서 배정받은 Controller에서 HTTP Request로 받은 정보를 Model로 저장한다.

* HTTP Request를 받아서 HTTP가 보여줄 View Name을 지정하거나 바로 View를 띄울 수 있다.

* But View에 Model 데이터를 세팅하지않는다.

### ModelAndView

* 여기서 Model은 Map으로 데이터를 저장한다. HTTP Request를 분석하여 Key-value로 만들어 저장한다.

* 여기서 저장된 Model은 나중에 View를 위해 사용된다.

* 여기서 View와 View Name은 나중에 그릴 ViewResolver에서 View를 가르킨다.

* 오해할만한 것이 있는데 ModelAndView에서 View와 View Name이 ViewResolver에서 그릴 View를 지정하지만 데이터를 가지고 있는 View를 가르키는 건 아니다.

### ViewResolver

* 앞에서 ModelAndView를 처리한 것을 가지고 View를 그린다.

* 이때 처리된 View는 클라이언트에게 바로 보여지는 View이고 반환되는 View이다.

## 나의 생각

> 테코톡 MVC패턴에 대해 강의를 보았는데 내 기억으로는 옛날에 코드를 썼을 때 코드가 오류나 수정해야될때 코드를 싹다 갈아엎어야된다고 들었는데 그런 면에서 MVC패턴이 개발자들에게는 편리하겠지만 View로 띄울 수 있는 게 html또는 JSP라고 들어서 한계가 분명 존재한다고 생각합니다!