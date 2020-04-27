---
layout: default-layout
sideHeader: C and C++ Struct
sourceCodeUrl: programming/c-cplusplus/api-reference/struct/Quadrilateral.md
sidebarListFile: sidelist-c-cpp-structs
needCollapsedSideBar: false
needAutoGenerateSidebar: false
---


# Quadrilateral
Stores the quadrilateral.  

## Typedefs

```cpp
typedef struct tagQuadrilateral  Quadrilateral 
```  
  
---
  

## Attributes
  
| Attribute | Type |
|---------- | ---- |
| [`points`](#points) | [`DBRPoint`](DBRPoint.md)[4] |


### points
Four vertexes in a clockwise direction of a quadrilateral. Index 0 represents the left-most vertex. 
```cpp
DBRPoint tagQuadrilateral::points[4]
```



