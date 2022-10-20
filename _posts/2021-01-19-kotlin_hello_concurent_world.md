---
title: Hello, Concurrent World!
author: glshlee
date: 2021-01-19
categories: [kotlin]
tags: [kotlin, concurrent, coroutine]
---

# 개요
코틀린은 표준 라이브러리에 최소한의 저수준 API를 제공하여 다른 라이브러리가 코루틴을 사용할 수 있도록 합니다. 비슷한 기능을 제공하는 다른 언어들과는 다르게 코틀린은 `async`와 `await`가 기본 키워드가 아니며 표준 라이브러리에도 포함되지 않습니다.
코틀린의 컨셉인 `suspending function(일시 중단 함수)`은 비동기 연산에 대해 `future`와  `promise`보다 좀 더 안전하고 오류를 발생시키지 않는 추상화를 제공합니다.

`kotlinx.coroutines`는 JetBrains가 개발한 풍부한 기능을 제공하는 라이브러리입니다. 이 라이브러리는 `lunch`, `async` 및 기타 여러가지 고수준 코루틴을 지원하는 기본요소들이 포함되어 있습니다.

이제부터 살펴볼 예제에서 코루틴을 사용하기 위해서는 `kotlinx-coroutines-core` dependency의 추가가 필요합니다.

프로젝트의 빌드 툴에 따라 다음을 추가합니다. 

자세한 내용은 다음의 가이드에서 확인합니다.  [kotlinx.coroutines guide][1]

## maven
``` xml
<!-- coroutines dependency 추가 -->
<dependency>
    <groupId>org.jetbrains.kotlinx</groupId>
    <artifactId>kotlinx-coroutines-core</artifactId>
    <version>1.4.2</version>
</dependency>

<!-- kotlin 버전 확인 -->
<properties>
    <kotlin.version>1.4.0</kotlin.version>
</properties>

<!-- jcenter repository 추가 -->
<profiles>
    <profile>
        <repositories>
            <repository>
                <snapshots>
                    <enabled>false</enabled>
                </snapshots>
                <id>central</id>
                <name>bintray</name>
                <url>https://jcenter.bintray.com</url>
            </repository>
        </repositories>
        <pluginRepositories>
            <pluginRepository>
                <snapshots>
                    <enabled>false</enabled>
                </snapshots>
                <id>central</id>
                <name>bintray-plugins</name>
                <url>https://jcenter.bintray.com</url>
            </pluginRepository>
        </pluginRepositories>
        <id>bintray</id>
    </profile>
</profiles>
<activeProfiles>
    <activeProfile>bintray</activeProfile>
</activeProfiles>
```

## Gradle
``` gradle
// coroutines dependency 추가
dependencies {
    implementation 'org.jetbrains.kotlinx:kotlinx-coroutines-core:1.4.2'
}

// kotlin 버전 확인
buildscript {
    ext.kotlin_version = '1.4.0'
}

// jcenter repository 추가
repositories {
    jcenter()
}
        
```

## Gradle Kotlin DSL
``` gradle
// coroutines dependency 추가
dependencies {
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-core:1.4.2")
}

// kotlin 버전 확인
plugins {
    kotlin("jvm") version "1.4.0"
}

// jcenter repository 추가
repositories {
    jcenter()
}
```

[1]: https://github.com/kotlin/kotlinx.coroutines/blob/master/README.md#using-in-your-projects