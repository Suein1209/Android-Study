# Job Scheduler
- [Google Developer Link](https://developer.android.com/reference/android/app/job/JobScheduler)
- [Blog-kr](https://medium.com/til-kotlin-ko/android-o%EC%97%90%EC%84%9C%EC%9D%98-%EB%B0%B1%EA%B7%B8%EB%9D%BC%EC%9A%B4%EB%93%9C-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%9C%84%ED%95%9C-jobintentservice-250af2f7783c)

## 백그라운드 제한은?
안드로이드 O에서는 앱이 백그라운드에 진입하게 되면 몇분 뒤 동작 중인 백그라운드 서비스는 자동으로 중지되며 **onDestroy()**가 호출됩니다. 더하여 백그라운드 상태에서 서비스를 구동하기 위한 startService()의 호출은 **IllegalStateException**이 발생하며 허용되지 않는다.

## 암시적 브로드캐스트 제한
- 암시적 브로드캐스트 인텐트(Implicit Broadcast Intent)란 **특정 앱을 대상으로 하지 않는** 브로드캐스트 인텐트
- 안드로이드O 에서는 암시적 브로드캐스트 수신자를 등록 할 수 없도록 [제한](https://developer.android.com/about/versions/oreo/background#broadcasts)
	- 안드로이드N 상에서는 특정 인텐트 동작을 [제한](https://developer.android.com/topic/performance/background-optimization) 하였다.
	- [필수 인텐트](https://developer.android.com/guide/components/broadcast-exceptions)는 제한하지 않는다.

## targetSDK ≥ 26
- [백그라운드 실행 제한](https://developer.android.com/preview/features/background.htl)은 target SDK가 Android O(API Level 26) 이상인 경우에 적용

## 가능한 작업들
- AndroidManifest.xml에 명시적(Explicit) 브로드캐스트는 등록이 가능하다.
- [Context.registerReceiver()](https://developer.android.com/reference/android/content/Context.html#registerReceiver%28android.content.BroadcastReceiver,%20android.content.IntentFilter%29)를 통해 리시버를 동적으로 등록할 수 있고 이렇게 등록된 리시버는 암시적 브로드캐스트 인텐트의 수신 제한에 해당되지 않는다.
- 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg1MTYwODA1LC00NDg3OTgzNzksLTE1Mj
U2MTE3NzEsNzQ4MjYzMDcyXX0=
-->