# Job Scheduler
- [Google Developer Link](https://developer.android.com/reference/android/app/job/JobScheduler)
- [Android O에서의 백그라운드 처리를 위한 JobIntentService](https://medium.com/til-kotlin-ko/android-o%EC%97%90%EC%84%9C%EC%9D%98-%EB%B0%B1%EA%B7%B8%EB%9D%BC%EC%9A%B4%EB%93%9C-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%9C%84%ED%95%9C-jobintentservice-250af2f7783c)
- [JobScheduler를 사용해서 최적화하기](http://blog.naver.com/horajjan/220854102354)
- [JobScheduler #1](http://tourspace.tistory.com/38),  [JobScheduler #2](http://tourspace.tistory.com/39)

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

## JobScheduler?
- 안드로이드 롤리팝에서는 Project Volta와 함께 백그라운드 동작을 최적화하기 위한 일환으로 JobScheduler를 소개
- 작업에 **필요한 조건 및 인자들**([JobInfo](https://developer.android.com/reference/android/app/job/JobInfo))과 **해당 조건의 동작**([JobService](https://developer.android.com/reference/android/app/job/JobService))을 등록하고, 안드로이드 프레임워크에 의해 적정한 실행 시점이 제어되는 백그라운드 실행 기능

## Job 구현 구성
1.  `JobInfo`를 통해 Job이 실행될 조건을 설정하고,  `JobScheduler`를 통해 이를 시스템에 등록합니다.
2.  `JobService`를 상속받아 Job 실행 시 필요한 동작을 구현합니다.
3.  Job 실행을 위한 권한(`android.permission.BIND_JOB_SERVICE`)를 등록합니다.

## 실행 조건의 설정과 등록
[JobInfo](https://developer.android.com/reference/android/app/job/JobInfo)는 네트워크의 연결 상태나 충전 여부, 디바이스의 유휴 시점 등 [JobService](https://developer.android.com/reference/android/app/job/JobService)가 실행되어야 하는 조건을 관리합니다. 설정 가능한 동작 조건은 다음과 같습니다
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTMxODU2NjU4NiwxOTI1OTA3ODksLTQ0OD
c5ODM3OSwtMTUyNTYxMTc3MSw3NDgyNjMwNzJdfQ==
-->