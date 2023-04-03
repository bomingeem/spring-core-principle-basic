### JPA

- Java Persistence API
- 자바 진영의 ORM 기술 표준

### ORM

- Object-relational mapping(객체 관계 매핑)
- 객체는 객체대로 설계
- 관계형 데이터베이스는 관계형 데이터베이스대로 설계
- ORM 프레임워크가 중간에서 매핑
- 대중적인 언어에는 대부분 ORM 기술이 존재

### JPA는 애플리케이션과 JDBD 사이에서 동작

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a875e402-5d51-4384-930d-9d05b1fb965d/Untitled.png)

### JPA 동작 - 저장

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0c5b059b-88b2-40b1-99a1-9a5833f2ed31/Untitled.png)

### JPA 동작 - 조회

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fdd08ee1-95b7-4992-a4d9-96d242fb256a/Untitled.png)

### JPA 소개

- EJB - 엔티티 빈(자바 표준) → 하이버네이트(오픈 소스) → JPA(자바 표준)

### JPA는 표준 명세

- JPA는 인터페이스의 모음
- JPA 2.1 표준 명세를 구현한 3가지 구현체
- 하이버네이트, EclipseLink, DataNucleus

### JPA를 왜 사용해야 하는가?

- SQL 중심적인 개발에서 객체 중심으로 개발
- 생산성
    - 저장: jpa.persist(member)
    - 조회: Member member = jpa.find(memberId)
    - 수정: member.setName(”변경할 이름”)
    - 삭제: jpa.remove(member)
- 유지보수
    - 기존: 필드 변경시 모든 SQL 수정
    - JPA: 필드만 추가하면 됨, SQL은 JPA가 처리
- 패러다임의 불일치 해결
    - JPA와 상속
    - JPA와 연관관계
    - JPA와 객체 그래프 탐색
    - JPA와 비교하기 - ‘동일한 트랜잭션’에서 조회한 엔티티는 같음을 보장
- 성능
    - 1차 캐시와 동일성(identity) 보장
        1. 같은 트랜잭션 안에서는 같은 엔티티를 반환 - 약간의 조회 성능 향상
        2. DB Isolation Level이 Read Commit이어도 애플리케이션에서 Repeatable Read 보장
    - 트랜잭션을 지원하는 쓰기 지연(transactional write-behind)

      **INSERT**

        1. 트랜잭션을 커밋할 때까지 INSERT SQL을 모음
        2. JDBC BATCH SQL 기능을 사용해서 한번에 SQL 전송

      **UPDATE**

        1. UPDATE, DELETE로 인한 로우락 시간 최소화
        2. 트랜잭션 커밋 시 UPDATE, DELETE SQL 실행하고, 바로 커밋
    - 지연 로딩(Lazy Loading)
        - 지연 로딩: 객체가 실제 사용될 때 로딩
        - 즉시 로딩: JOIN SQL로 한번에 연관된 객체까지 미리 조회
- 데이터 접근 추상화와 벤더 독립성
- 표준
