---
layout: page
title: 'Pivot 최신버전 1.0.15'
published: true
description: ""
---

Pivot 최신 버전 이력
## 1.0.15 (2025년 9월)
#### 기능 개선
1. [DisplayOptions](https://help.realgrid.com/pivotApi/types/DisplayOptions/){:target="_blank"}에 header, row, column 영역의 resize 가능 여부를 제어하는 속성을 추가    
1. [PivotField](https://help.realgrid.com/pivotApi/types/PivotField/){:target="_blank"} 에 `displayField`가 지정되어있고 `displayField`의 data가 `""`일때 `sourceField`의 data가 표시되는 현상 수정
1. [SetupOptions](https://help.realgrid.com/pivotApi/types/SetupOptions/){:target="_blank"}에 행필드 또는 컬럼필드의 조작을 막도록 하는 [rowControlLevel](https://help.realgrid.com/pivotApi/types/SetupOptions/){:target="_blank"}, [columnControlLevel](https://help.realgrid.com/pivotApi/types/SetupOptions/){:target="_blank"} 속성추가
1. value의 값을 절대값으로 표시할수 있도록 `numberFormat` 개선

#### 오류 수정
1. [SummaryOptions](https://help.realgrid.com/pivotApi/types/SummaryOptions/){:target="_blank"}의 `totalFixed`가 `true`이고 `rowPosition`이 `last`이면서 data가 적은 경우 행의 합계가 정상적으로 표시되지 않는 오류 수정

## 1.0.14 (2025년 5월)
#### 기능 개선
1. 설정창에서 전체 설정을 초기화 할수 있는 버튼을 표시하도록 하는 [SetupOptions.showResetAllButton](https://help.realgrid.com/pivotApi/types/SetupOptions/){:target="_blank"} 과 개별 필드초기화 버튼을 표시하도록 하는 [SetupOptions.showResetButtons](https://help.realgrid.com/pivotApi/types/SetupOptions/){:target="_blank"}속성 추가


## 1.0.13 (2025년 4월)
#### 기능 개선
1. `setupView`가 종료될때 발생하는 [onSetupClosed](http://help.realgrid.com/pivotApi/RealPivot/onSetupClosed/){:target="_blank"}이벤트 추가
1. [showSetupView()](http://help.realgrid.com/pivotApi/RealPivot/showSetupView/){:target="_blank"}를 이용해서 설정화면을 표시할때 parentElement를 지정할수 있도록 개선

#### 오류 수정
1. setupView가 표시되는 상태에서 `showSetupView`를 다시 호출하면 pivot을 사용할수 없는 현상 개선


## 1.0.12 (2025년 2월)
#### 기능 개선
1. 설정창을 왼쪽에 표시했을때 `tooltip`이 정상적인 위치에 표시되지 않는 현상 개선    
1. 일부 프레임웍에서 `RealPivot module`이 load되지 않는 현상 개선
1. 설정창과 pivot화면의 간격을 지정하는 [SetupOptions](https://help.realgrid.com/pivotApi/types/SetupOptions/){:target="_blank"}.itemGap 속성 추가

#### 오류 수정
1. [SummaryOptions](https://help.realgrid.com/pivotApi/types/SummaryOptions/){:target="_blank"}의 `totalFixed`가 `true`일때 `rowPosition`또는 `columnPosition`이 `last`인 경우 키보드를 이용한 focus이동 개선    
스크롤시 전체요약 영역이 일부 표시되지 않는 현상 개선


## 1.0.11 (2025년 1월)
#### 기능 개선
1. [SetupOptions](https://help.realgrid.com/pivotApi/types/SetupOptions/){:target="_blank"}
  - 설정창을 왼쪽 또는 오른쪽으로 표시하도록 하는 `position` 속성 추가
```js
pivot.setSetupOptions({position: "right"});
```

1. [PivotField.displayLabels](https://help.realgrid.com/pivotApi/types/PivotField/){:target="_blank"}
  - 행의 합계를 표시하는 영역에도 `displayLables`가 적용되도록 수정

1. `chromium`계열 브라우저의 콘솔창에 웹접근성 관련 오류가 표시되지 않도록 개선    

1. focus cell의 위치를 지정하도록 하는 [setCurrent](http://help.realgrid.com/pivotApi/RealPivot/setCurrent/){:target="_blank"} api가 추가.    
  - `valueField`, `rowPath`, `columnPath`를 지정하면 해당하는 셀의 위치로 focus가 이동한다.    
```js
  pivot.setCurrent("차량가격", ["국산","기아","대형"], [4, 10]);
```

## 1.0.10 (2023년 8월)
#### 기능 개선
1. [PivotExport]({{'/Pivot/PivotExport/' | prepand:site.baseurl}})
  - `title` 또는 `tail`영역을 출력할때 `style`속성을 지정할수 있도록 개선되었습니다.
```js
  pivot.exportGrid({
    type: "excel", 
    target:"local", 
    documentTitle: {
      message:"documentTitle", 
      styles: {border: "2px solid blue", textAlign: "center", color:"red", fontSize:"20px", fontWeight:"bold"},
    }
  });
  // 또는
  pivot.exportGrid({
    type: "excel",
    target: "local",
    documentTitle: {
      message: "Title을 입력합니다.",
      styleName: "style-name"
    }
  })
```

1. [ExportOptions](http://help.realgrid.com/pivotApi/types/ExportOptions/){:target="_blank"}
  - export시 임의 셀을 출력할수 있도록 [userCells](http://help.realgrid.com/pivotApi/types/ExportOptions/#userCells){:target="_blank"}속성이 추가되었습니다.
```js
  pivot.exportGrid({type: "excel", target: "local", 
    yOffset: 5,
    userCells: [
      {row: 1, col: 0, value: '결\n재', mergeRow: 3, mergeCol: 1, styles: {border: "1px solid black", textAlign: "center", verticalAlign: "middle"}, height: 30},
      {row: 1, col: 1, value: '담당', styles: {border: "1px solid black"}, styleName: "user-cell-2"},
      {row: 1, col: 2, value: '팀장', styles: {border: "1px solid black"}, styleName: "user-cell-2"},
      {row: 1, col: 3, value: '부서장', styles: {border: "1px solid black"}, styleName: "user-cell-2"},
      {row: 1, col: 4, value: '사장', styles: {border: "1px solid black"}, styleName: "user-cell-2"},
      {row: 2, col: 1, value: '', mergeRow: 2, mergeCol: 1, styles: {border: "1px solid black"}, heights: [40, 50], styleName: "user-cell-2"},
      {row: 2, col: 2, value: '', mergeRow: 2, mergeCol: 1, styles: {border: "1px solid black"}, styleName: "user-cell-2"},
      {row: 2, col: 3, value: '', mergeRow: 2, mergeCol: 1, styles: {border: "1px solid black"}, styleName: "user-cell-2"},
      {row: 2, col: 4, value: '', mergeRow: 2, mergeCol: 1, styles: {border: "1px solid black"}, styleName: "user-cell-2"},
    ]
  });
```

  - 사용자가 출력 셀을 추가할때 출력되는 row와 column을 참조해서 셀의 위치를 변경할수 있도록 [userCellsCallback](http://help.realgrid.com/pivotApi/types/ExportOptions/#userCellsCallback){:target="_blank"}콜백이 추가되었습니다.
```js
var callback = function(pivot, rowCount, columnCount) {
  return [
    {row: 3, col: colCount -3, mergeCol: 3, text: "열의 마지막에 표시", styles:{textAlign:"right"}}
  ]
}
pivot.exportGrid({"type":"excel", "target":"local", "yOffset":4, userCellsCallback: callback});
```

1. data를 Loading한 이후 행의 헤더 또는 컬럼의 헤더를 클릭하여 정렬하는 경우 이미 만들어진 데이터를 이용해서 정렬하도록 개선되었습니다.

1. 데이터의 양이 많은 경우 데이터 분석시에도 진행바가 표시되도록 개선되었습니다.
## 1.0.9 (2022년 8월)

---

#### 기능 개선
1. [getPivotFields](http://help.realgrid.com/pivotApi/RealPivot/getPivotFields/){:target="_blank"}
  - 피벗 그리드를 구성하는 필드들을 가져오는  api가 추가되었습니다.
```js
var currentFields = pivot.getPivotFields();
```

1. 셀에 값이 없는 경우 표시되는 [emptyValue](http://help.realgrid.com/pivotApi/types/PivotField/#emptyValue){:target="_blank"}속성이 추가되었습니다.
  - `blankFillValue`보다 우선해서 적용됩니다.

1. [columnSizeCallback](http://help.realgrid.com/pivotApi/types/DisplayOptions/#columnSizeCallback){:target="_blank"}
  - column의 너비를 변경할수 있는 columnSizeCallback이 추가되었습니다.
  - `0`을 return시 화면에는 보이지 않지만 excel export시에는 너비가 `0`으로 출력됩니다.

1. [getFilter](http://help.realgrid.com/pivotApi/RealPivot/getFilter/){:target="_blank"}
  - 현재 설정된 filter 정보를 가져오는 api가 추가되었습니다.

1. 행/컬럼/셀의 raw data
  - 행/컬럼/셀의 값을 계산할때 사용된 data의 dataRow를 확인 할수 있도록 개선되었습니다.
  - 셀의 값을 가져오는 [getCellValues](http://help.realgrid.com/pivotApi/RealPivot/getCellValues/){:target="_blank"} api가 추가되었습니다.
  - 현재 선택된 셀또는 입력된 CellIndex의 값을 가져오는 [getCellValuesAt](http://help.realgrid.com/pivotApi/RealPivot/getCellValuesAt/){:target="_blank"} api가 추가되었습니다.
  - [getRowValues](http://help.realgrid.com/pivotApi/RealPivot/getRowValues/){:target="_blank"}의 결과값에 `dataRows`가 추가되었습니다.
  - [getColumnValues](http://help.realgrid.com/pivotApi/RealPivot/getColumnValues/){:target="_blank"}의 결과값에 `dataRows`가 추가되었습니다.

1. 현재 선택된 셀의 index
  - 현재 선택된 셀의 index를 가져오는 [getCurrent](http://help.realgrid.com/pivotApi/RealPivot/getCurrent/){:target="_blank"} api가 추가되었습니다.

1. 피벗 크기 변경
  - 브라우저의 크기가 변경되거나 피벗 컨테이너의 display속성이 변경되었을때 피벗의 크기가 변경되도록 하는 [displayOptions.watchDisplayChange](http://help.realgrid.com/pivotApi/types/DisplayOptions/#watchDisplayChange){:target="_blank"} 속성이 추가되었습니다.
  - 브라우저의 크기가 줄어들때 `body`영역에 스크롤이 생기지 않도록 하기위해서는 피벗 컨테이너 div style의 overflow 속성을 `hidden`으로 해야합니다.

1. 정렬
  - value를 이용한 정렬시 정상적으로 정렬되지 않는 현상이 개선되었습니다.
  - 컬럼헤더 영역 또는 행헤더 영역의 text를 클릭하면 정렬되는 기능이 추가되었습니다.
  - 헤더 클릭 정렬의 사용여부를 지정하는 [headerOptions.headerSortable](http://help.realgrid.com/pivotApi/types/HeaderOptions/#headerSortable){:target="_blank"}속성이 추가되었습니다.
  - 값 헤더 영역의 text를 클릭하면 값을 이용한 정렬을 할수 있도록 설정창이 표시되는 기능이 추가되었습니다.
  - 사용자가 정렬을 변경했을때 정렬을 취소할수 있는 [onSorting](http://help.realgrid.com/pivotApi/RealPivot/onSorting/){:target="_blank"} 콜백이 추가되었습니다.  
  `false`를 return 하면 정렬 변경이 취소됩니다.

1. valueType의 종류와 순서
  - `setup`화면에 표시되는 [valueType](http://help.realgrid.com/pivotApi/types/ValueType/){:target="_blank"}의 종류와 순서를 사용자가 지정할수 있도록 [setupOptions.expressions](http://help.realgrid.com/pivotApi/types/SetupOptions/#expressions){:target="_blank"} 속성이 추가되었습니다.
  - 값 필드 개별로 사용가능한 `valueType`을 지정할수 있도록 [expressions](http://help.realgrid.com/pivotApi/types/PivotField/#expressions){:target="_blank"} 속성이 추가되었습니다.
  - [field.expression](http://help.realgrid.com/pivotApi/types/PivotField/#expression){:target="_blank"}을 지정하지 않았을때 기본값으로 사용되는 [DataOptions.defaultExpression](http://help.realgrid.com/pivotApi/types/DataOptions/#defaultExpression){:target="_blank"}속성이 추가되었습니다.

1. setup창을 이용한 filter영역에 표시되는 필드 조건의 기본 설정을 변경하도록 하는 [setupOptions.filterOperation](http://help.realgrid.com/pivotApi/types/SetupOptions/#filterOperation){:target="_blank"}속성이 추가되었습니다.
  - `"and"` 또는 `"or"`로 지정할수 있으며 setup화면이 처음 생성될때 한번만 적용되고 사용자가 변경을 하면 변경된 값이 유지됩니다.

1. 셀의 값이 없는 경우 표시되는[blankFillValue](http://help.realgrid.com/pivotApi/types/DisplayOptions/#blankFillValue){:target="_blank"}의 기본값이 `0`에서 `null`로 변경되었습니다.
  - data 자체가 없을때 와 data의 값이 `0`일때가 구분되는 않는 현상때문에 기본값을 `null`로 변경하였습니다. 피벗 버전변경시 주의해야 합니다.

1. 필드 헤더의 너비를 변경할수 있는 [displayOptions.labelTextWidth](http://help.realgrid.com/pivotApi/types/DisplayOptions/#labelTextWidth){:target="_blank"}속성이 추가되었습니다.  

1. [displayOptions.styleCallback](http://help.realgrid.com/pivotApi/types/DisplayOptions/#styleCallback){:target="_blank"} 속성이 추가되었습니다.
  - body 셀의 `className`을 추가할수 있는 콜백이 추가되었습니다.
  - export시 style을 적용하기 위해서는 [exportOptions.applyStyleCallback](http://help.realgrid.com/pivotApi/types/ExportOptions/#applyStyleCallback){:target="_blank"}을 `true`로 지정해야 합니다.    
```js
    var styleCallback = function(pivot, index, value){
        if (index.rows["국가"] === "국산" && index.rows["브랜드명"] === "기아" && index.valueField === "차량가격") {
            var st = '기아';
            if (value < 10000) {
                st += '-low';
            } else if (value > 50000) {
                st += '-high';
            }
            return st;
        }
    };
    pivot.setDisplayOptions({"styleCallback": styleCallback});
    pivot.drawView();
```

1. labelTooltip의 위치변경
  - 행 또는 컬럼의 헤더 tooltip 생성위치가 마우스가 위치한 곳에 표시되도록 변경되었습니다.

1. 설정 변경 이벤트
  - 사용자가 `setup`을 이용해서 피벗설정을 변경할때 발생하는 [onSetupChanging](http://help.realgrid.com/pivotApi/RealPivot/onSetupChanging/){:target="_blank"}이 추가 되었습니다.
  - `false`를 return하면 설정 변경이 취소됩니다.

1. expand/collapse
  - 그룹행 또는 그룹컬럼의 펼침상태를 가져오는 [getRowExpanded](http://help.realgrid.com/pivotApi/RealPivot/getRowExpanded/){:target="_blank"}와 [getColumnExpanded](http://help.realgrid.com/pivotApi/RealPivot/getColumnExpanded/){:target="_blank"} api가 추가되었습니다.

1. labelEnable이 `true`인 필드를 행필드 또는 컬럼필드에만 추가할수 있도록 하는 [pivotField.labelType](http://help.realgrid.com/pivotApi/types/PivotField/#labelType){:target="_blank"}이 추가되었습니다.
  - `labelType`을 `row`로 지정하게 되면 행필드에만 추가 가능하며 `column`으로 지정하면 컬럼 필드에만 추가 할수 있습니다.

#### 오류 수정
1. [blankFillValue](http://help.realgrid.com/pivotApi/types/DisplayOptions/#blankFillValue){:target="_blank"}를 `null`로 설정후 excel export 시 `0`으로 출력되는 현상이 수정되었습니다.

1. rowLabel 또는 columnLabel 영역에 html tag를 적용후 excel export하면 html tag가 그대로 출력되는 현상이 수정되었습니다.

1. expression이 `min`일때 정상적으로 계산되지 않는 현상이 개선되었습니다.

1. 특정 행이나 컬럼을 접은후 excel export시 오류가 발생하는 현상을 수정하였습니다.

1. 행 또는 컬럼 필드의 값이 `null`또는 `undefined`인 경우 누락되는 현상을 수정하였습니다.

1. RealGridDom과 연결된 pivot의 경우 [buildPivot()](http://help.realgrid.com/pivotApi/RealPivot/buildPivot/){:target="_blank"}을 호출해도 변경전 data를 가져오는 현상을 개선하였습니다.

## 1.0.8 (2021년 4월)

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