# Architecture Decision Records

### Monorepo vs Multirepo 
- Monorepo를 선택하면 앱이랑 서버만 있으면 돼서 하나로 관리하기 편함

**-> Monorepo**

<br><br>
### 애플리케이션
주소록 애플리케이션 -> 모바일 vs 웹 
- 모바일이 전화기로서 기능이 있어서 활용도 높음
- 모바일로 메일 많이 보내는데 메일 전송에도 수신자 설정

**-> 모바일**
<br>
### 안드로이드 vs iOS vs Flutter
- 팀원들 다 안드로이드 경험이 있음
- 새로운 개발환경에 적응하고 언어(Swift, Dart)를 배울 시간/능력 여유 없음
- Flutter는 통합 개발환경을 지원한다는 장점이 있지만 사용하려면 Dart언어만 사용하는것이 아니라 Android면 Kotlin, iOS면 Swift도 사용해야하고, Github 이슈란에 가보면 엄청난 이슈가 올라와 있음

**-> 안드로이드**
<br>
### Java vs Kotlin
- 팀원들 다 자바로 안드로이드 개발 경험이 있음
- 코틀린을 사용하면 자바를 사용했을때보다 코드의 길이는 줄어 개발의 편의성은 증가하지만 사용할 줄 모른다.

**-> Java**
