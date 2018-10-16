---
layout: post
title: "Playing with String and Data Binding in xml!"
categories: development
---

Playing with String and Data Binding in xml!

## 1. Use hard-coded text

hard-coded text를 이용할 수 있습니다.

```xml
    <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="@{`It is hard-coded.`}"/>
```

Result

    It is hard-coded.

## 2. Use string resource

strings.xml에 선언된 string을 이용할 수 있습니다.
```xml
    <string name="msg_hello_data_binding">Hello DataBinding!</string>
```
```xml
    <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="@{@string/msg_hello_data_binding}"/>
```
Result

    Hello DataBinding!

## 3. Use format string resource with hard-coded text

strings.xml에 선언된 format string을 이용할 수 있습니다.
```xml
    <string name="msg_hello_data_binding">%s, Hello DataBinding!</string>
```
```xml
    <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="@{@string/msg_hello_data_binding(`Seokwon`)}"/>
```
Result

    Seokwon, Hello DataBinding!

## 4. Use format string resource with string resource

물론 format string에 hard-coded뿐만 아니라 string resource도 사용할 수 있습니다.
```xml
    <string name="msg_hello_data_binding">%s, Hello DataBinding!</string>
    <string name="everybody">Everybody</string>
```
```xml
    <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="@{@string/msg_hello_data_binding(@string/everybody)}"/>
```
Result

    Everybody, Hello DataBinding!

## 5. Use format string resource with ternary operator `?:`(Feat hard-coded)

format string resource 에서 삼항 조건 연산자`?:`와 hard-coded text를 이용해서 표현할 수 있습니다.
```xml
    <string name="msg_hello_data_binding">%s, Hello DataBinding!</string>
```
```xml
    <data>
    	<variable
                name="isHelpful"
                type="Boolean"/>
    <data>
    
    <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="@{@string/msg_hello_data_binding(isHelpful ? `Gooood` : `Woo`)}"/>
```
Result

    Gooood, Hello DataBinding!
    or
    Woo, Hello DataBinding!

## 6. Use format string resource with ternary operator `?:`(Feat string resource)

format string resource 에서 삼항 조건 연산자`?:`와 string resource를 이용해서 표현할 수 있습니다.
```xml
    <string name="msg_hello_data_binding">%s, Hello DataBinding!</string>
    <string name="msg_good">Goooood</string>
    <string name="msg_bad">Wooooooooo</string>
```
```xml
    <data>
    	<variable
                name="isHelpful"
                type="Boolean"/>
    <data>
    
    <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="@{@string/msg_hello_data_binding(isHelpful ? @string/msg_good : @string/msg_bad)}"/>
```
Result

    Goooood, Hello DataBinding!
    or
    Wooooooooo, Hello DataBinding!

[Code](https://github.com/sangcomz/DatabindingExample) 보기