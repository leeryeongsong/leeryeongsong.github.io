---
title: "JohnSundell/SwiftTips #4 Using typealiases to reduce the length of method signatures에 대해 알아보자"
excerpt: " "
toc: true
toc_sticky: true
categories:
  - iOS
tags:
  - ios
  - 
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


typealias : 별명 



# 앞으로 읽으면 좋을 글
