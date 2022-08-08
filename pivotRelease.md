---
layout: page
title: 'Pivot 최신버전 1.0.8'
published: true
description: ""
---

Pivot 최신 버전 이력
## 1.0.9 (2022 8월)

---

#### 기능 개선
1. [getPivotFields](http://help.realgrid.com/pivotApi/types/getPivotFields){:target="_blank"}
  - 피벗 그리드를 구성하는 필드들을 가져오는 getPivotFields()함수가 추가되었습니다.
```js
var setupFields = pivot.getSetupFields();
```

1. 셀에 값이 없는 경우 표시되는 [emptyValue](http://help.realgrid.com/pivotApi/types/PivotField/#emptyValue){:target="_blank"}속성이 추가되었습니다.
  - `blankFillValue`보다 우선해서 적용됩니다.

1. rowLabel 또는 columnLabel 영역에 html tag를 적용후 excel export하면 html tag가 그대로 출력되는 현상이 개선되었습니다.

// api 수정 필요. // 데모 추가 필요.
1. [columnSizeCallback](http://help.realgrid.com/pivotApi/DisplayOptions/#columnSizeCallback){:target="_blank"}
  - column의 너비를 변경할수 있는 columnSizeCallback이 추가되었습니다.
  - `0`을 return시 화면에는 보이지 않지만 excel export시에는 너비가 `0`으로 출력됩니다.

// api 추가 필요.
1. [getFilter](http://help.realgrid.com/pivotApi/getFilter){:target="_blank"}
  - 현재 설정된 filter 정보를 가져오는 api가 추가되었습니다.

1. 행/컬럼/셀의 raw data
  - 행/컬럼/셀의 값을 계산할때 사용된 data의 dataRow를 확인 할수 있도록 개선되었습니다.
  - 셀의 값을 가져오는 [getCellValues](http://help.realgrid.com/pivotApi/getCellValues){:target="_blank"} api가 추가되었습니다.
  - 현재 선택된 셀의 값을 가져오는 [getCellValuesAt](){} api가 추가되었습니다.
  - [getRowValues](){}의 결과값에 ``가 추가되었습니다.
  - [getColumnValues](){}의 결과값에 ``가 추가되었습니다.

1. 현재 선택된 셀의 index
  - 현재 선택된 셀의 index를 가져오는 [](){} api가 추가되었습니다.

1. 피벗 크기 변경
  - 브라우저의 크기가 변경되거나 피벗 컨테이너의 display속성이 변경되었을때 피벗의 크기가 변경되도록 하는 [](){} 속성이 추가되었습니다.
  - 브라우저의 크기가 줄어들때 `body`영역에 스크롤이 생기지 않도록 하기위해서는 피벗 컨테이너의 overflow style을 `hidden`으로 해야합니다.

1. expression이 `min`일때 정상적으로 계산되지 않는 현상이 개선되었습니다.

1. 정렬
  - value를 이용한 정렬시 정상적으로 정렬되지 않는 현상이 개선되었습니다.
  - 컬럼헤더 영역 또는 행헤더 영역의 text를 클릭하면 정렬되는 기능이 추가되었습니다.
  - 헤더 클릭 정렬의 사용여부를 지정하는 [](){}속성이 추가되었습니다.
  - 값 헤더 영역의 text를 클릭하면 값을 이용한 정렬을 할수 있도록 설정창이 표시되는 기능이 추가되었습니다.
  - 사용자가 정렬을 변경했을때 정렬을 취소할수 있는 [](){} 콜백이 추가되었습니다.  
  `false`를 return 하면 정렬 변경이 취소됩니다.

1. valueType의 종류와 순서
  - `setup`화면에 표시되는 [](){}의 종류와 순서를 사용자가 지정할수 있도록 [](){}이 추가되었습니다.
  - 값 필드 개별로 지정할수 있도록 []()}{} 속성이 추가되었습니다.
  - `setup`화면에서 값 필드를 추가했을때 선택되는 valueType의 기본값을 지정할수 있는 [](){}속성이 추가되었습니다.

1. 특정 행이나 컬럼을 접은후 excel export시 오류가 발생하는 현상을 수정하였습니다.

1. setup창을 이용한 filter영역에 표시되는 필드 조건의 기본 설정을 변경하도록 하는 [](){}속성이 추가되었습니다.

1. 셀의 값이 없는 경우 표시되는[](){}의 기본값이 `0`에서 `null`로 변경되었습니다.
  - data 자체가 없을때 와 data의 값이 `0`일때가 구분되는 않는 현상때문에 기본값을 `null`로 변경하였습니다. 피벗 버전변경시 주의해야 합니다.

1. 필드 헤더의 너비를 변경할수 있는 [](){}속성이 추가되었습니다.

1. [](){}
  - body 셀의 `className`을 추가할수 있는 콜백이 추가되었습니다.

1. labelTooltip의 위치변경
  - 행 또는 컬럼의 헤더 tooltip 생성위치가 마우스가 위치한 곳에 표시되도록 변경되었습니다.

1. 설정 변경 이벤트
  - 사용자가 `setup`을 이용해서 피벗설정을 변경할때 발생하는 [](){}이 추가 되었습니다.
  - `false`를 return하면 설정 변경이 취소됩니다.

1. expand/collapse
  - 그룹행 또는 그룹컬럼의 펼침상태를 가져오는 [](){}와 [](){} api가 추가되었습니다.

추가된 api
getFilter

getPivotFields

getCellValues

getCellValuesAt

getValueNames

getCurrent

columnExpanded

rowExpanded

onSetupChanging

onSorting

추가된 enum
LabelType

#### 오류 수정
1. [blankFillValue](){}를 `null`로 설정후 excel export 시 `0`으로 출력되는 현상이 수정되었습니다.

## 1.0.8 (2021 4월)

1. GlobalContextMenu 로 destroy() 사용 시 오류가 개선되었습니다.  

1. formType: "grid" 인 경우 excel export시 오류가 개선되었습니다.  

1. setPivotFields() 사용 시 피벗 화면이 틀어지는 현상이 개선되었습니다.

## 1.0.3 (2019년 2월)

---

#### 기능 개선

1. Focus 가이드 표시
  - [DisplayOptions](http://help.realgrid.com/pivotApi/types/DisplayOptions/#showFocusGuide){:target="_blank"}의 showFocusGuide 속성이 추가되었습니다. showFocus와 showFocusGuide가 true이면 선택된 셀의 가로와 세로에 배경색을 표시할 수 있습니다.  
  - 다음과 같이 setDisplayOptions() 함수를 통해 사용 할 수 있습니다.  
```js
pivot.setDisplayOptions({
  showFocus: true,
  showFocusGuide: true
});
```
  - `CSS` `realpivot-focus-guide` class가 추가되었습니다.

1. 메모리 최적화
  - 컬럼과 행의 수가 대량일 때 Memory Overflow로 동작이 멈추는 현상이 있어 메모리 사용량을 최적화 하였습니다.

1. 값필드 가로 맞춤 설정
  - 이전 버전까지 expression이 "distinct"인 경우 중앙, 그 외의 경우 우측으로 가로 정렬로 고정되어 있었는데, 값 필드 별로 정렬 방식을 지정할 수 있게 하였습니다. 
  - [PivotField.valueAlignment](http://help.realgrid.com/pivotApi/types/PivotField/#valueAlignment){:target="_blank"} 속성을 "near", "center", "far"로 지정하여 맞춤 설정 할 수 있습니다.
  - 설정 화면에서 값 설정의 맞춤 방식 선택 박스가 추가 되었습니다.
  - `CSS` realpivot-cell 하위의 `span.near`, `span.center` class가 추가되었습니다.

1. 커스텀 날짜 표현
  - 필드의 [dateType](http://help.realgrid.com/pivotApi/types/DateValueType/){:target="_blank"}을 "custom"으로 설정 하면 [PivotField.dateFormat](http://help.realgrid.com/pivotApi/types/PivotField/#dateFormat){:target="_blank"}에 맞추어 표시합니다. 
  - 포맷에 사용하는 문자열은 Data Provider와 동일합니다.
  
1. 스크롤 UI 개선
  - 스크롤 버튼을 누르고 있는 동안 계속적으로 스크롤되도록 개선하였습니다.
  - 스크롤 바를 드래그해서 이동하는 중에 마우스 포인터가 Pivot을 벗어나도 가능하도록 개선하였습니다.

1. 공백을 &amp;nbsp;로 치환
  - Pivot은 HTML Dom방식이라 앞뒤 공백이나 연속되는 공백이 화면상에 표시 되지 않았습니다.
  - [DisplayOptions](http://help.realgrid.com/pivotApi/types/DisplayOptions/#keepLabelSpace){:target="_blank"}의 keepLabelSpace 속성이 true이면 라벨상의 모든 공백을 &amp;nbsp;로 치환하여 표시합니다.

1. 라벨 prefix/suffix
  - 필드의 displayFormat, summaryFormat에 사용되는 문자열이 특정 웹서버에서 예약어로 사용되어 사용하기 어려운 경우가 있었습니다.
  - [PivotField.labelPrefix](http://help.realgrid.com/pivotApi/types/PivotField/#labelPrefix){:target="_blank"}, [PivotField.labelSuffix](http://help.realgrid.com/pivotApi/types/PivotField/#labelSuffix){:target="_blank"}를 사용 해 displayFormat과 유사한 동작을 하도록 하였습니다. 
  - 요약을 위한 [PivotField.summaryPrefix](http://help.realgrid.com/pivotApi/types/PivotField/#summaryPrefix){:target="_blank"}, [PivotField.summarySuffix](http://help.realgrid.com/pivotApi/types/PivotField/#summarySuffix){:target="_blank"}도 추가하였습니다.
  - [format 사용예]
```js
    pivot.setFieldMapping([{
        ...
        displayFormat: "${value}년도",
        summaryFormat: "${value}년도 합",
        ...
    }]);
```    
  - [prefix/suffix 사용예]
```js
    pivot.setFieldMapping([{
        ...
        labelSuffix:"년도",
        summarySuffix:"년도 합",
        ...
    }]);
```    

#### 오류 수정

1. form 태그
  - form 태그 안에 피벗 컨테이너가 있는 경우 설정화면의 버튼이 커밋 버튼으로 오동작하는 문제를 수정하였습니다.
  - `CSS` button class가  input type="button" 으로 변경 되었습니다.

1. 필드 정렬
  - 필드의 sortDir 속성을 기본 정의하지 않았을 때 제대로 정렬되지 않는 문제를 수정하였습니다.

1. 컬럼 필드가 없을때 설정 화면 오류
  - 컬럼 필드가 없을때 설정화면에서 값 필드의 정렬 방식 선택 UI에서 오류  가 발생하는 문제를 수정하였습니다.


## 1.0.2 (2018년 10월)

---

#### 기능 개선

1. Expand/Collapse
  - [GroupOptions](http://help.realgrid.com/pivotApi/types/GroupOptions/){:target="_blank"}의 columnExpand, rowExpand 속성으로 컬럼과 행의 그룹을 기본으로 특정 레벨까지 펼치도록 지정할 수 있게 되었습니다.
  - 다음과 같이 setGroupOptions() 함수를 통해 사용 할 수 있게 되었습니다.
```js
pivot.setGroupOptions({
  columnExpand: 1,
  rowExpand: -1
});
```
  - 피벗이 표시 된 후 다음의 함수를 통해 특정 레벨 또는 특정 라벨을 펼치고 닫을 수 있게 되었습니다.  
    `레벨단위`: [expandColumnLevel()](http://help.realgrid.com/pivotApi/RealPivot/expandColumnLevel/){:target="_blank"}, [expandRowLevel()](http://help.realgrid.com/pivotApi/RealPivot/expandRowLevel/){:target="_blank"}  
    `라벨단위`: [expandColumn()](http://help.realgrid.com/pivotApi/RealPivot/expandColumn/){:target="_blank"}, [expandRow()](http://help.realgrid.com/pivotApi/RealPivot/expandRow/){:target="_blank"}, [collapseColumn()](http://help.realgrid.com/pivotApi/RealPivot/collapseColumn/){:target="_blank"}, [collapseRow()](http://help.realgrid.com/pivotApi/RealPivot/collapseRow/){:target="_blank"}  
  - Ctrl + Alt + 방향키로 컬럼과 행의 그룹을 접고 펼 수 있게 되었습니다.

1. 피벗 값 가져오기
  - 피벗과 연동하여 차트등을 구현하기 위해서 피벗에 표시된 값을 가져올 수 있는 다음과 같은 함수가 추가되었습니다.  
    `필드정보`: [getColumnFieldNames()](http://help.realgrid.com/pivotApi/RealPivot/getColumnFieldNames/){:target="_blank"}, [getRowFieldNames()](http://help.realgrid.com/pivotApi/RealPivot/getRowFieldNames/){:target="_blank"}  
    `라벨정보`: [getColumnLabels()](http://help.realgrid.com/pivotApi/RealPivot/getColumnLabels/){:target="_blank"}, [getRowLabels()](http://help.realgrid.com/pivotApi/RealPivot/getRowLabels/){:target="_blank"}  
    `데이터정보`: [getRowValues()](http://help.realgrid.com/pivotApi/RealPivot/getRowValues/){:target="_blank"}, [getColumnValues()](http://help.realgrid.com/pivotApi/RealPivot/getColumnValues/){:target="_blank"}, [getAllValues()](http://help.realgrid.com/pivotApi/RealPivot/getAllValues/){:target="_blank"}
  - [HighCharts 연계 데모](/Pivot/PivotHighCharts/)가 추가되었습니다.

1. 라벨 필드 정렬 별도 지정
  - 라벨 필드의 정렬 방식을 외부에서 직접 지정할 수 있게 되었습니다.  
  [PivotField.sortCallback](http://help.realgrid.com/pivotApi/types/PivotField/#sortCallback){:target="_blank"}에 compare함수를 지정하여 함수에서 정렬방법을 -1, 0, 1의 결과값으로 조정할 수 있습니다. 

1. 그리드 모드 헤더
  - [HeaderOptions.formType](http://help.realgrid.com/pivotApi/types/HeaderOptions/){:target="_blank"}속성이 추가되었습니다.  
  이 속성을 "grid"로 지정하면 헤더 영역을 그리드와 같이 표시하도록 하였습니다.  
  이 헤더에서는 설정버튼이 제공되지 않으므로 필요시 [showSetupView()](http://help.realgrid.com/pivotApi/RealPivot/showSetupView/){:target="_blank"} 함수를 이용해야 합니다.

1. 필드별 넓이 지정
  -  [PivotField.width](http://help.realgrid.com/pivotApi/types/PivotField/#width){:target="_blank"}속성으로 필드의 개별 넓이를 지정할 수 있도록 하였습니다.
  - 컬럼의 상위 필드는 하위에 의하여 자동 결정되기 때문에 width 속성이 무시됩니다.


#### 오류 수정

1. 접힌 상태에서 요약 라벨의 크기를 변경하고 다시 펼쳤을 때 위치가 일치하지 않는 문제를 수정하였습니다.

1. 피벗 영역을 키운 후 resetSize 호출 후 늘어난 부분 클릭 시 화면이 깜빡거리는 현상을 수정하였습니다.

1. 행 라벨 리사이즈 후 바디 영역 우측에 빈 공간이 생기는 현상을 수정하였습니다.


## 1.0.1 (2018년 8월)

---

#### 기능 개선

1. 포커스
  - [DisplayOptions.showFocus](http://help.realgrid.com/pivotApi/types/DisplayOptions/){:target="_blank"} 속성으로 포커스를 표시하고 키보드로 이동할 수 있습니다.
  - 다음과 같이 setDisplayOptions() 함수를 통해 포커스를 활성화할 수 있습니다.
```js
pivot.setDisplayOptions({
	showFocus: true
});
```
  - 포커스가 이동될때 [onCurrentChanged()](http://help.realgrid.com/pivotApi/RealPivot/onCurrentChanged/){:target="_blank"}  콜백이 발생합니다. 
  - `CSS` `realpivot-focus` class가 추가되었습니다.

1. 셀 복사
  - 선택된 셀의 값을 Ctrl+C 단축키를 통해 클립보드로 복사할 수 있게 되었습니다.
  - [CopyOptions.copyDisplayText](http://help.realgrid.com/pivotApi/types/CopyOptions/){:target="_blank"}  속성이이 true이면 표시된 텍스트가 복사되고, false이면 원시 데이터가 복사됩니다.

1. 컨텍스트 메뉴
  - 마우스 우측 버튼 클릭시 표시되는 컨텍스트 메뉴를 [setContextMenu()](http://help.realgrid.com/pivotApi/RealPivot/setContextMenu/){:target="_blank"} 를 통해 대체할 수 있습니다.
```js
pivot.setContextMenu([{
    text: "menu1",
    callback: function () { alert("menu1 click"); }
}, {
    text: "menu2",
    callback: function () { alert("menu2 click"); }
}, {
    text: "-"
}, {
    text: "menu3",
    callback: function () { alert("menu3 click"); }
}]);
```  
  - [getContextMenu()](http://help.realgrid.com/pivotApi/RealPivot/getContextMenu/){:target="_blank"} 를 호출하여 설정된 컨텍스트 메뉴를 가져올 수 있습니다.
  - 상단 Menu Icon을 통해 표시되는 메뉴에 관한 기능은 setGlobalContextMenu(), getGlobalContextMenu()로 이름이 변경되었습니다.
  
1. Setup UI
  - Setup 화면 타이틀 부분을 드래그하여 이동할 수 있도록 개선하였습니다.
  - 컬럼, 행 간 필드 이동이 가능하도록 개선하였습니다.

1. 기타 UI 개선
  - 필드 헤더와 값 헤더 사이의 경계선을 이동하도록 개선하였습니다.
  - 컬럼 헤더, 행 헤더, 값 헤더의 내용이 줄바꿈되도록 수정하였습니다.

#### 오류 수정

1. 고유 값 처리
  - 값 필드의 표현식이 고유(distinct)일 때 표시되지 않는 오류가 수정되었습니다.
  - 고유 값일때 가운데 정렬하도록 개선하였습니다.
  - `CSS` `span.distinct` class가 추가되었습니다.

  
## 1.0.0 (2018년 6월 15일)

- 데이터 수집 속도가 개선되었습니다.
- 전반적인 Pivot Rendering 속도가 개선되었습니다.
- Setup에서 드래그 UI가 개선되어 Firefox, IE 9등의 브라우저에서 사용할 수 있도록 하였습니다.
- Setup에서 필드 제거 버튼을 추가하였습니다.
- [DisplayOptions.rowHeight](http://help.realgrid.com/pivotApi/types/DisplayOptions/)의 기본값이 25로 변경되었습니다.
- rowHeight크기에 맞춰 스크롤 되도록 개선되었습니다.
- 많은 오류가 수정되었습니다.

## 0.8.0 (2018년 2월 28일)

 initial version