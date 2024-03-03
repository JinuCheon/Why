# Instant 타입 (vs LocalDateTime)

## Instant 타입
``` java
Instant now = Instant.now();
```

- 인간보다는 기계에 친화적인 표기 방법
- Instant 는 항상 UTC(+00:00)를 기준으로 작동
- Instant 는 Timestemp 를 기반으로 만들었다.
  - 1970년 1월 1일 UTC의 첫 번째 순간 이후의 현재 시간까지의 나노초를 나타낸 값
  - Unix Timestemp 의 문제점을 해결했다
  - toString() 을 재정의하여 DateTimeFormatter 로 읽기 쉽게 해준 것이다.

### Unix Timestemp 란?

- long 타입 기반
  - 정렬 / 연산등에서 다른 타입들보다는 빠른 속도를 자랑합니다.

### Unix Timestemp 의 문제점
- 2038년에 bit overflow 가 발생할 예쩡
- https://en.wikipedia.org/wiki/Year_2038_problem

Java Time에서 `Local` 이 들어간다는것은 시간대(Zone Offset/Zone Region)에 대한 정보가 없다는 의미입니다. like LocalDateTime

다른나라에서 하는 이벤트 시간을 맞추기 위해서는 반드시 `OffsetDateTime`, `ZonedDateTime을` 사용해야함. 

## LocalDate, LocalTime, LocalDateTime
- Instant와 달리 인간이 읽을 수 있는 시간을 표시
- **로컬 pc의 날짜와 시간을 반환**

## ZonedDateTime
- LocalDateTime에 시간대를 추가하면 ZoneDateTime

## 글로벌 서비스
- 글로벌 서비스일 경우 LocalDateTime보다는 Instant나 ZonedDateTime 을 사용
- UTC 기반으로 DB에 넣어주고 Timezone 기반으로 보여주기

### Reference
https://velog.io/@lsb156/Instant-vs-LocalDateTime
https://sujl95.tistory.com/85