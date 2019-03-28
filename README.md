# **PhotoFrame**

# step1. Tabbed App 템플릿(19.03.12)

<img width="1440" alt="스크린샷 2019-03-12 오후 5 21 53" src="https://user-images.githubusercontent.com/31604976/54185320-0ba76080-44ec-11e9-9cb2-4b44df2731ee.png">

file : /Users/jina/github/swift-photoframe/PhotoFrame/PhotoFrame/FirstViewController.swift  

line : 16  

function : viewDidLoad()  

column : 40 (16번 행의 40번 열에 있다. #column이 시작되는 곳이 40번이다.)  

### UITabBarController 와 UITabBar
- UITabBarController
버튼을 눌렀을 때 보여질 자식 컨트롤러를 결정하는 라디오 스타일의 선택 장치로 윈도우 하단에 각각 다른 모드를 선택하도록 표시한다. 
사용자가 특정 탭을 누르면 해당 뷰 컨트롤러로 대체되며, 서로 다른 유형의 정보를 표시하거나 완전히 다른 스타일의 인터페이스를 사용하여 동일한 정보를 표시하기 위해 사용된다.

- UITabBar
앱에서 하위 잡업이나 모드 선택을 위해 하나 또는 하나이상의 버튼을 표시하는 컨트롤.
UITabBarController와 사용되지만, 독립적으로 사용할 수 있다. 

------------------------------------------------------------------------------------------------------------------------

UITabBarController는 버튼을 눌렀을 때 대체될 뷰를 보여주는 역할을 하고 UITabBar는 버튼자체를 프로그래머가 디자인 하고 보여주는 역할을 한다.

# step2. IBOutlet

<img width="547" alt="스크린샷 2019-03-13 오후 9 46 30" src="https://user-images.githubusercontent.com/31604976/54280188-3b349680-45da-11e9-9284-46804be03d75.png">

# step3. IBAction

다음 버튼을 추가하여 버튼을 누르면 '노리의 사진액자' 배경색 변경

<img widht="400" src="https://user-images.githubusercontent.com/31604976/54746618-f9c26d80-4c0f-11e9-842f-a28de4731633.jpg">

- IBAction 과 IBOutlet

IB = Interface Builder 

: 간단하게 드래그앤드롭만으로 윈도우,버튼,텍스트필드 등의 객채를 사용자 인터페이스 기능을 만들어 다이나믹한 동작을 만들수 있게 해준다.

Cocoa와 Cocoa Touch는 MVC패턴을 이용하여  인터페이스를 독립적으로 구현하고 기능을 분리하기 쉽기 때문이다.

MVC 패턴이란 데이터를 소유한 Model과 사용자에게 보여지는 View 그리고 View에서 발생되는 Event를 받아서 Model을 갱신하는 Controller를 의미하는데 View와 ViewController를 연결해주는 역할을 하는 것이 IBAction과 IBOutlet이다

IBAction : View에서 Event가 발생되었을 때 호출되는 함수  

IBOutlet : Button 등 View의 Controller에 접근하기 위한 변수

# step4. Scene과 Segue

First View옆에 새로운 view controller를 추가하여 다음 버튼과 연결하였을 때의 변화를 확인

<img width="600" src="https://user-images.githubusercontent.com/31604976/54804955-bbcd5400-4cb8-11e9-8043-4dfade42bc70.png">

<img width="1440" src="https://user-images.githubusercontent.com/31604976/54806229-bffb7080-4cbc-11e9-9e3f-eca866f74b09.png">

<img width="350" src="https://user-images.githubusercontent.com/31604976/54806759-5b411580-4cbe-11e9-93ca-ffc48248c0b6.gif">

* segue types 

|          Type          |                           Behavior                           |
| :--------------------: | :----------------------------------------------------------: |
|      `show(push)`      |              새로운 내용의 뷰컨트롤러를 보여줌               |
| `Show Detail(Repalce)` | show와 흡사하지만 푸시가 아닌 교체가 됨, split뷰컨트롤러에서 마스터영역을 오른쪽 디테일 뷰에 상세 내용을 표시해줌 |
|   `Present Modally`    | 새로 로드하는 컨텐츠 뷰를 모달 형태로 띄움, 계층구조 또는 스택에 속하지 않고 뷰 위에 위치하며 새로운 뷰를 띄운다. |
| `Present as Propover`  | 현재 보여지는 뷰 위에 앵커를 가진 팝업 형태(작은 뷰 컨트롤러) |

# step 5. ViewController 프로그래밍

다음 버튼을 누르면 다음 화면으로 전환 되고 close버튼을 누르면 이전 화면으로 돌아간다.

<img src="https://user-images.githubusercontent.com/31604976/54906787-5b901980-4f27-11e9-986c-d90432dcd947.gif">

## 뷰컨트롤러의 라이프사이클

<center><img width="400" src="https://t1.daumcdn.net/cfile/tistory/2613D13C58C64DE32C"><center>

- viewDidLoad()  

  뷰의 컨트롤러가 메모리에 로드되고 난 후에 호출됩니다. 이 viewDidLoad 메소드는 뷰의 로딩이 완료 되었을 때 **시스템에 의해 자동으로 호출**되기 때문에 일반적으로 리소스를 초기화하거나 초기 화면을 구성하는 용도로 주로 사용합니다.

  화면이 처음 만들어질 때 한 번만 실행되므로, 처음 한 번만 실행해야 하는 초기화 코드가 있을 경우 이 메소드 내부에 작성하면 됩니다. 

   ++ loadView가 뷰를 만들고, 메모리에 올린 후에 viewDidLoad가 호출된다

- viewWillAppear()  

  뷰가 이제 나타날 거라는 신호를 컨트롤러에게 알리는 역할을 합니다. 즉 뷰가 나타나기 직전에 호출된다고 볼 수 있다. 다른 뷰에서 갔다가 다시 돌아오는 상황에 해주고 싶은 처리가 있을 때는 viewWillAppear에서 해주면 된다.

  참고 : https://zeddios.tistory.com/44

- viewDidAppear()  

  뷰가 나타났다는 것을 컨트롤러에게 알리는 역할을 합니다. 데이터 가져오기 또는 애니메이션 표시와 같이 뷰가 화면에 나타난 직후에 실행됩니다.

- viewWillDisappear()  

  뷰가 사라지기 직전에 호출되는 함수이다. 변경을 수행하거나 첫 번째 응답자 상태를 종료하는 등의 정리 작업을 수행한다. 

- viewDidDisappear()  

  뷰가 사라진 직후에 호출된다.

**참고 : https://zeddios.tistory.com/43**

## segue 없이 코드로 화면 전환

```swift
// 이동할 뷰컨트롤러 객체를 스토리보드ID를 이용하여 참조
if let vc = self.storyboard?.instantiateViewController(withIdentifier: "greenView") {
  // 화면을 전환할 때 애니메이션 정의
  vc.modalTransitionStyle = UIModalTransitionStyle.coverVertical
            // coverVertical : 하단에서 위로 수직이동하며 등장
            // crossDissolve : 번인아웃되면서 화면 변경
            // partialCurl : 책넘김 효과로 화면 변경
            // flipHorizontal : 화면이 돌아가며 변경
            
  //인자값으로 받은 뷰 컨트롤러로 화면 이동
  self.present(vc, animated: true, completion: nil)
}
```

# step6. Container ViewController

> 뷰 컨트롤러는 자식 뷰 컨트롤러를 소유할 수 있다는 개념으로 **UINavigationController, UITabBarController, UISplitViewController, UIPageViewController** 가 컨테이너 뷰컨트롤러에 속한다.

네비게이션 컨트롤러를 연결하여 동작확인

네비게이션 컨트롤러의 자식 뷰 컨트롤러들은 일종의 스택처럼 관리되는데, 맨 처음 표시되는 뷰 컨트롤러를 **rootViewController**라 하고, 세부 항목으로 들어갈 때마다 다음 레벨의 뷰 컨트롤러를 push하고, 반대방향으로 빠져나올 땐 pop한다. 즉, 화면에 표시되는 뷰는 스택의 top에 해당하는 뷰 컨트롤러의 뷰가 된다.

참고 : https://soooprmx.com/archives/4496

<img width="998" src="https://user-images.githubusercontent.com/31604976/55055457-4f7e9600-50a6-11e9-9b61-dd7d1b9e833e.png">



<img width="1440" src="https://user-images.githubusercontent.com/31604976/55053072-5dc8b400-509e-11e9-8d5f-7d9c1c407c5e.png">

네비게이션 컨트롤러 사용 시 back 버튼이 생기고 기존의 dismiss close 버튼이 동작하지 않는다. 네비게이션 컨트롤러의 popViewController를 사용하면 동작한다.

```swift
@IBAction func closeButtonTouched(_ sender: UIButton) {
//        self.dismiss(animated: true, completion: nil)
        self.navigationController?.popViewController(animated: true)
    }
```



