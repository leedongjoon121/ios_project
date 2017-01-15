# CoreLocation



> ios는 디바이스의 현재 위치에 대한 정보를 알아오는데에 있어서 GPS, 기지국 삼각측량과 와이파이의 IP 주소를 사용한다. 현 시스템에서 사용할수 있는 방법 중 가장 정확한 것을 이용하여 위치 정보를 얻는다.



#### 정의

 ![사진](https://github.com/leedongjoon121/ios_project/blob/master/determineCL.png?raw=true)



>  With Core Location, you have to test and debug your app on a device. There is no support in iOS Simulator for  current exact location of the user.



---



#### Index

* [1. Class](#ch-1)
* [2. Protocols](#ch-2)
* [3. 사용 방법](#ch-3)
* [4. Structures](#ch-4)
* [5. Extended Types](#ch-5)




### Class <a id="ch-1"></a>

- CLBeacon

> 1. CLBeacon 클래스는 특정 영역을 감시하며, 그 감시 영역중 검출된 이벤트를 나타낸다.
>
>
> 2. 클래스의 인스턴스를 직접 만들지 않는다.
>
>
> 3. Location manager 객체는 디바이스에 탐지된 비콘에게 관련된 객체에 위임 한다.
>
>
> 4. 비콘 객체의 정보를 사용하여 어떤 비콘이 발생했는지 식별이 가능 하다.



- CLBeaconRegion

> 1. CLBeaconRegion 객체는 지리적 위치가 아니라 Bluetooth 비콘에 대한 장치의 접근성을 기반으로 하는 영역 유형을 정의 한다.
> 2. 비콘 영역은 사용자가 제공한 정보와 일치하는 식별 정보를 가진 장치를 찾는다.
> 3. 해당 장치가 범위안에 들어오면 해당 지역에서 적절한 알림이 전달 된다.



- CLCircularRegion

> 1. CLCircluarRegion 클래스는 지리적 영역의 위치와 경계를 정의 한다.
> 2. CLCircluarRegion 클래스의 인스턴스를 사용하여 특정 위치에 대한 geofences를 이용 할 수 있다.
> 3. 설정된 geo fences의 경계를 넘으면 location manager가 해당 delegate에 알린다.



- CLFloor

> 1. CLFloor 객체는 사용자가 실제 위치하고 있는 건물의 바닥을 위치로 지정한다.
> 2. Floor 정보가 지정될 수 있는 장소에서, CLLocation 객체는 일반 위치 데이터와 함께 floor 객체를 포함 할 수 있다.



- CLGeocoder

> 1. CLGeocoder 클래스는 위도와 경도로 지정된 좌표와 사용자에게 친숙한 좌표간의 변환 처리를 위한 서비스를 제공 한다.
> 2. 좌표에 대한 표현은 일반적으로 주어진 위치에 해당하는 거리, 도시, 주 및 국가 정보로 이루어 지지만 관련 관심 장소, 경계표 또는 기타 식별자를 포함 할 수도 있다.
> 3. geocoder 객체는 네트워크 기반 서비스와 함께 작동하여 지정된 좌표 값에 대한 위치 정보를 조회하는 single-shot object 이다.



- CLHeading

> 1. CLHeading 객체는 CLLocationManager 객체에 의해 생성된 heading data를 포함 한다.
> 2. Heading data는 true 값과 자북(북쪽-magnetic north)에 대한 계산된 값으로 구성 된다.
> 3. Heading data는 3차원 벡터의 값을 포함하는 raw data도 포함 한다.



- CLLocation

> 1. CLLocation 객체는 CLLocationManager 객체에 의해 생성 된 위치 데이터를 나타 낸다.
> 2. CLLocation 객체는 장치 위치의 지리적 좌표와 디바이스의 위치가 측정된 고도(altitude)의 값을 통합하여 관리 한다.
> 3. IOS에서 CLLocation 객체는 디바이스가 움직이는 속도와 방향에 대한 정보에 대한 처리를 한다.



- CLLocationManager

> 1. CLLocationManager 클래스는 위치 정보와 방향 정보 이벤트를 앱에 전달 하기 위한 핵심이다.(컨트롤러)
> 2. CLLocationManager 클래스의 인스턴스를 사용하여 위치 정보와 방향 정보 이벤트를 전달해야 하는 시기를 결정 하고, 실제 전달을 시작하거나 중지하는 매개변수를 설정 하는 역할을 한다.
> 3. CLLocationManager 객체를 통하여 가장 최근의 위치 정보와 방향 정보 데이터를 검색 할 수도 있다.



- CLPlacemark

> 1. CLPlacemark는 주소정보를 지리적 위치 또는 지역 정보와 연관 시켜 작업을 처리 한다.



- CLRegion

> 1. CLRegion 클래스는 추적할 수 있는 (tracking) 추상 영역 작업 처리를 한다.
> 2. IOS에서는 이 클래스의 인스턴스를 직접 만들지 않는다, 대신 특정 유형의 영역을 지정하고 있는 하위 클래스를 인스턴스화 하여 사용 된다.
> 3. macOS에서는 이 CLRegion클래스의 인스턴스를 만들고 이를 사용하여 영역 정보를 저장한다.  
> 4. 영역 정보를 저장한 후에는 반드시!!!! CLLocationManager 객체로 영역을 등록 해야 한다.
> 5. location manager는 사용자가 지역의 경계를 넘을 때마다 이벤트를 생성 한다.



- CLVisit

> 1. CLVisit 객체는 사용자가 원하는 장소(사용자가 원해서 직접 지정한 장소)에 대한 정보를 캡슐화 한다.
> 2. CLVisit 객체는 시스템에서 만들어 이벤트 전달을 시작한 후 CLLocationManager 개체에 의해 해당 delegate에 전달됨.
> 3. CLVisit 객체는 visit이벤트가 발생한 위치와 관련 있는 도착 및 시작에 대한 정보가 포함 된다.
> 4. CLVisit 객체를 직접 만들지 않고 CLVisit의 하위 클래스를 만들어야 한다.



### Protocols <a id="ch-2"></a>

- CLLocationManagerDelegate

> 1. CLLocationManagerDelegate 프로토콜은 CLLocationManager 객체에서 위치 및 방향 정보를 업데이트 받는데 사용되는 메서드 이다.



#### 사용방법 <a id="ch-3"></a>

1. CoreLocation 프레임워크 추가.

![사진](https://github.com/leedongjoon121/ios_project/blob/master/plus_core_fw.png?raw=true)





2. Info.plist에서 -> 허가설정을 한다.

![사진](https://github.com/leedongjoon121/ios_project/blob/master/Info1.png?raw=true)



- Privacy - LocationWhenInUseUsageDescription를 입력하고 value값 작성 (포그라운드에서 작동)
- Privacy - LocationWhenInUseUsageDescription를 입력하고 value값 작성(백그라운드에서 작동)





3. 뷰 컨트롤러에서 CoreLocation import &  CLLocationManagerDelegate추가.

![사진](https://github.com/leedongjoon121/ios_project/blob/master/import_cl.png?raw=true)



4. CLLocationManager 추가.

```swift
let manager = CLLocationManager()
```



5. viewDidLoad( ) 내용 추가

- 위치 접근 허가 요청 : 애플리케이션이 위치 데이터를 추적하려면 사용자로 부터 이에 대한 허가를 구해야 한다. -> CLLocationManager의 인스턴스를 이용해 호출 한다. -> 포그라운드 or 백그라운드 중에 선택!!
- 위치 정확도 설정 : 애플리케이션이 위치 데이터를 추적할때 정확도를 설정 할 수 있다. -> 정확도는 CLLocationManager 객체의 desiredAccuracy 속성을 통해 설정 된다. -> 정밀한 정확도는 배터리를 많이 소모해서 적절한 조정이 필요!!
  - kCLLocationAccuracyBestForNavigation : 가장 높은 수준의 정확도, 외부 전원이 연결되어 있을 경우에만 사용
  - kCLLocationAccuracyBest : 배터리로 동작할때 권장되는 가장 높은 수준의 정확도
  - kCLLocationAccuracyNearsetTenMeters : 10미터 이내의 정확도
  - kCLLocationAccuracyHundedMeters : 100미터 이내의 정확도
  - kCLLocationAccuracyKilometer : 1킬로미터 이내의 정확도
  - kCLLocationAccuracyThreeKilometers : 3킬로미터 이내의 정확도

```swift
 override func viewDidLoad() {
        super.viewDidLoad()
		  
		  manager.delegate = self
		  manager.desiredAccuracy = kCLLocationAccuracyBest // 위치 정확도 설정 
          manager.requestWhenInUseAuthorization() //허가 설정 (포그라운드) 
          manager.startUpdatingLocation()// 위치 업데이트 시작 -> 위치가 업데이트 될 때마다, 
           /*로케이션 매니저에 의해 didUpdateToLocation델리게이트 메서드가 호출될 것이며, 
             현재 위치에 대한 정보가 전달 될 것이다.
           */
 }         
```



6. Location Manager Delegate : 로케이션 매니저는 CLLocationManagerDelegate 프로토콜에 정의된 3개의 메서드를 사용하여 위치 정보 변경과 에러, 퍼미션 변경여부를 알려준다.

- func locationManager : CLLocation 객체로부터 위치 정보를 획득 한다.
- 위치 정보는 didUpdateLocation 델리게이트 메서드를 통해 CLLocation 객체의 형태로 전달 되며 다음 데이터를 포함 
  - Latitude
  - Longitude
  - Horizontal Accuracy
  - Altitude
  - Altitude Accuracy



```swift
func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
 let location = locations[0] // 가장 최신 위치
 
 /*
 스팬은 지도보기 객체가 사용하는 현재 줌 레벨도 정의합니다.
 */
  let span:MKCoordinateSpan = MKCoordinateSpanMake(0.01, 0.01) // 줌 정설정 값이 작을수록 확대 됨
        
/*
CLLocationCoordinate2D: 지리적 좌표가 포함 된 구조체 포멧 이며, 
                        맵킷 뷰가 어떻게 나타낼지에 대한 정보를 갖고 있음

CLLocationCoordinate2DMake: 위도와 경도 값을 좌표 데이터 구조 형식으로 형식화 하며. 리턴 값으로 
                            위도와 경도 값을 포함하는 좌표 구조를 리턴한다.
*/
        let myLocation:CLLocationCoordinate2D =   
   CLLocationCoordinate2DMake(location.coordinate.latitude, location.coordinate.longitude)
    // 현재 디바이스의 위치 값 
    
        let pin_location:CLLocationCoordinate2D =       
   CLLocationCoordinate2DMake(37.303169,127.008660) // 마커 위치
   
   /*
   MapKit Data Types : Map Kit 프레임 워크에 있는 데이터 유형을 포함 하며, 데이터 타입으로는 아래와같다

    MKCoordinateRegion: 지리적 좌표가 포함된 구조체 포멧 이며, 지도에 추가할 사항에 대한 영역을 표시 하는 
                        새로운 객체를 생성 한다.
    
    MKCoordinateRegionMake: 지도 부분의 어느 부분에 표시를 할지 정의 하는 구조체, 파라미터로 추가할 영역에 대한 좌표 값과, 추가할 영역이 표시 할 지도의 크기를 줌으로 설정 한 값을 설정 한다.

   */
        let region:MKCoordinateRegion = MKCoordinateRegionMake(pin_location, span)
        
        map.setRegion(region, animated: false) // 맵에 추가 
        
        let annotation = MKPointAnnotation() // 마커 객체
           annotation.coordinate = pin_location // 좌표는 위에서 설정한 핀 좌표로 설정 
           annotation.title = "우리집 _ 북수원 홈플러스" // 내용 추가~
           annotation.subtitle = "놀러오세유~~"
        
        map.addAnnotation(annotation) // 마커 추가
        self.map.showsUserLocation = true // 현재 사용자 위치 추가
```



7. 에러 처리

```swift
  func locationManager(_ manager: CLLocationManager, didFailWithError error: Error) {
        print("ㅜㅜ 에러 났어용 ~~ \(error.localizedDescription)")
    }
```



### 결과 화면

![사진](https://github.com/leedongjoon121/ios_project/blob/master/result.jpeg?raw=true)





