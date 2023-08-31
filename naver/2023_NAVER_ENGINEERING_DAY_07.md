# NAVER ENGINEERING DAY(7월)

## Reactor Operator 파헤치기

> 내용출처: https://d2.naver.com/helloworld/3158221



### 유용한 Operator

#### flatMap

- Element 를 통해 inner flux를 새로 구독한다.

#### map

- 단순히 동기적인 mapper function을 통해 element를 다른 값으로 변환한다.

#### doOnNext

- element에 대해 side effect를 적용한다.
- side effect 효과를 먼저 적용하고, element를 그대로 downstream에 방출한다.
- 로깅할때 주로 사용된다.

#### filter

- element에 predicate을 적용해 true인 경우에만 downstream으로 방출한다.
- 

#### switchIfEmpty

- filter는 empty 퍼블리셔 문제가 있을 수 있다.
- 이런경우 기본값을 지정할 수 있는 defaultIfEmpty, switchIfEmpty 같은것을 사용하면 된다.

#### filterWhen

- inner 퍼블리셔의 반환하는 boolean 값으로 filter를 적용하는 오퍼레이터이다.

#### zip

- 동시에 여러 reactive 오퍼레이터를 호출하고 싶을때 사용한다.
- 여러 오퍼레이터를 동시에 구독한 후 tuple로 합쳐서 반환한다.

#### zipWhen

- 한 mono가 다른 mono에 종속적일 때 사용하면 된다.
- 한 mono의 결과물로 다른 mono의 결과물을 만들고 두 mono 모두 필요한 경우 사용한다.
- downstream 에서 tuple로 합쳐진 것을 다시 꺼내는 작업이 필요하다.
  - io.projectreactor.addons:reactor-extra
  - TupleUtils.function() 을 사용하면 컨슈머 람다로 바로 사용가능하다.

#### delayUntil

- doOnNext는 synchronous 한 side effect를 적용하는 반면에 reactive 한 side effoect를 적용시켜준다.
- flux의 delayUntil은 사용 주의
  - 첫 element의 inner 퍼블리셔가 complete 시그널을 보낸 이후에야 flux의 다음 엘리먼트에서 inner 퍼블리셔가 구독을 한다.

#### xxxDelayError



### Example

