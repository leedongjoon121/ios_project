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
- 로우 데이터를 애플리케이션에서 사용할 수 있는 이미지 데이터로 변환하고, 이미지 뷰에 

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

#### 방법1. 메서드를 만들지 않는 방법.

    
