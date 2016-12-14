---
layout: page
title: Subtypes
order: 5
published: true
categories:
  - 데이터 관리
tags: ['data', 'subtypes']
---

*Data Type*에 설명한대로 리얼그리드 DataProvider의 DataField는 네 가지 자료형 중 하나가 될 수 있습니다.  
하지만 업무 환경에서 기본 자료형이 제한된 범위로 사용되는 것은 흔한 일입니다.   
리얼그리드는 이런 요구 사항의 일부를 지원하기 위해 DataField 별 *Subtype* 속성을 지원합니다.  
*Subtype*은 데이터필드 추가시 지정할 수 있는데 *"subtype"* 지시자와 *"set"* 및 *"min"/"max"* 한정값을 사용할 수 있습니다.  
하지만, Subtype은 데이터필드의 자료형이 아니라 DataProvider에 해당 필드의 값이 저장될 때 지정된 범위에 맞춰주는 역할을 할 뿐입니다.   
즉, Subtype 적용이 해제된 시점에 저장된 기존 데이터나, 다른 Subtype을 적용해 저장된 데이터를 새로운 Subtype에 맞추는 일은 하지 않습니다.  
물론, 저장 범위의 역할 외에 지정된 Subype에 맞춰서 UI나 다른 기능이 동작하도록 하는 것은 가능한 일입니다.

---

#### 1). subtype 지시자

데이터필드 지정시 "subtype" 속성으로 설정할 수 있습니다. 기본 자료형별로 설정 가능한 값은 아래와 같습니다.

|:--|:--|
|**Text**|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*"char"* - 0 보다 큰 *"length"* 속성과 더불어 길이가 제한된 문자열로 저장됩니다. |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"length"를 0 이하로 지정하면 "text" 기본 자료형과 동일합니다.|
|||
|**Number**|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*"unum"* - 0 이상의 숫자로 저장됩니다.|
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*"int"* - 정수형 값으로 저장됩니다. |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<mark>i = v >= 0 ? Math.floor(v) : Math.ceil(v);</mark> 와 같은 방식으로 저장됩니다.|
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;즉, 1.1 이면 1 로, -1.1 이면 -1 로 저장됩니다.|
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*"uint"* - 0 이상의 정수형 값으로 저장됩니다.|
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<mark>i = Math.floor(v);</mark> 와 같은 방식으로 저장됩니다.|
|||
|**Datetime**|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*"date"* - 시간 부분이 제거된 날짜값으로 저장됩니다.|

```
"fields": [{
    "fieldName": "ItemId",
    "dataType": "number",
    "subtype": "unum"
},{
    "fieldName": "ItemName",
    "dataType": "text",
    "subtype": "char",
    "length": 100
},{
...
}];
```

---

#### 2). minimum/maximum

DataField를 추가할 때 *"min"* 혹은 *"minimum"* 과 *"max"* 혹은 *"maximum"* 속성들을 지정해서, 값이 저장될 때의 범위를 설정할 수 있습니다.  
*경계를 넘어선 값은 경계값으로 저장됩니다.* 즉, min 보다 작은 값은 min으로, max 보다 큰 값은 max로 저장됩니다.  
최소값이나 최소값 중 하나만 지정해도 되고, 최대값을 최소값보다 작게 지정하면 이 범위는 무시됩니다.  
이 속성들은 *Number, Datetime* 자료형에 지정할 수 있습니다.  
Datetime 필드에 이 속성을 지정할 때는 해당 필드의 datatimeFormat이나, 필드에 지정되지 않은 경우 DataProvider에 설정된 datetimeFormat에 맞는 문자열로 지정합니다.

```
"fields": [{
   "fieldName": "Price",
   "dataType": "number",
   "min": 100,
   "max": 200
   ...
```

---

#### 3). set

*Boolean* 자료형을 제외한 나머지 자료형의 DataField에 *"set"* 배열 속성 값을 지정해서, 배열에 포함된 값이 아니면 *undefined*로 저장되도록 할 수 있습니다.

```
"fields": [{
   "fieldName": "State",
   "set": ["ab", "cd", ...],
   ...
```

---

#### 4). 주의 사항

위에서 지적한 대로 리얼그리드 Subtype은 에러를 발생 시키지 않고, 입력되는 값을 범위 내의 값으로 조정하는 일종의 제한 조건(constraints)입니다.  
DataProvider의 *subtypeEnabled* 속성으로 subtype 기능을 중지 시키거나, 다시 활성화 시킬 수 있습니다.  
또, DataProvider에서 subtypeEnabled가 true로 지정됐다면, 각 데이터필드별 subtypeEnabled가 속성을 통해 활성화/비활성화 시킬 수 있습니다.

Subtype 설정은 행 추가/변경 등에서 요청된 필드 값이 *DataProvider에 저장되기 직전에 적용됩니다.*