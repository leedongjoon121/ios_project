# ios 개념 정리 & mark down 연습 
## 스터디 시작일 : 2016 12. 22
***
### 옵셔널
##### Swift에서 변수를 선언할때는 기본적으로 옵셔널이 아닌(non-optional)값을 지정해야 한다.
####  변수에는 반드시 nil 이 아닌(non-nil) 값을 할당 해야만 한다. 
#### 만일, 옵셔널이 아닌 변수에 nil 을 설정하려 하면 컴파일러는 nil값을 할당 할 수 없다고 오류를 발생시킬 것이다.
#### 예시1
<prev><code>
    var message: String = "Swift is awesome!" // OK
    message = nil // 이렇게 하면 에러가 발생함!
     
</code></prev>
