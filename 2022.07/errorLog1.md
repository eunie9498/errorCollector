### 패키지 변경 오류
> 발생일자 : 2022.07.06

<br>
패키지명을 변경하려다 생긴 오류<br>
<br>

#### 🔒 에러 메시지
```(kotlin)
 Caused by: org.gradle.api.GradleException: No matching client found for package name
```
<br>

#### 🔑 해결 방안
app/google.services.json 파일 속 `package_name` 변경
```(kotlin)
"client": [
    {
      "client_info": {
        ...
        "android_client_info": {
          "package_name": "패키지명"
        }
      }
      ...
```
<br><br>

### Manifest 미등록 오류
> 발생일자 : 2022.07.09

<br>
새로 생성한 Activity를 Manifest에 등록하지 않은 오류
<br><br>

#### 🔒 에러 메시지
```(kotlin)
android.content.ActivityNotFoundException: Unable to find explicit activity class; have you declared this activity in your AndroidManifest.xml?
```
<br>

#### 🔑 해결 방안
AndroidManifest.xml에 등록해줍니다
```(kotlin)
<activity android:name="패키지.액티비티명"
           android:exported="false"/>
```
여기서 `exported`는 다른앱에서 해당 Activity를 실행가능한지에 대한 boolean 값입니다 <br>
targetSdkVersion이 31이상이라면 필수로 포함해야합니다.

<br><Br>

### MpAndroidChart 연동 오류
```kotlin
Execution failed for task ':app:dataBindingMergeDependencyArtifactsDebug'.
> Could not resolve all files for configuration ':app:debugCompileClasspath'.
   > Could not find com.github.PhilJay:MPAndroidChart:v3.1.0.
     Required by:
         project :app
```
<br>

#### 🔑 해결 방안
settings.gradle에 아래항목 추가해야해요
```kotlin
maven {url 'https://jitpack.io'}
```
<br><br>

### API 통신 모델 Null문제
```kotlin
java.lang.IllegalArgumentException : Parameter specified as non-null is null
```

API 모델 중 null값이 내려오는 경우가 있는데, 무조건 값이 있는것으로 가정해서 나는 오류였습니다
<br>

#### 🔑 해결 방안
DTO에 nullable을 허용해줍니다
```kotlin
@Parcelize
data class Test(
  var title : String?=""
): Parcelable
```
