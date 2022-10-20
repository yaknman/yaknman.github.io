---
title: Spring REST Docs
author: glshlee
date: 2021-01-15
categories: [spring, docs]
tags: [java, spring, restDocs]
---

## Spring REST Docs
Spring REST Docs의 주요 목적은 [Asciidoctor][1]를 사용하여 작성한 문서를 [Spring MVC Test][2]로 자동 생성된 코드와 결합하여 RESTful 서비스를 정확하고 가독성이 높도록 쉽게 문서화 하는 것입니다.

> `Asciidoctor`는 텍스트를 이용해 HTML로 생성해주는 도구입니다.

Spring REST Docs는 test를 이용해 snippet들을 만들어 냅니다.
Test는 아래의 방법으로 작성되어야 합니다.
* Srping MVC의 [test framework][4]
* WebFlux의 [WebTestClient][5] 또는 [REST Assured 3][6]

이런 test-driven 접근은 문서의 정확도를 보장하는데 도움이 됩니다. 왜냐하면 만약에 snippet이 잘못됐다면 테스트가 실패할 것이기 때문이지요.

RESTful service의 문서를 만드는데 중요한 것은 주로 어떤 HTTP requests를 처리할 수 있는지와 그에 대해 어떤 HTTP responses를 만들어내는지 입니다. Spring REST Docs는 내부적인 서비스 구현을 감추고 HTTP request, response를 사용하여 문서를 생성할 수 있습니다. 이런 구조는 문서의 재작업 없이 내부 구현을 향상시키는데 도움을 줍니다.

## 제약 사항
Java 8이나 그 이후 버전이 필요하며 [Gradle][3]을 사용합니다.

## Config
Spring boot는 Test에 Spring REST Docs를 활용하기 위해서 `@AutoConfigureRestDocs` annotation을 제공합니다.

// TODO..

[1]: https://asciidoctor.org
[2]: https://docs.spring.io/spring-framework/docs/4.1.x/spring-framework-reference/htmlsingle/#spring-mvc-test-framework
[3]: https://gradle.org/
[4]: https://docs.spring.io/spring-framework/docs/5.0.x/spring-framework-reference/testing.html#spring-mvc-test-framework
[5]: https://docs.spring.io/spring-framework/docs/5.0.x/spring-framework-reference/testing.html#webtestclient
[6]: https://rest-assured.io/
