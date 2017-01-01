# 스위프트 
## 작성자 : 이동준 
***
## 웹에서의 처리.
### 웹뷰.
```
let stringURL = "http:www.google.co.kr"
if let url = URL(string: stringURL){   //URL 객체 만들기.
  let urlreq = URLRequest(url: url) // URL 요청 만들기.
  myWebView.loadRequest(urlreq) // 웹뷰로 읽어 들이기.
}
```

### 애플리케이션에서 사파리를 띄워서 사용.
- SFSafariViewController는 애플리케이션에서 사파리를 일시적으로 띄워 웹사이트를 출력하는 방식.
- Info.plist를 사용하지 않고, 여러 사이트를 출력할 경우 SFSafariViewContoller를 사용한다.
```
import UIkit
import SafariServices  //SafariServices 임포트.
class ViewController: UIViewController{
 @IBAction func tapBtn(){
   if let url = URL(string: "http://www.apple.com/kr"){  // URL 객체 만들기.
   let vc  = SFSafariViewController(url: url) //URL객체로 지정한 페이지를 출력하는 SFSafariViewController 객체 
     present(vc, animated: true, completion: nil)
   }
 }
}
```
### 애플리케이션에서 사파리를 띄워서 사용.-> 컨트롤러가 종료될때를 알아야 할경우.
- SFSafariViewController가 끝날때는 SFSafariViewControllerDidFinish() 메서드가 호출.
- 이 메서드를 사용하면 SFSafariViewController가 종료될 때 특별한 처리 가능.
```
import UIkit
import SafariServices  //SafariServices 임포트.
class ViewController: UIViewController, SFSafariViewControllerDelegate{ // SFSafariViewControllerDelegate를 통해 통지 받을 준비
 @IBAction func tapBtn(){
   if let url = URL(string: "http://www.apple.com/kr"){  // URL 객체 만들기.
   let vc  = SFSafariViewController(url: url) //URL객체로 지정한 페이지를 출력하는 SFSafariViewController 객체 
    vc.delegate = self // 통지 받을 대상을 자기 자신(뷰 )으로 설정함 
     present(vc, animated: true, completion: nil) 
   }
 }
 func SFSafariViewControllerDidFinish(_controller: SFSafariViewController){ 
  // 메서드를 생성하여  SFSafariViewController가 닫힐때 자동 호출 되게끔 처리, 
  print("close")
 }

```

### 이미지 뷰(웹에서 이미지 데이터 내려 받기)
- 지정한 URL에서 로우(raw)데이터를 내려 받는다.
- 로우 데이터를 애플리케이션에서 사용할 수 있는 이미지 데이터로 변환하고, 이미지 뷰에 출력한다.
- NSData는 동기 통신을 수행하는 메서드.
```
@IBOutlet weak var imageview: UIImageView! // 이미지 뷰
     
    @IBAction func tapLoadImage() {
      let stringurl = "https://wikibook.github.io/swift3-textbook/sample.jpg"
        if let url = URL(string: stringurl){ // URL을 나타내는 문자열로 URL객체를 생성.
                if let data = NSData(contentsOf: url){ //데이터를 내려받아 로우 데이터 만들기 NSData(contentsOf: url)
                imageview.image = UIImage(data: data as Data) // 로우 데이터를 이미지 데이터로 변환하고 이미지 뷰에 출력
           }
        }
    }
```

### 웹에서 텍스트  데이터 내려 받기.
- 웹에서 텍스트 데이터를 내려 받을 때에는 URLSession을 사용한다.
- URLSession은 웹 서버와 통신하는 객체이다. (지정한 url의 데이터를 읽어주세요, 그리고 완료되면 알려주세요! )
- 메인 프로그램은 통신 명령만 내리고, 실제 처리는 서버에서 하는 비동기 통신 방식을 사용.

