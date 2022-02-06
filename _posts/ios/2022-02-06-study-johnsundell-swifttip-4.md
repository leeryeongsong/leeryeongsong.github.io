---
title: "JohnSundell/SwiftTips #4 Using typealiases to reduce the length of method signatures에 대해 알아보자"
excerpt: "typealias "
toc: true
toc_sticky: true
categories:
  - iOS
tags:
  - ios
  - typealias
---

[JohnSundell/SwiftTips](https://github.com/JohnSundell/SwiftTips)의 \#3 Using typealiases to reduce the length of method signatures를 번역하고 관련 내용을 공부해보자.  

# typealias를 사용하여 메서드 시그니처 길이를 줄입니다.

Swift에서 정말 유용하다고 생각하는 기능 : typealias를 사용하여 generic 타입에서 method signatures 길이 줄이기

```
public class PathFinder<Object: PathFinderObject> {
    public typealias Map = Object.Map
    public typealias Node = Map.Node
    public typealias Path = PathFinderPath<Object>
    
    public static func possiblePaths(for object: Object, at rootNode: Node, on map: Map) -> Path.Sequence {
        return .init(object: object, rootNode: rootNode, map: map)
    }
}
```


typealias : 타입 별명. 기존에 선언되어 있는 타입에 별칭을 사용. 새로운 타입을 생성하는 것은 아님. 별칭을 사용했을 때 실제 타입을 참조하도록 허용한 것. 
typealias 키워드를 사용해서 선언한다.  
```
typealias name(별명) = existing type
```
예시)  
```
public typealias Map = Object.Map  
```

메서드 시그니처(Method signature) : 메서드 이름과 메개변수 리스트의 조합   
예시)  
```
possiblePaths(for object: Object, at rootNode: Node, on map: Map)  
```


[Swift typealias, 스위프트 별명 사용방법, 주의사항](https://0urtrees.tistory.com/126)  

[5 Ways to Use Typealias in Swift](https://betterprogramming.pub/5-ways-to-use-type-alias-in-swift-45ddce3cc941)  


[Swift - typealias](https://brody.tistory.com/103)  
