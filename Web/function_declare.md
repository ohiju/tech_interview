# JS에서 함수를 선언하는 5가지 방식
- 참고: 
    - [함수 표현식과 선언식](https://joshua1988.github.io/web-development/javascript/)function-expressions-vs-declarations/
    - [new Function 문법](https://ko.javascript.info/new-function)

## 함수 표현식
    - 호이스팅에 영향을 받지 않는다.
    - 클로저로 사용
    - 콜백으로 사용

    ## 포인터 함수
    - const func = () => {}

    ## 일반
    const func = function(){}

    ## 
    const func = new Function()

## 함수 선언식 
    ## 
    - function func (){}

    ## 
    - (function(){})()

