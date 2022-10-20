---
title: Chirpy GitHub Action Trigger 안될 때
author: glshlee
date: 2021-01-07
categories: [github.io, tip]
tags: [blog, github, jekyll, chirpy]
---

# Chirpy theme GitHub Action trigger
github action을 트리거하기 위해서는 .github/workflows/pages-deploy.yml 에 적혀있는 트리거 조건이 맞아야 합니다.

처음 clone을 받으면 트리거 조건이 다음과 같이 적혀있습니다.
```
on:
  push:
    branches:
      - master
    paths-ignore:
      - .gitignore
      - README.md
      - LICENSE
```
main branch에 push했을 때 트리거가 되는것을 확인할 수 있습니다.

하지만 얼마전부터 github는 기본 branch를 master 대신 main으로 만들어주고 있습니다.

따라서 다음과 branch를 다음과 같이 변경해 줍니다.
```
on:
  push:
    branches:
      - main
    paths-ignore:
      - .gitignore
      - README.md
      - LICENSE
```