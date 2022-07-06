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
