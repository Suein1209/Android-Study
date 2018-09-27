# About Android
## [안드로이드 버전별 백그라운드 정책](https://www.charlezz.com/?p=737)
### Play Store 정책
arget API는 현재 출시된 Android 버전보다 1년 이상 오래되지 않아야 한다.
### 정책 변천사
-   롤리팝 5.0 :  [Job Scheduler](https://developer.android.com/reference/android/app/job/JobScheduler)의 등장. 작업을 미루거나 스케쥴링 할 수 있도록 함.
-   마시멜로우 6.0 :  [도즈 모드 및 앱 대기모드](https://developer.android.com/about/versions/marshmallow/android-6.0-changes#behavior-power)  등장. 디바이스 또는 앱이 장시간 사용중이 아닐 때, 네트워크의 액세스를 제한하고 백그라운드 작업을 유예하기 시작.
-   누가 7.0 :  [개선된 도즈모드](https://developer.android.com/about/versions/nougat/android-7.0-changes#doze). 화면이 꺼지고 움직이지 않을때 도즈모드의 하위제약조건이 적용되기 시작.
-   오레오 8.0 :  [백그라운드 제약](https://developer.android.com/about/versions/oreo/android-8.0-changes#back-all), 백그라운드 서비스와 위치 갱신을 제약하기 시작. 사실상 여기부터 아이폰화..
-   파이 9.0 :  [앱 대기 버킷](https://developer.android.com/about/versions/pie/power#buckets), [배터리 세이버 개선](https://developer.android.com/about/versions/pie/power#battery-saver)
 
# Google Android Development
## Job Scheduler
- [Google Developer Link](https://developer.android.com/reference/android/app/job/JobScheduler)
- [Blog-kr](https://medium.com/til-kotlin-ko/android-o%EC%97%90%EC%84%9C%EC%9D%98-%EB%B0%B1%EA%B7%B8%EB%9D%BC%EC%9A%B4%EB%93%9C-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%9C%84%ED%95%9C-jobintentservice-250af2f7783c)
-
안드로이드 O에서는 앱이 백그라운드에 진입하게 되면 몇분 뒤 동작 중인 백그라운드 서비스는 자동으로 중지되며 onDestroy()가 호출됩니다. 더하여 백그라운드 상태에서 서비스를 구동하기 위한 startService()의 호출은 IllegalStateException이 발생하며 허용되지 않습니다.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNTA1OTczOTgsLTEwMTc0MzM1NDgsLT
QyODg1ODEzNSw0ODEyMzI3MThdfQ==
-->