# Architecture Decision Records

<br>

## Management

### `Monorepo`/Multirepo 
- 앱이랑 서버만 있기 때문에 하나의 레포로도 관리하기 편함

### 데이터 저장방식
- 기본 연락처의 API를 활용해서 기존 연락처와 연동
- 로컬: RDB에 태그 목록과 그 태그를 가지는 연락처 목록 저장
- 클라우드: 백업, 동기화

<br>

## Front-end

### Mobile Application
- 주소록 애플리케이션 -> `Application` vs Web service
- 모바일이 전화기로서 기능이 있어서 활용도 높음
- 모바일로 메일 많이 보내는데 메일 전송에도 수신자 설정하기 편함
- 기존 주소록과 연동은 모바일에서만 가능함

### OS(Environment): `Android` vs iOS vs Flutter
- 팀원들 다 안드로이드 개발 경험이 있음
- 새로운 개발환경에 적응하고 언어(Swift, Dart)를 배울 시간/능력 여유 없음
- Flutter는 통합 개발환경을 지원한다는 장점이 있지만 사용하려면 Dart언어만 사용하는것이 아니라 Android면 Kotlin, iOS면 Swift도 사용해야하고, Github 이슈란에 가보면 엄청난 이슈가 올라와 있음

### Android SDK
- `minSdkVersion` : 16
- `targetSdkVersion` : 30

### Local DB: `Room` vs Realm
- Realm은 NoSQL라서, id 기반으로 구조화된 태그 정보를 저장하는 데에는 SQLite추상화 API인 Room이 더 적합함
    
### Language: `Java 11` vs Kotlin
- 팀원들 다 자바로 안드로이드 개발 경험이 있음
- 코틀린을 사용하면 자바를 사용했을때보다 코드의 길이는 줄어 개발의 편의성은 증가하지만 사용할 줄 모름
- Android Gradle 플러그인 4.0.0 이상을 사용하면 Android 플랫폼의 모든 버전에서 Java 8+ API 사용 가능

<br>

## Back-end
- 필요성: 클라우드 백업, 동기화

### Framework: `Spring Boot` vs Django
- Spring Boot는 국내 주류 프레임워크로서 자료가 훨씬 풍부해서 더 효율적으로 학습할 수 있음
- 반면 Django는 한글로 된 자료 찾기가 비교적 어렵고, 이미 만들어진 라이브러리를 활용하는 경우가 많이 때문에 커스텀이 어려움
- 팀원 중 한 명이 Spring Boot를 사용해본 경험이 있어서 문제를 좀 더 빠르게 해결할 수 있음
- 가장 최신 버전인 2.5 사용
- `Spring Cloud`: 클라우드 연동 시 활용
- `Spring (Cloud) Security` : 사용자 인증 시 활용
- DB연동 필요

### Build: `Gradle` vs Maven
- Gradle이 간결함, 가독성, 성능면에서 우위

### Language: `Java 11` vs Python
- Spring Boot는 Java 기반 프레임워크

### Hosting: `AWS` vs Heroku vs 네이버클라우드 vs Local
- 여분의 컴퓨팅 기기가 없어서 Local에서 서버를 돌릴 수 없으므로 클라우드 서비스를 사용해야 함
- Heroku는 PaaS(Platform as a Service)로서, 간단한 `git push` 작업만으로도 어플리케이션을 배포할 수 있음. 하지만 모든 복잡한 작업을 대신 해주는 만큼 비용이 더 비싸고, PostgreSQL이 기본 DB라 MySQL을 사용하기 번거로움
- AWS는 IaaS(Infrastructure as a Service)로서, 컴퓨팅 리소스만 클라우드 형태로 제공해주고, 나머지 DB, SW 등을 어플리케이션 배포와 함께 구축해야 함. 하지만 12개월 무료임
- 네이버 클라우드는 IaaS이지만, 유료라서 후보에서 제외
- 대부분의 기업들은 AWS를 사용하기 때문에 공부할 필요를 느낌

<br>

## DB

### `RDB` vs NoSQL
- 주소록은 딱 정해진 하나의 스키마로 데이터가 관리됨
- 특히 태그에 따라서 데이터를 탐색, 관리해야 함
- RDB가 NoSQL보다 데이터의 정렬과 분류, 탐색 속도가 빠름
- NoSQL은 정형화된 스키마 없이 데이터를 저장하기 때문에 일정한 스키마에 따라 관리되는 RDB가 더 적합함

### DBMS: `MySQL` vs Oracle
- MySQL이 Oracle보다 더 가볍고 오버 헤드도 작음
- Oracle은 대용량 DB에 적합한 고성능, 안정적 기능을 다양하게 제공하지만, 유료라는 치명적인 한계가 있음
- 간단한 데이터 트랜잭션을 위해서는 MySQL이 더 적합함
