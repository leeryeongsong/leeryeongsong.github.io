---
title: "JohnSundell/SwiftTips #3 Referencing either external or internal parameter name when writing docs에 대해 알아보자"
excerpt: " "
toc: true
toc_sticky: true
categories:
  - iOS
tags:
  - ios
  - 
---

[JohnSundell/SwiftTips](https://github.com/JohnSundell/SwiftTips)의 \#3 Referencing either external or internal parameter name when writing docs를 번역하고 관련 내용을 공부해보자.  

# 문서를 작성할 때 외부 또는 내부 매개변수 이름을 참고합니다.

Swift 문서를 작성할 때 외부 또는 내부 매개변수 레이블을 참조할 수 있습니다.
and they get parsed the same! 

```
// EITHER:

class Foo {
    /**    *   - parameter string: A string
    */func bar(with string: String) {}
}

// OR:

class Foo {
    /**    *   - parameter with: A string
    */func bar(with string: String) {}
}
```

# 앞으로 읽으면 좋을 글

[Swift : 기초문법 [매개변수 레이블 - Parameter Label]](https://seons-dev.tistory.com/109)


[[Swift] MarkUp Overview Documentation 작성하기 (설명문서작성)](https://nsios.tistory.com/63)




