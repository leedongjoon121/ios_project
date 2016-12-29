# ios 개념 정리 & mark down 연습 
## 스터디 시작일 : 2016 12. 22
***
### 옵셔널
- Swift에서 변수를 선언할때는 기본적으로 옵셔널이 아닌(non-optional)값을 지정해야 한다.
- 변수에는 반드시 nil 이 아닌(non-nil) 값을 할당 해야만 한다. 
- 만일, 옵셔널이 아닌 변수에 nil 을 설정하려 하면 컴파일러는 nil값을 할당 할 수 없다고 오류를 발생시킬 것이다.

#### 예시1

```
   var message: String = "Swift is awesome!" // OK .  
   message = nil // 이렇게 하면 에러가 발생함!
```   

### optional wrapping
#### 예시1 ####
```
func findStockCode(company: String) -> String? {
 if (company == "Apple") {
 return "AAPL"
 } else if (company == "Google") {
 return "GOOG"
 }
 return nil
 }
 var stockCode:String? = findStockCode("Facebook")
 let text = "Stock Code - "
 let message = text + stockCode  // compile-time error
 println(message)
 ```
#### 예시1-설명 
- stockCode는 문자열 또는 nil값일 수 있다. 옵셔널 문자열인 String?은 업랩(Unwrapped)되지 않았으므로,
 > 이것을 수정할 수 있도록 에러를 발생한다. 이렇게 컴파일시에 nil 체크를 수행함으로써 잠재적인 에러를 탐지할 수 있다는것이 옵셔널의 장점이다

### optional unwrapping
#### 예시1
```
 var stockCode:String? = findStockCode("Facebook")
 let text = "Stock Code - "
 if stockCode {.  //if문으로 nil 체크를 했다고 치는것 같음
 let message = text + stockCode!
 println(message)
 }
```
- 스위프트에서 느낌표는 강제 언래핑(Unwrapping)을 할때 사용된다. 
- if문으로 stockCode에 값이 있다는것을 확인했으므로, 위와 같이 옵셔널 변수에 !를 붙여 값을 꺼낼 수 있다.
 
