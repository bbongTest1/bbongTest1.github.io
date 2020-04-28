---
layout: default-layout
sideHeader: C and C++ Struct
sourceCodeUrl: /programming/c-cplusplus/api-reference/struct/IntermediateResultArray.md
sidebarListFile: sidelist-c-cpp-structs
needCollapsedSideBar: false
needAutoGenerateSidebar: false
---


# IntermediateResultArray
Stores the intermediate result array.

## Typedefs

```cpp
typedef struct tagIntermediateResultArray  IntermediateResultArray
```  
  
---
  

## Attributes
  
| Attribute | Type |
|---------- | ---- |
| [`resultsCount`](#resultscount) | *int* |
| [`results`](#results) | [`PIntermediateResult`](IntermediateResult.md)*  |


### resultsCount
The total count of intermediate result.
```cpp
int tagIntermediateResultArray::resultsCount
```

### results
The intermediate result array.
```cpp
PIntermediateResult* tagIntermediateResultArray::results
```


