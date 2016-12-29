# 스위프트 옵셔널 
## 작성자 : 이동준 
##### 스터디 개념 참조 : <http://chanlee.github.io/2015/06/14/Introduce-Swift-Optional/>
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
- 이것을 수정할 수 있도록 에러를 발생한다. 이렇게 컴파일시에 nil 체크를 수행함으로써 잠재적인 에러를 탐지할 수 있다는것이 옵셔널의 장점이다

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

### optional binding
- 옵셔널 바인딩은 옵셔널이 값을 가지고 있는지 아닌지를 체크한다.
- 값이 있을 경우 그것을 꺼내어 임시로 특정 상수(또는 변수)에 값을 보관하는 방법을 말한다.

#### 예시 
```
var stockCode:String? = findStockCode("Facebook")
 let text = "Stock Code - "
 if let tempStockCode = stockCode {
 let message = text + tempStockCode
 println(message)
 }
```
#### 예시 설명
#####  “if let”(또는 if var 도 사용 가능) 구문은 두가지 의미를 내포하고 있다. 
##### 쉽게말해, “만일 stockCode가 값을 가지고 있다면, 이것을 꺼내서 (1)tempStockCode에 값을 대입하고, 
##### (2) 조건문 블록을 실행하라” 는 것을 의미 한다. 그렇지 않다면 조건문은 실행되지 않는다.
##### tempStockCode는 새로운 상수이므로 끝에 느낌표(!)를 사용할 필요가 없다.

### 옵셔널 체이닝 
#### 옵셔널 체이닝 적용전 예시
```
class Stock {
    var code: String?   // 
    var price: Double?
}
func findStockCode(company: String) -> Stock? {
    if (company == "Apple") {
        let aapl: Stock = Stock()
        aapl.code = "AAPL"
        aapl.price = 90.32
        return aapl
    } else if (company == "Google") {
        let goog: Stock = Stock()
        goog.code = "GOOG"
        goog.price = 556.36
        return goog
    }
    return nil
}
```

#### 위의 예제에서 옵셔널바인딩 적용
  
```
if let stock = findStockCode("Apple") {
    if let sharePrice = stock.price {
        let totalCost = sharePrice * 100
        println(totalCost)
    }
}
```
#### findStockCode()의 반환값은 옵셔널이므로, 옵셔널 바인등을 사용해 nul-체크를 하고 stock의 price 역시 옵셔널 이므로 다시 한번 if let~ 문을 사용하였다.  
### 옵셔널 체이닝 적용 .     
```
if let sharePrice = findStockCode("Apple")?.price {
    let totalCost = sharePrice * 100
    println(totalCost)
}
```
#### 설명 
- 중첩된 “if set” 문을 사용하는 대신 옵셔널 체이닝을 사용해 더 간단히 할 수 있다. 
- 옵셔널 체인은 “?.” 오퍼레이터를 사용해 다수의 옵셔널을 체인으로 묶을 수 있다. 


    
    
    
    
    
    
