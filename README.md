# UsefulReferencelink


BaseFragment</br>
https://github.com/HYUNJUNEPARK/-Ref-AndroidUI/blob/main/3_ViewPager2_BottomNavigation/app/src/main/java/com/example/viewpager2_bottomnavigation/util/BaseFragment.kt </br>
-> **원하는 프래그먼트에 상속시킨 후 initView() 를 오버라이딩해 사용 (dataBinding 사용)**

```kotlin
//상속 예시
class AFragment : BaseFragment<FragmentABinding>(R.layout.fragment_a) {
    override fun initView() {
        super.initView()

        binding.apply {

        }
    }
}
```
<br></br>

Permission</br>
https://github.com/HYUNJUNEPARK/-Ref-AndoridProgramming/blob/main/5_Permission/app/src/main/java/com/june/permission/Permission.kt </br>
-> **권한 요청이 필요한 Activity/Fragment 에서 `Permission(context).checkPermissions()` 호출, override onRequestPermissionResult**

```kotlin
//override onRequestPermissionResult
override fun onRequestPermissionsResult(requestCode: Int, permissions: Array<out String>, grantResults: IntArray) {
    super.onRequestPermissionsResult(requestCode, permissions, grantResults)

    //result : true(0) 모든 권한 승인 / false(-1) 권한 중 하나라도 거절
    if (grantResults.all { result -> result == PackageManager.PERMISSION_GRANTED}) { //권한을 모두 승인 받았을 때
        Permission(this).permissionGranted()
    }
    else { //권한 승인이 하나라도 거절되었을 때 -> AlertDialog
        Permission(this).permissionDenied()
    }
}
```
<br></br>

NetworkConnection</br>
https://github.com/HYUNJUNEPARK/-Ref-AndoridProgramming/blob/main/8_NetworkConnection/app/src/main/java/com/example/networkstate/NetworkConnectionCheckModule.kt </br>
-> **Activity onCreate/onDestroy 에 register()/unregister() 해 사용 (생명주기에 맞게 호출해 사용)**

```kotlin
class MainActivity : AppCompatActivity() {
    private val networkCheck: NetworkConnectionCallback by lazy { NetworkConnectionCallback(this) }
    
    override fun onCreate(savedInstanceState: Bundle?) {
        //...
        networkCheck.register()
    }
    
    override fun onDestroy() {
        //...
        networkCheck.unregister()
    }
}    
```
<br></br>


AlertDialog Sample</br>

```
AlertDialog.Builder(context)
    .setTitle("권한 설정")
    .setMessage("권한 거절로 인해 일부기능이 제한됩니다.")
    .setPositiveButton("취소") { _, _ -> }
    .setNegativeButton("권한 설정하러 가기") { _, _ ->
        applicationInfo()
    }
    .create()
    .show()

```
<br></br>



AAR</br>
Library AAR 파일 생성</br>
https://cording-cossk3.tistory.com/156</br>

프로젝트 구조 대화상자를 사용하여 종속 항목 추가</br>
https://developer.android.com/studio/projects/android-library?hl=ko#psd-add-library-dependency</br>
cf).aar 파일을 Project/app/libs 에 복사</br>
-> File > Project Structure > Dependencies > Add Jar/Aar Dependency > Step 1 Provide a path to the library file or directory to add 'libs/aar파일명'</br>

<br></br>

---

액션바 뒤로가기 버튼</br>
https://programmingworld1.tistory.com/15

Status bar 색상 변경</br>
https://origogi.github.io/android/dark-mode/

커스텀다이얼로그 데이터 바인딩</br>
https://github.com/HYUNJUNEPARK/BasicAOSApp/blob/main/1_BMICalculator/app/src/main/java/com/june/androidApp/bmicalculator/ResultDialog.kt

[Android, 단축키] 내가 자주 사용하는 단축키 정리 for MAC</br>
https://black-jin0427.tistory.com/186</br>

파이어베이스 gradle 세팅 방법(gradle 7.x 이상)</br>
https://gift123.tistory.com/68</br>
https://developer.android.com/studio/releases/gradle-plugin?hl=ko#updating-plugin</br>
