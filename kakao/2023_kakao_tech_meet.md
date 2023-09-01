# 2023 Kakao Tech Meet

## Spring Batch 애플리케이션 성능 향상을 위한 주요 팁

> 영상링크: https://www.youtube.com/watch?v=VSwWHHkdQI4

#### 간략 소개

- JobLanucher, Job, Step
- JobRepository
- ItemReader, ItemProcessor, ItemWriter
- Chunk 프로세싱

#### 성능 최적화 과정

- ItemProcessor 느린 원인
  - I/O 작업 (Chunk size 만큼의 작업) 
- 최적화 방안
  - Network I/O → 멀티 스레드 기반 처리
  - Database I/O → IN 절 기반 최소화
- 등급별 포인트 추가
  - 각 유저의 포인트를 업데이트 하려면 다시 개별적 업데이트가 발생한다. → JDBC Execute Batch 사용 (쿼리를 붂어서 한번에 DB에 전송)







## Java App Server Refactoring 후기

> 영상링크: https://www.youtube.com/watch?v=ESwYltg47Yw

#### 가변 Context 클래스는 신중히 사용하자

1. 함수가 Context 객체를 업데이트 할 목적으로 Context 객체를 받지 말고, 리턴으로 처리하자
2. 함수에서 값을 받을 때 편하다고 Context 객체를 받지 말고, 필요한 것만 명시적으로 받자



#### 고차 함수로 의존성 줄이기

1. 순환 의존성
2. 리팩터링으로 의존성 분리
3. 단위 테스트 구성
4. JShell에서 코드 조각 테스트
5. 간단한 성능 차이 확인



#### 코드 복잡도 줄이기 (Cyclomatic Complexity, NPath Complexity)

1. 코드 복잡도
2. 함수 추출하기
3. 중첩 조건문을 보호 구문으로 바꾸기