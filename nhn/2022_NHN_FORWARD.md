# 📜NHN FORWARD 2022

[TOC]

## 📌클린 아키텍처 애매한 부분 정해 드립니다.

### 💡좋은 아키텍처를 구성하는 방법

> 패러다임, 설계 원칙(SOLID), 컴포넌트 응집성/결합 원칙 등을 지키는...
>
> 아키텍처 패턴 종류
> (Layered, Clean, Hexagonal)

#### Clean Architecture 란?

- 목표: 관심사 분리
- 규칙: 의존성의 방향은 안쪽(고수준)을 향한다.

- 중요도에 따라 계층을 나눈다.

#### Package

- 계층형 
  - 전통적인 수평적 계층화, 단순
  - Controller
  - Service 
  - Repository
- 기능 기반
  - 서로 연관된 기능, 도메인 개념에 따라 수직의 얇은 조각으로 나누나 계층 구조가 분리되지 않는다.
  - xDomain
    - Controller
    - Service
    - Repository
- 헥사고날(포트&어뎁터)
  - 수직/수평형 계층 구조의 장점, 다른 세부사항에 의존하지 않음, 클래스와 패키지 구조가 더 많아짐
  - adapter
    - in/web
    - out/persistence
  - application
    - port
      - in
        - usecase
      - out
        - port
    - service
  - domain



####  클린 아키텍처는 애매하다

- 규칙이 너무 단순하다.
  - 핵심 규칙 2가지 외에는 Case by case로 애매한 지점이 많다.
- 애매한 것을 판단할 기준
  - 의존성이 안쪽(고수준)으로 향하고 있는가?
  - 테스트하기 쉬운가?
  - ...

**1. JPA Entity와 Domain Entity 분리**

- 같이 사용할 경우 클래스/패키지 구조는 단순화 되지만 영속성 계층과 도메인 계층의 강결합,
- 업무규칙, 연관관계 매핑, 즉시/지연 로딩 등 고려해야한다.

**2. JPA Repository는 어디에?**

- JpaRepository는 어댑터에서 사용

**3. Usecase가 다른 Usecase를 호출해야 할 때?**

- 직접 호출해도 괜찮을 것 같다. (service가 service 레이어를 호출한다, 강결합 주의, 단방향 인지)

**4. 유스케이스를 꼭 인터페이스로 뽑아야하는가?**

- 뽑는게 좋다고 생각한다. (구현에 대해서 너무 많이 알지 못하도록 마기위한 존재, 인터페이스는 API 스펙같은 것)



### ETC.

- 책: 만들면서 배우는 클린 아키텍처 (헥사고날 아키텍처 따라하기 좋음) 