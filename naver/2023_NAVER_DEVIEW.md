# 📜NAVER DEVIEW 2023

[TOC]

## 📌네이버 스케일로 카프카 컨슈머 사용하기



### Kafka 란

- Log 자료구조를 분산 스토리지 형태로 만든 것
- Log (Topic), Pub/Sub 형태, 분할/복제 된, 
- Produce는 Thread safe 함, Consumer는 Thread safe 하지 않음



### Consumer 

#### Consumer Group

- 같은 `group.id` 설정값을 가진 Consumer들은 하나의 Consumer Group을 이룸
- 동일한 Consumer Group은 Topic에 속한 Partition을 나누어 읽음



#### Consumer Group Coordinator

- Consumer Group에 변화 (Consumer 또는 Partition의 증감)에 따른 Rebalance 판단
- Consumer Group Leader와 나머지 Consumer와 중개

> Consumer Coordination 기능을 택한 이유는 Broker를 재시작 할 필요 없이 더 유연하고 확장 가능한 파티션 할당을 지원하기 위해서



| 옵션                          | 설명                                                         |
| ----------------------------- | ------------------------------------------------------------ |
| max.poll.interval.ms          | Consumer가 Poll 메서드롤 호출하는데 허용하는 최대 시간       |
| heartbeat.interval.ms         | 컨슈머와 브로커 간 heartbeat를 주고받는 간격                 |
| session.timeout.ms            | heartbeat이 sesstion.timeout.ms 만큼 안오는것을 허용         |
| partition.assignment.strategy | 파티션 할당 방식 (ConsumerPartitionAssignor 구현체가 들어감) |



## 📌Colud 환경에서 Kafka Consumer 사용하기

- 단순 재시작 등으로 Partition Rebalance가 발생하는 현상을 방지하기 위해
  - group.instance.id(static-membership)를 명시 (컨슈머 인스턴스 별로 고유값 명시)



- Broker 설정 
  - broker.rack
    - 새로 생성된 replica가 서로 다른 rack에 할당되도록 하기 위한 설정



## 📌앞으로의 Kafka

- [Multi-level Rack Awareness](https://cwiki.apache.org/confluence/display/KAFKA/KIP-879%3A+Multi-level+Rack+Awareness)
- [Rack-aware Partition Assignment](https://cwiki.apache.org/confluence/display/KAFKA/KIP-881:+Rack-aware+Partition+Assignment+for+Kafka+Consumers)
- 