# App Life Cycle 앱의 생명 주기

## 앱의 생명주기

- 앱의 생명주기란, 앱 각각의 상태를 다섯 가지로 나누어 정의하는 말이라고 할 수 있겠다!
- 앱 하나를 실행하면, 그 앱을 제외한 나머지 앱들은 화면에 보이지 않는다. 
하지만 화면에 보이지 않더라도 실행 중인 앱이 있을 수 있음! 
예를 들어, 타이머 앱! 타이머를 켜 놓고 다른 앱을 실행해도 타이머 앱에서의 시간은 멈추지 않고 정해진 시간이 되면 알림을 준다.

### 다섯 가지 상태

- Active: 앱이 실행 중인 상태 (Foreground)
- Not Running: 앱이 시작되기 전
- Inactive: 앱이 화면에서 실행 중이지만, 어떤 신호도 받지 않는 상태 (Foreground)
    - 예를 들어, 전화가 오거나 알람이 울리면 화면 위를 덮을 때
- Background: 앱이 화면에 보이지 않지만 코드를 실행하고 있는 상태
- Suspend: 앱이 곧 종료될 상태

## 공식 문서 - 요약

앱의 현재 상태에 따라 할 수 있는 것과 없는 것이 결정됩니다. 예를 들어, foreground에 있는 앱은 유저가 사용하고 있는 것이므로 시스템 자원(예를 들어 CPU)에 우선순위를 가집니다. 반면, background에 있는 앱은 최대한 적은 일을 해야합니다. 앱의 상태가 바뀌면 그에 따라 앱의 행위도 바꾸어야 합니다.

앱의 상태가 바뀌면 UIKit은 적절한 delegate object의 메소드를 불러 알려줍니다.

- iOS 13와 그 이후로는 `UISceneDelegate` object를 사용 (scene-based 방식)
- iOS 12와 그 이전으로는 `UIApplicationDelegate` object를 사용 (app-based 방식)

## iOS 13 이상, Scene-based app

- UI를 Scene이 담당하며 멀티플 윈도우를 가능하게 해 주는 방식 - iPad OS
- Scene 전환을 이용해 다음과 같이 행동할 수 있다:
    - UIKit이 앱의 scene에 연결되었을 때, scene의 첫 UI와 scene에서 필요한 데이터를 준비한다.
    - Foreground-active 로 전환될 때, UI를 준비하고 유저와 상호작용할 준비를 한다.
    - Foreground-active 상태를 벗어날 때, 데이터를 저장하고 앱의 동작을 최소화한다.
    - Background 상태에 들어가면, 중요한 작업을 완료하고 가능한 한 많은 메모리를 확보하고, 앱 스냅샷을 준비한다.
    - scene과 연결이 끊어지면, 관련된 공유 리소스를 정리한다.
    - scene 관련 이벤트 외에도, `UIApplicationDelegate` 객체를 사용해 앱 실행에 응답해야 한다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/641c143b-9321-41be-8a55-9b3aad66d1ad/Untitled.png)

## iOS 12와 그 이전, App-based

iOS 12 및 이전 버전과 scene을 지원하지 않는 앱에서 UIKit은 모든 생명 주기 이벤트를 `UIApplicationDelegate` 객체에 제공한다. App delegate는 별도의 윈도우를 포함한 앱의 모든 창을 관리한다. 결과적으로, 앱 상태 전환은 외부 디스플레이의 콘텐츠를 포함한 앱의 전체 UI에 영향을 미친다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/183b9573-2db8-4b0a-856a-8f4b2f559d02/Untitled.png)

출처

- https://developer.apple.com/documentation/uikit/app_and_environment/managing_your_app_s_life_cycle
- 새싹 SeSAC 강의
