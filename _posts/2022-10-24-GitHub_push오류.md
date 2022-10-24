---
title: GitHub push 오류 해결
author: yaknman
date: 2022-10-24
categories: [GitHub]
tags: [blog, github]
---


# GitHub Push 오류

소스 수정사항을 push 하려는데 오류가 났었다.

오류 내용은
``` bash
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

push 전에 pull을 해서 repository 내용을 복사 후 재시도 해보라는 방법도 실패했었다.

삽질하다가 결국 내가 찾은 해결 방법은 이렇다.


``` bash
git branch (내 브런치명 확인)
git pull origin "브런치명" --allow-unrelated-histories (프로젝트 병합)
```

이후 push를 하니까 잘 됐다.

