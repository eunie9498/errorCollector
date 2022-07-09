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
