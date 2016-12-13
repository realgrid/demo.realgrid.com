---
layout: page
title: 불린 타입 필드
order: 3
devbox: true
devboxfile: BooleanField-devbox.md
published: true
categories:
  - 데이터 관리
tags: ['data', 'bool', 'boolean']
---

DataProvider는 Boolean 필드의 값을 `undefined`나 `false/true` 둘 중 하나로 저장합니다.  

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
	var data = [
        ["False, False, False, False, False, False", "False", "False", "False", "False", "False"],
        ["True, True, True, True, True, True", "True", "True", "True", "True", "True"],
        ["N, N, N, N, N, N", "N", "N", "N", "N", "N"],
        ["Y, Y, Y, Y, Y, Y", "Y", "Y", "Y", "Y", "Y"],
        ["false, false, false, false, false, false", "false", "false", "false", "false", "false"],
        ["true, true, true, true, true, true", "true", "true", "true", "true", "true"],
        ["n, N, n, n, n, n", "n", "N", "n", "n", "n"],
        ["y, Y, y, y, y, y", "y", "Y", "y", "y", "y"],
        ["1, 1, 1, 1, 0, 1", "1", "1", "1", "1", "1"],
        ["'', 'false', false, 'f', 0", "", "false", false, "f", 0]
    ];
 
	dataProvider.setRows(data);
}
var onDoneDataSet = function() {
	gridView.setStyles({
        body: {
            cellDynamicStyles: [{
                "criteria": "value",
                "styles": "background=#228991ff"
            }]
        }
    });
}
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="booleanField"
  columnSet="booleanColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="griddata1.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}