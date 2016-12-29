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
var number:Int = 10   // Integer 형태. 
let weight:Double = 1.23  // Double 형태.
var flag:Bool = true / false // Boolean 형태.
var name = "String 타입 문자열 지정법" . // String 형태.
```

### 자료형 변환 
#### 문법  : 변환할 자료형(값).
#### 예시
```
let string_num = "100"  // 스트링 
let cast_num = Int(string_num)       // Integer 타입으로 변환

let number : Int = 200      //  Integer 타입
let cast_number = Double(number)  // Double 타입으로 변환

let number = 5
let string_num :String = "문자열로 변환 합니다"+String(number)+"이런식으로요 ~"

```

### 조건문.
#### switch
```
var dice  = 1
switch dice {
case 1: print("~~~~ 1")
case 2,5: print("~~~~ 2 or 5")
default : print("~~~~ 디폴트 ")
} // break 가 필요 
```

### 배열.
```
var int_array = [1,2,3]
var string_array = ["A","B","C"]

// 자료형을 지정해서 배열 만들기.
var int_array:[Int] = [1,2,3]
var str_array:[String] = ["a","b","c"]

// 같은 초기값이 있는 배열 만들기.
var int_array = Array(repeating:0, count:3) . // 0을 3개 가진 배열 => [0,0,0]
var str_array = Array(repeating:"A", count:3) . // A 를 3개 가진 배열 => ["A","A","A"]

// 빈 배열만들기
var empt_arr:[String] = []
var empt_arr2 = [String]()    // 둘다 같은 뜻임

// 배열 요소 갯수 확인
var int_arr = [1,2,3,4,5]
print(int_arr.count) // 5출력

```

#### 배열의 조작
```
// 가장 마지막 위치에 요소 추가.
var str_arr = ["a","b","c"]
srt_arr.append("d")

//지정한 위치에 요소 추가.
var str_arr = ["a","b","c"]
str_arr.insert("d", at:1) // 1번 인덱스에 d

//지정한 위치의 요소 제거.
var str_arr = ["a","b","c"]
str_arr.remove(at:1) //1번 인덱스 요소 제거

// 요소 모두 제거.
var str_arr = ["a","b","c"]
str_arr.removeAll()

//오름차순 정렬.
var int_arr = [4,3,1,5,2]
var sort_arr = int_arr.sorted(by: <) // 오름 차순으로 정렬함 
```
```
