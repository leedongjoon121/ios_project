# 스위프트 
## 작성자 : 이동준 
***
### 템플릿
|템플릿|설명|
|:---:|:---:|
|single view application|1개의 뷰로 구성된 애플리케이션 만들때 사용하는 템플릿|
|Tabbed application|화면의 하단에 탭 바가 있는 애플리케이션 만들때 사용하는 템플릿|
|master-detail application|계층구조를 가지는 애플리케이션 만들때 사용하는 템플릿|
|game|게임을 만들때 사용하는 템플릿|
|page-based application|페이지를 넘기는 애플리케이션을 만들 때 사용하는 템플릿|

### 프로젝트 내부 파일.
|네비게이터|설명|
|:---:|:---:|
|AppDelegate.swift|애플리케이션 전체 프로그램을 작성하는 파일로 앱이 닫혀 있는 상태등에서가 하고 싶을때|
|ViewController.swift|화면(view)속의 움직임을 제어하는 프로그램을 작성하는 파일|
|Main.storyboard|스토리보드 파일이며, 애플리케이션의 화면을 작성함|
|Assets.xcassets|아이폰에 표시되는 이미지의 해상도 등을 관리하는 이미지 에셋|
|LaunchScreen.storyboard|스토리보드 파일이며, 앱이 시작된 직후 표시되는 시작화면을 만들때 사용|
|Info.plist|애플리케이션의 설정파일이며,기본 설정은 프로젝트파일에서 수행하기 때문에 거의 수정하지 않음|

### 오토 레이아웃 
#### 화면의 크기가 달라지더라도 의도한 대로 레이아웃을 만들려면 오토레이아웃(Auto Layout)을 사용한다.
#### 오토레이아웃은 화면의 비율이나 크기에 따라 자동으로 레이아웃을 변화시켜주는 기능이다.

#### IB :  IBOutlet, IBAction의 IB는 인터페이스 빌더를 의미
#### Outlet : 현실에서 일반적으로 물건을 싸게 처분하는 곳이라는 의미, 즉 연결 통로 같은 곳, 

### 변수
#### var score = 100
#### score = 200

### 상수 .
#### let myage = 20

** 상수와 변수를 만들었는데 사용하지 않으면 에러가 발생한다. **

### 반복문
#### `for index in 0 ... 5 {}` .   0~5까지 반복, index 값으로 사용

### 자료형
#### var 변수이름 : 자료형 = 값 의 형태.   
#### 예시 
```
var number:Int = 10
let weight:Double = 1.23
var flag:Bool = true / false
var name = "String 타입 문자열 지정법"
```




