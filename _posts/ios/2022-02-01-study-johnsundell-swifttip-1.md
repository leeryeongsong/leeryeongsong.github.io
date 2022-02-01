---
title: "JohnSundell/SwiftTips #1 Namespacing with nested types에 대해 알아보자"
excerpt: "namespace, nested type에 대해 조사"
toc: true
toc_sticky: true
categories:
  - iOS
tags:
  - namespace
  - ios
  - nestedtype
  - 구조체
  - 열거형
  - 클래스
---

[JohnSundell/SwiftTips](https://github.com/JohnSundell/SwiftTips)의 \#1 Namespacing with nested types를 번역하고 관련 내용을 공부해보자.  

# 중첩 타입(Nested Type)으로 Namespace하기  
저는 스위프트의 nested types(중첩 타입)의 열렬한 팬이 되었습니다.  
스위프트가 제공하는 추가적인 namespace를 좋아하세요!  

'''
public struct Map { //Map이라는 구조체로 열거형 Direction, 구조체 Position, 열거형 Size 묶어주기
public struct Model { 
public let size: Size
public let theme: Theme
public var terrain: [Position : Terrain.Model]
public var units: [Position : Unit.Model]
public var buildings: [Position : Building.Model]
}

public enum Direction { //열거형
    case up
    case right
    case down
    case left
}

public struct Position { //구조체
    public var x: Int
    public var y: Int
}

public enum Size: String { //열거형
    case small = "S"
    case medium = "M"
    case large = "L"
    case extraLarge = "XL"
}
}
'''

# namespace란?

namespace(네임스페이스, 이름 공간) : 함수, 상수, 클래스 등의 이름이 중복되어 충돌하는 것을 막기 위해 고안된 수단.  
대형 프로젝트에서 다양한 라이브러리를 사용할 때, 개발자 여러 명이 같이 작업할 때 함수 등의 이름이 겹치는 문제가 생기기 쉽다.  

> namespace : 개체를 구분할 수 있는 범위를 나타내는 말로 일반적으로 하나의 이름 공간에서는 하나의 이름이 단 하나의 개체만을 가리키게 된다.  
[위키백과](https://ko.wikipedia.org/wiki/%EC%9D%B4%EB%A6%84%EA%B3%B5%EA%B0%84)

namespace의 필요성과 사용방법에 대해 쉽게 소개한 글을 읽고 싶으면, 다음 링크를 참고하기 -> [namespace의 장점과 사용법](https://bourne.tistory.com/18)


# Swift에서 namespace를 사용하는 방법

Swift에서는 namespace를 지원하지 않는다.  
→ 대신, 중첩 타입(Nested Type) 이용하기  

관련 글  
[cocoacasts - namespaces in swift](https://cocoacasts.com/namespaces-in-swift)  
위 글의 번역글  
[[Swift] Namespace 네임스페이스 란? (Struct, Enum 활용)](https://onelife2live.tistory.com/15)  


# 중첩 타입(Nested Type)이란?
중첩 타입 : 열거형, 클래스, 구조체를 중첩하여 사용할 수 있다.  
예) 구조체 안에 구조체 정의하기. 열거형 안에 구조체 정의하기 등..  

- enum 키워드를 사용해 열거형을 선언.  
- class 키워드로 클래스를 선언.  
- struct 키워드로 구조체를 선언.  

- 열거형, 클래스와 구조체에 대해 알려면 다음 링크 참고하기  
[The Swift Language Guide(한국어) - 열거형 (Enumerations)](https://jusung.gitbook.io/the-swift-language-guide/language-guide/08-enumerations)  
[The Swift Language Guide(한국어) - 클래스과 구조체 (Classes and Structures)](https://jusung.gitbook.io/the-swift-language-guide/language-guide/09-classes-and-structures)  



# struct 구조체 안에 class 클래스를 선언한다면?
→ struct이기 때문에 인스턴스로 만들 수 있는 문제 발생


# 해결 1. struct 안에 private init() {} 문구 추가하기

→ 구조체의 초기화를 private로 선언  

'''
struct NameSpace {
  private init() {}
  static let ~~
}
'''

# 해결 2. case가 없는 enum 사용하기.

→ 인스턴스화 막을 수 있고..namespace로만 작동 가능하다고 함  

'''
enum NameSpace {
  static let ~~
}

→but... 이것도 만능은 아니라고 하는 듯..  

[forums.swift - an enum based approach to namespaces](https://forums.swift.org/t/an-enum-based-approach-to-namespaces/12487/5)

[Swift Korea Meet 발표 - Swift의 네임스페이스와 typealias](https://academy.realm.io/kr/posts/swift-namespace-typealias/)




앞으로 읽어보면 좋을 글  

[[Swift] static과 class method, property 효과적으로 사용하기](https://sujinnaljin.medium.com/swift-static%EA%B3%BC-class-method-property-%ED%9A%A8%EA%B3%BC%EC%A0%81%EC%9C%BC%EB%A1%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0-b336311a923c)
