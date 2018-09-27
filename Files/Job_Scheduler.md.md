# Job Scheduler
- [Google Developer Link](https://developer.android.com/reference/android/app/job/JobScheduler)
- [Blog-kr](https://medium.com/til-kotlin-ko/android-o%EC%97%90%EC%84%9C%EC%9D%98-%EB%B0%B1%EA%B7%B8%EB%9D%BC%EC%9A%B4%EB%93%9C-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%9C%84%ED%95%9C-jobintentservice-250af2f7783c)

## 백그라운드 제한은?
안드로이드 O에서는 앱이 백그라운드에 진입하게 되면 몇분 뒤 동작 중인 백그라운드 서비스는 자동으로 중지되며 **onDestroy()**가 호출됩니다. 더하여 백그라운드 상태에서 서비스를 구동하기 위한 startService()의 호출은 **IllegalStateException**이 발생하며 허용되지 않는다.

## 암시적 브로드캐스트 제한
- 암시적 브로드캐스트 인텐트(Implicit Broadcast Intent)란 **특정 앱을 대상으로 하지 않는** 브로드캐스트 인텐트
- 안드로이드O 에서는 암시적 브로드캐스트 수신자를 등록 할 수 없도록 [제한](https://developer.android.com/about/versions/oreo/background#broadcasts)
#### 안드로이드N 상에서는 특정인텐트 동작을 제한
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3NDk5MjQ3MzBdfQ==
-->