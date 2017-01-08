---
layout: post
title:  "Elm Core Language And The Elm Architecture"
categories: Elm
---

[Core Language](https://guide.elm-lang.org/core_language.html)


## Functions with If Expressions

```
> over9000 powerLevel = \
|   if powerLevel > 9000 then "It's over 9000!!!" else "meh"
<function>

> over9000 42
"meh"

> over9000 100000
"It's over 9000!!!"
```

이 부분에서 고생을 했다. 정확하게 따라했어야 했는데, 
```
|   if powerLevel > 9000 then "It's over 9000!!!" else
```
if 앞에 공백을 빼먹고 했더니 자꾸 오류가 났다.
```
-- SYNTAX PROBLEM -------------------------------------------- repl-temp-000.elm

The = operator is reserved for defining variables. Maybe you want == instead? Or
maybe you are defining a variable, but there is whitespace before it?

3|   over a = 
            ^
Maybe <http://elm-lang.org/docs/syntax> can help you figure it out.
```
whitespace에 대한 언급이 있었는데, 제대로 읽지 않아서 고생을 했다. 0.18.0 버젼과 튜토리얼 버젼이 다른가 라고 생각을...어쨌든 공백을 주고하니까 function이 잘 생성됐다.

## Records
```
> jeong = { name = "Seokwon", age = 27 }
{ age = 27, name = "Seokwon" }
```
근데 이 부분에서 
```Jeong = { name = "Seokwon", age = 27 }``` 이런식으로 시작을 대문자로 했더니 오류가 발생했다.

```
-- SYNTAX PROBLEM -------------------------------------------- repl-temp-000.elm

I need whitespace, but got stuck on what looks like a new declaration. You are
either missing some stuff in the declaration above or just need to add some
spaces here:

4| t_s_o_l = ()
   ^
I am looking for one of the following things:

    whitespace
```
아직 정확하게 원인을 모르겠다.

## Comparing Records and Objects
JavaScript의 Object와 Elm의 Records는 차이가 존재한다.
- You cannot ask for a field that does not exist.
- No field will ever be undefined or null.
- You cannot create recursive records with a this or self keyword.


[The Elm Architecture](https://guide.elm-lang.org/core_language.html)

느릅 나무 ! Redux에도 영향을 줬다.
느릅 나무를 배워서 당장 어플리케이션에 적용할 수 없더라도, 많은 부분을 배울 수 있다!

## The Basic Pattern

- Model - 애플리케이션의 상태
- Update - 상태를 업데이트 하는 방법
- View - HTML같은 뷰


세 부분으로 나눌 수 있다.