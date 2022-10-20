---
title: Hello, Circuit Breaker
author: glshlee
date: 2021-01-27
categories: [spring]
tags: [spring, circuit breaker]
---

# 개요
https://www.baeldung.com/resilience4j

# status
CircuitBreaker는 3가지의 상태를 가질 수 있습니다.
CLOSED - 서비스가 잘 동작하고 있는 상태입니다.
OPEN - 원격 서버가 다운되어 모든 요청이 실패되고 있는 상태입니다.
HALF_OPEN - OPEN상태에서 얼마간의 시간이 지난 후 CircuitBreaker가 리모트 서버가 살아나는지 요청을 보내 체크해보고 있는 상태입니다.

A CircuitBreaker can be in one of the three states:

CLOSED – everything is fine, no short-circuiting involved
OPEN – remote server is down, all requests to it are short-circuited
HALF_OPEN – a configured amount of time since entering OPEN state has elapsed and CircuitBreaker allows requests to check if the remote service is back online
We can configure the following settings:

the failure rate threshold above which the CircuitBreaker opens and starts short-circuiting calls
the wait duration which defines how long the CircuitBreaker should stay open before it switches to half open
the size of the ring buffer when the CircuitBreaker is half open or closed
a custom CircuitBreakerEventListener which handles CircuitBreaker events
a custom Predicate which evaluates if an exception should count as a failure and thus increase the failure rate

# dependency
``` xml
<dependency>
    <groupId>io.github.resilience4j</groupId>
    <artifactId>resilience4j-circuitbreaker</artifactId>
    <version>0.12.1</version>
</dependency>
```

# Circuit Breaker 설정
|설정|기본값|설명|
|---|---|---|
| slidingWindowType | COUNT_BASED | 서킷에서 사용할 슬라이딩 윈도우 타입 설정 (카운트, 시간) |
| slidingWindowSize | 100 | 서킷 판단에 필요한 윈도우 크기 |
| minimumNumberOfCalls | 100 | 서킷 판단에 필요한 최소 요청 수 |
| waitDuraitionInOpenState | 60000 | 서킷 오픈 상태에서 하프오픈으로 변환될때 기다리는 시간 |
| failureRateThreshold | 50 | 실패 요청 threshold |
| permittedNumberOfCallsInHalfOpenState | 10 | 하프오픈 상태에서 테스트하는 요청 수 |
| recordExceptions | empty (all) | failure에 포함되는 예외 |
| ignoreExceptions | empty (no) | failure에 포함되지 않는 예외 |
| slowCallRateThreshold | 10 | slow 요청에 대한 threshold |
| slowCallDurationThreshold | 60000 | slow 요청 기준값 |