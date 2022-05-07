---
title: arrow function and this 
date: 2022-05-08
tags: [this] 
---

## **this**

콜백함수 내부의 this가 외부 함수의 this와 다르기 때문에 발생하는 문제 

![this-error](/media/this-1.png)

고차 함수(함수를 받아서 함수를 리턴할수있는 함수) 의 인수로 전달되어 고차 함수 내부에서 호출되는 콜백함수의 예제이다. 

프로토타입 메서드 add의 내부에서 this는 메서드를 호출한 객체를 가리킨다. (위 예제에서는 coffee 객체). 클래스 내부의 모든코드에는 strict mode가 암묵적으로 적용된다. 따라서 map 메서드의 콜백함수에도 strict mode가 적용된다.

클래스 내부의 모든 코드에는 strict mode가 암묵적으로 적용된다. strict mode에서 일반 함수로서 호출된 모든 함수 내부의 this에는 전역 객체가 아니라 undefined가 바인딩 되므로 위 예제에서 map 메서드의 콜백함수 내부의 this에는 undefined가 바인딩된다. 

### **이와같은 문제를 해결할 수 있는 방법** 

1\. this를 할당 한 후 콜백 함수 내부에서 사용

![this-error](/media/this-2.png)

2\. map의 두번째 인수로 add 메서드를 호출한 coffee 객체를 가리키는 this를 전달한다. 

![this-error](/media/this-3.png)

3\. bind 메서드를 사용하여 this를 바인딩한다.

![this-error](/media/this-4.png)

### **화살표함수를 사용하여 해결하는 방법**

ES6에서는 화살표 함수를 사용하여 해결할수있다. 

화살표 함수는 함수 자체의 this 바인딩을 갖지 않는다. 따라서 화살표 함수 내부에서 this를 그대로 참조한다.

![this-error](/media/this-5.png)
