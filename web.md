# 스위프트 
## 작성자 : 이동준 
***
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
