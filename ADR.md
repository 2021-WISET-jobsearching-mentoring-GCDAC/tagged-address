# Architecture Decision Records

## Back-end

### Framework: `Spring Boot`/Django
- Spring Boot는 국내 주류 프레임워크로서 자료가 훨씬 풍부해서 더 효율적으로 학습할 수 있음
- 반면 Django는 한글로 된 자료 찾기가 비교적 어렵고, 이미 만들어진 라이브러리를 활용하는 경우가 많이 때문에 커스텀이 어려움
- 팀원 중 한 명이 Spring Boot를 사용해본 경험이 있어서 문제를 좀 더 빠르게 해결할 수 있음

### Language: `Java`/Python
- Spring Boot는 Java 기반 프레임워크

### Hosting: `AWS`/Heroku/네이버클라우드/Local
- 여분의 컴퓨팅 기기가 없어서 Local에서 서버를 돌릴 수 없으므로 클라우드 서비스를 사용해야 함
- Heroku는 PaaS(Platform as a Service)로서, 간단한 `git push` 작업만으로도 어플리케이션을 배포할 수 있음. 하지만 모든 복잡한 작업을 대신 해주는 만큼 비용이 더 비싸고, PostgreSQL이 기본 DB라 MySQL을 사용하기 번거로움
- AWS는 IaaS(Infrastructure as a Service)로서, 컴퓨팅 리소스만 클라우드 형태로 제공해주고, 나머지 DB, SW 등을 어플리케이션 배포와 함께 구축해야 함. 하지만 12개월 무료임
- 네이버 클라우드는 IaaS이지만, 유료라서 후보에서 제외
- 대부분의 기업들은 AWS를 사용하기 때문에 공부할 필요를 느낌

<br>

## DB

### `RDB`/NoSQL
- 주소록은 딱 정해진 하나의 스키마로 데이터가 관리됨
- 특히 태그에 따라서 데이터를 탐색, 관리해야 함
- RDB가 NoSQL보다 데이터의 정렬과 분류, 탐색 속도가 빠름
- NoSQL은 정형화된 스키마 없이 데이터를 저장하기 때문에 일정한 스키마에 따라 관리되는 RDB가 더 적합함

### DBMS: `MySQL`/Oracle
- MySQL이 Oracle보다 더 가볍고 오버 헤드도 작음
- Oracle은 대용량 DB에 적합한 고성능, 안정적 기능을 다양하게 제공하지만, 유료라는 치명적인 한계가 있음
- 간단한 데이터 트랜잭션을 위해서는 MySQL이 더 적합함
