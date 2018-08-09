---
layout: page
title: 'Pivot 최신버전 1.0.0'
published: true
description: ""
---

Pivot 최신 버전 이력



## 1.0.1 (2018년 8월)

---

#### 기능 개선

1. 포커스
  - [DisplayOptions.showFocus](http://help.realgrid.com/pivotApi/types/DisplayOptions/){_blank} 속성으로 포커스를 표시하고 키보드로 이동할 수 있습니다.
  - 다음과 같이 setDisplayOptions() 함수를 통해 포커스를 활성화할 수 있습니다.
```js
pivot.setDisplayOptions({
	showFocus: true
});
```
  - 포커스가 이동될때 [onCurrentChanged()](http://help.realgrid.com/pivotApi/RealPivot/onCurrentChanged/){_blank} 콜백이 발생합니다.  
  - `CSS` `realpivot-focus` class가 추가되었습니다.

1. 셀 복사
  - 선택된 셀의 값을 Ctrl+C 단축키를 통해 클립보드로 복사할 수 있게 되었습니다.
  - [CopyOptions.copyDisplayText](http://help.realgrid.com/pivotApi/types/CopyOptions/){_blank} 속성이이 true이면 표시된 텍스트가 복사되고, false이면 원시 데이터가 복사됩니다.

1. 컨텍스트 메뉴
  - 마우스 우측 버튼 클릭시 표시되는 컨텍스트 메뉴를 [setContextMenu()](http://help.realgrid.com/pivotApi/RealPivot/setContextMenu/){_blank}를 통해 대체할 수 있습니다.
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
  - [getContextMenu()](http://help.realgrid.com/pivotApi/RealPivot/getContextMenu/){_blank}를 호출하여 설정된 컨텍스트 메뉴를 가져올 수 있습니다.
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