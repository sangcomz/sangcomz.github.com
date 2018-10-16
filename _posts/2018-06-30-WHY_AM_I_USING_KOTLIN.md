---
layout: post
title:  "Why am I using Kotlin?"
categories: Kotlin
---

2016년 초부터 kotlin으로 개발을 했다. "근데 왜 코틀린을 써?" 라고 하면 잘 대답을 못했다. 
그래서 나는 왜 코틀린을 사용하고, 왜 코들린이 좋다고 생각하는지 정리해보자.

# 코틀린이란?

> 코틀린(kotlin)은 자바 플랫폼에서 돌아가는 새로운 프로그래밍 언어다.

# 내가 코틀린을 사용하는 이유?

## 안전한 프로그래밍!

### Nullable type 지원
Nullable Type지원은 안전한 개발을 할 수 있도록 도와준다. 자바의 경우 Null 체크를 하지 못해서 죽는 경우가 있다. 하지만 코틀린은 변수를 처음 선언할때부터 null이 들어갈 변수인지 선언할 수 있다. 그래서 그 변수를 사용할땐 무조건 null을 체크해줘야한다. 

```kotlin
  //선언
  val x = null // Error
  var y = null // ok
  
  //사용
  y?.let{
    it.something()
  }
  
  y?.something()
```

## 보기 좋다!
- 객체와 컬렉션을 함수형 스타일로 다룰 수 있는 API를 제공한다.
- [Elvis Operrator](https://kotlinlang.org/docs/reference/null-safety.html#elvis-operator)를 제공한다.
- Google for Mobile I/O RECAP 2018 - Kotlin으로 코딩 시작하기 세선에서 본 [DSL](https://proandroiddev.com/writing-dsls-in-kotlin-part-1-7f5d2193f277)도 잘 쓰면 좋을것같다.
```kotlin
  // API 제공
   val list: List<User> = arrayListOf()
   
   list
        .sortedBy { it.age }
        .find { it.name == "Tom" }
        
  
  val name = value ?: "UNNAME" //Elvis Operrator
```

## Extension Functions!
좋은 예인지는 모르겠지만 이런식으로 사용할 수 있다.

```kotlin
  fun List<User>.sortAndToString(): List<String> = this.sortedBy { it.age }
        .map {
            "name : ${it.name} age : ${it.age}"
        }
```

[공식 문서]((https://kotlinlang.org/docs/reference/extensions.html))를 확인해보세요!

## 풀스택의 길로 갈 수 있다!!
Kotlin을 이용해서 Android, Web Backend, Web Frontend, Native등 모든 분야에서 사용할 수 있다. 개인적으론 웹쪽 서버와 프론트엔드 개발을 해보고 있다.


이것 말고도 이유가 있을것같다. 생각나는대로 정리해야겠다.