#### 방법1. 메서드를 만들지 않는 방법.
```
@IBAction func tapbtn3() {
        if let url = URL(string: "https://wikibook.github.io/swift3-textbook/test.txt"){  // url 객체 만들기
             let urlSession = URLSession.shared // 세션 객체 만들기.
           let task  = urlSession.dataTask(with: url, completionHandler:{ 
           // urlSession의  dataTask를 이용하여, 태스크(데이터를 내려받기 위한 작업)을 만든다.
           // 내려 받을 대상 url 지정, 통신이 완료되면, 실행할 처리를 completionHandler 뒤에다가 
           
          (data, response, error) in // 통신이 완료되면, 데이터, 상태정보, 오류 코드 형식의 튜플 사용 가능
                if let nsstr = NSString(data: data!, encoding: String.Encoding.utf8.rawValue){ 
                // 내려받은 데이터는 로우 데이터 이기때문에 utf-8 처리.
                    let str = String(nsstr) // 스트링타입으로  변환.
                    print("문자열 =  [\(str)]")
                }
            })
            task.resume() // 태스크를 실행함. -> resume메서드를 호출하면 실행됨.
       }
    }
```
    
#### 방법2. 메서드를 만드는 방법.
- 방법1과 동일하나, 내려받기가 완료됬을때, 만들어둔 다른 메서드를 호출하는 방식.
- 복잡한 처리를 메서드로 옮겨서 사용가능함.

#### 에러 발생함.., -> 원인은 찾지 못함 ..
```
@IBAction func tapbtn4() {
        if let url = URL(string: "https://wikibook.github.io/swift3-textbook/test.txt"){ // url 객체 생성.
           
            let urlSession = URLSession.shared // 세션 객체 생성.
            let task  = urlSession.dataTask(with: url, completionHandler: onFinish) // 데이터 태스크 만들기.
            //completionHandler: onFinish)as! (Data?, URLResponse?, Error?) -> Void) 이런식의 변환이 필요하다고 나옴.
           
            task.resume() // 태스크 실행.
        }
    }
    
    func onFinish(data: Data?, response: URLResponse?, error: NSError?){ // 통신 완료시 호출할 메서드 만들기.
            if let nsstr = NSString(data: data!, encoding: String.Encoding.utf8.rawValue){ // utf-8처리.
           let str = String(nsstr)
            print("문자열 =  [\(str)]")
        }
    }
```

### JSON 데이터 파싱
- json이란 웹 애플리케이션에서 무언가를 주고 받을때 사용하는 데이터 형식,
- 배열은 []로 감싸고, 각 데이터를 쉼표로 구분해서 나열-> ["동준","동준2"]
- 딕셔너리는 {}로 감싸고, 각 데이터를 키:값 형식으로 구분 -> {"name":"동준", "age":"25"}
- 딕셔너리에 여러개의 배열 나열 가능 - >  [{"name":"동준1", "age":"25"}, {"name":"동준2", "age":"25"}, {"name":"동준3", "age":"25"}]

#### JSON 데이터 파싱 방법, -> NSJSONSerializtion 이용.
#### NSJSONSerializtion.JSONObjectWithData()를 실행하는 것만으로도 JSON데이터가 파싱됨.
- JSON 데이터를 배열로 파싱할때는 자료형을 NSArray로 지정해야 한다. -> 마지막에 as!NSArray를 붙여 준다.
- JSON 데이터를 딕셔너리로 파싱할때는 자료형을 NSDictionary로 지정해야 한다. -> 마지막에 as!NSDictionary를 붙여 준다.
- JSON 데이터 파싱을 위한 오류 처리 -> do try catch 구문 사용.
```
do{
  try < 오류가 발생할 지도 모르는 처리>
   < 오류가 발생하지 않았을때의 
}catch{
   < 오류가 발생했을때의 처리 >
}
```
#### 예시.

```
var jsonstr1 = "[100, 200]" // 샘플 json 데이터 형식
var jsonstr2 = jsonstr1.data(using: String.Encoding.utf8) // 파싱 테스트 하기 위해 로우데이터로 변환함
do{
    var array = try JSONSerialization.jsonObject(with: jsonstr2!, options: JSONSerialization.ReadingOptions.mutableContainers) as! NSArray
 print(array)
}catch{
  print("응 에러 ㅠ")
}
```
