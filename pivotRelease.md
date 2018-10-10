---
layout: page
title: 'Pivot 최신버전 1.0.2'
published: true
description: ""
---

Pivot 최신 버전 이력


## 1.0.2 (2018년 10월)

---

#### 기능 개선

1. Expand/Collapse
  - [GroupOptions](http://help.realgrid.com/pivotApi/types/GroupOptions/){:target="_blank"}의 columnExpand, rowExpand 속성으로 컬럼과 행의 그룹을 기본으로 특정 레벨까지 펼치도록 지정할 수 있게 되었습니다.
  - 다음과 같이 setGroupOptions() 함수를 통해 사용 할 수 있게 되었습니다.
```js
pivot.setGroupOptions({
  columnExpand: 1
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
  - 라벨 필드의 정렬 방식을 외부에서 직접 지정할 수 있게 되었습니다. [PivotField.sortCallback](http://help.realgrid.com/pivotApi/types/PivotField/#sortCallback)에 compare함수를 지정하여 함수에서 정렬방법을 -1, 0, 1의 결과값으로 조정할 수 있습니다. 

1. 그리드 모드 헤더
  - [HeaderOptions.formType](http://help.realgrid.com/pivotApi/types/HeaderOptions/){:target="_blank"}속성이 추가되었습니다. 이 속성을 "grid"로 지정하면 헤더 영역을 그리드와 같이 표시하도록 하였습니다. 이 헤더에서는 설정버튼이 제공되지 않으므로 필요시 [showSetupView()](http://help.realgrid.com/pivotApi/RealPivot/showSetupView/){:target="_blank"} 함수를 이용해야 합니다.

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