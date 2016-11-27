---
layout: post
title:  "I will be a hipster(Elmer)"
categories: Elm
---

JetBrains Night 서울에서 임백준님의 '프로그래밍 언어의 선택'이란 세션에서 Elm이란 언어에 대해서 들었다.

[Seven More Languages](https://pragprog.com/book/7lang/seven-more-languages-in-seven-weeks)란 책에서 소개가 됐다. 소개된 언어들로는 Factor, Lua, Elm, Elixir, Julia, miniKanren, Idris 이 있다.  

평소에 Web Frontend를 해보고 싶다는 생각이 많았다. 그래서 React를 할까, angular2를 할까 고민을 했는데, 겸사 겸사 힙스터가 될겸 Elm을 시작해 보려고 한다.

## Elm

  - 하스켈, ML 영향을 받은 정적 타입 체크 함수 언어
  - 불변성
  - 지속 데이터 구조
  - 모듈 시스템
  - 자바스크립트의 대안
  - 떠오르는 tech stack; Elm frontend + Elixir backend
  - pure functional code
  - [시간 여행 디버깅](http://debug.elm-lang.org/edit/Mario.elm)
    - 코드를 바꾸면 적용
    - 이벤트가 축적되어있고, 그걸로 변경할 수 있다.
  - [An Introduction to Elm](https://www.gitbook.com/book/evancz/an-introduction-to-elm)
    - > Elm is a functional language that compiles to JavaScript. It competes with projects like React as a tool for creating websites and web apps. Elm has a very strong emphasis on simplicity, ease-of-use, and quality tooling.


## Why Elm?

함수형 프로그래밍에 관심이 많다. 뭔가 멋있는 느낌적인 느낌!

## Start Elm

[Install](https://guide.elm-lang.org/install.html) - nodejs가 필요했다.

- ### In Terminal
터미널에서 elm-repl을 통해서 실행해 봤다.
<img src="/images/elm-terminal.png">

- ### [Try Elm In Online](http://elm-lang.org/try)
온라인에서 많은 샘플을 통해서 실습할 수 있다.

- ### In Editor
사용 가능한 Editor

  - Atom
  - Brackets
  - Emacs
  - IntelliJ
  - Light Table
  - Sublime Text
  - Vim
  - VS Code

  나는 Atom을 이용해서 했다. 간단하게 플러그인을 설치하고 하면 된다.
[Elm-Reactor](https://github.com/elm-lang/elm-reactor)를 통해서 간단하게 컴파일 할 수 있다.
받아서 root project에서 실행시킬 수 있다.
```bash
elm-reactor
```
http://localhost:8000에서 확인 할 수 있다.  
그리고 Atom혹은 Editor로 수정하고 새로고침하면 결과를 확인할 수 있다.

## Wow Elm

아직 잘 모르겠지만 앞으로 공식 홈페이지를 보면서 하나 하나 공부해 볼 예정입니다.
모두 Elm을 통해서 즐거움을 느끼시기를 바랍니다.
>I have put a huge emphasis on making Elm easy to learn and use, so all I ask is that you give Elm a shot and see what you think. I hope you will be pleasantly surprised!
