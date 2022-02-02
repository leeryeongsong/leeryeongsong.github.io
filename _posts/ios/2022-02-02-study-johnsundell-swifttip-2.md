---
title: "JohnSundell/SwiftTips #2 Using auto closures에 대해 알아보자"
excerpt: "closeures, autoclosures에 대해 조사"
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

[JohnSundell/SwiftTips](https://github.com/JohnSundell/SwiftTips)의 \#2 Using auto closures를 번역하고 관련 내용을 공부해보자.  

# auto closures를 사용하기
스위프트에서 auto closures 사용 용도들을 더 많이 찾고 있다. 다음과 같이 꽤 괜찮은 APIs를 사용할 수 있다. 

```
extension Dictionary {
    mutating func value(for key: Key, orAdd valueClosure: @autoclosure () -> Value) -> Value {
        if let value = self[key] {
            return value
        }
        
        let value = valueClosure()
        self[key] = value
        return value
    }
}
```

# 앞으로 읽으면 좋을 글

auto closures에 대해 잘 이해하려면 closures에 대해 먼저 공부하는 것이 좋다.  
closures 관련 공식 Swift 문서(번역본)
[The Swift Language Guide(한국어) - 클로저 (Closures)](https://bbiguduk.gitbook.io/swift/language-guide-1/closures)     

Clousue, EscapingClosure, AutoClosure에 대해 소개하는 글  
[[Swift] AutoClosure, EscapingClosure 알아보기](https://icksw.tistory.com/157)  

Autoclosures에 대해 소개하는 글  
[[Swift] Autoclosure 개념과 활용사례](https://eunjin3786.tistory.com/468)  
  
AutoClosure로 Swift APIs를 디자인하는 방법에 대한 더 자세한 글  
[Using @autoclosure when designing Swift APIs](https://www.swiftbysundell.com/articles/using-autoclosure-when-designing-swift-apis/)  



