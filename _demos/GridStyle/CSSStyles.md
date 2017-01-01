---
layout: page
title: CSS Styles
order: 6
published: false
devbox: true
devboxfile: DynamicStylesonRows_devbox.md
categories:
  - 그리드 스타일
tags: ['style', '스타일', 'css', '씨에스에스']
---

RealGridJS 1.1.17.2245 버전부터 Popup, DropDown, Date 에디터에서 CSS 스타일을 적용할 수 있습니다.
ContextMenu는 PopupMenu와 CSS 스타일을 공유 합니다.
그리드에서 마우스 오른쪽 버튼을 클릭하여 ContextMenu 스타일을 확인하세요.

각 에디터에 CSS 스타일을 사용하기 위해서는 editorOptions.useCssStyleDropDownList, useCssStyleDatePicker, useCssStylePopupMenu 속성값에 true를 설정해야 합니다.
에디터 모두 CSS Style을 적용 한다면 useCssStyle 속성값만 true로 설정해도 됩니다.

각 엘리먼트에 적용된 클래스 명은 더보기에서 확인하세요.

`※ CSS 스타일은 각 객체가 생성된 이후에는 변경할 수 없습니다.(동적으로 변경할 수 없습니다.)`

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {
    var newDynamicStyles = [{
        criteria: "row mod 2 = 0",
        styles: "background=#F4F4FA"
    }];

    gridView.setStyles({
        body: {
            dynamicStyles: newDynamicStyles
        }
    });    
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="fieldset1"
  columnSet="CSSStylesColumn"
  dpOptionSet="dataProviderOption1"  
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}
