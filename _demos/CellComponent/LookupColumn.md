---
layout: page
title: Lookup 컬럼
order: 5
devbox: true
devboxfile: LookupColumn-devbox.md
categories:
  - 셀 구성요소
tags: ['LookupColumn', 'Lookup', 'label']
---

컬럼에 연결된 데이터 필드의 실제 값 대신 그 값과 연관된 다른 값을 셀에 표시할 수 있습니다.

<script>
	var onDoneDataSet = function() {
		var rows = [
	        ["user1", "HANAR", "28", "Male", "001-0002-0001", "user1@gmail.com", "<28>"],
	        ["user3", "HANAR", "25", "Male", "001-0002-0003", "user3@gmail.com", "<25>"],
	        ["user6", "HANAR", "21", "Female", "001-0002-0006", "user6@gmail.com", "<21>"],
	        ["user2", "VICTE", "25", "Male", "001-0002-0002", "user2@gmail.com", "<25>"],
	        ["user4", "VICTE", "38", "Male", "001-0002-0004", "user4@gmail.com", "<38>"],
	        ["user5", "THREE", "55", "Male", "001-0002-0005", "user5@gmail.com", "<55>"],
	        ["user7", "SEVEN", "44", "Female", "001-0002-0007", "user7@gmail.com", "<44>"],
	        ["user8", "SEVEN", "33", "Female", "001-0002-0008", "user8@gmail.com", "<33>"],
	        ["user9", "SEVEN", "55", "Male", "001-0002-0009", "user9@gmail.com", "<55>"],
	        ["user10", "VINET", "65", "Male", "001-0002-0010", "user10@gmail.com", "<65>"],
	        ["user11", "VINET", "29", "Female", "001-0002-0011", "user11@gmail.com", "<29>"],
	        ["user12", "HANAR", "18", "Female", "001-0002-0012", "user12@gmail.com", "<18>"],
	        ["user13", "SUPRD", "52", "Male", "001-0002-0013", "user13@gmail.com", "<52>"],
	        ["user14", "SUPRD", "61", "Male", "001-0002-0014", "user14@gmail.com", "<61>"],
	        ["user15", "SUPRD", "26", "Female", "001-0002-0015", "user15@gmail.com", "<26>"],
	        ["user16", "THREE", "46", "Male", "001-0002-0016", "user16@gmail.com", "<46>"],
	        ["user17", "THREE", "26", "Female", "001-0002-0015", "user15@gmail.com", "<26>"],
	        ["user18", "THREE", "46", "Male", "001-0002-0016", "user16@gmail.com", "<46>"],
	        ["user19", "VINET", "26", "Female", "001-0002-0015", "user15@gmail.com", "<26>"],
	        ["user20", "VINET", "46", "Male", "001-0002-0016", "user16@gmail.com", "<46>"],
	        ["user21", "VINET", "64", "Male", "001-0002-0017", "user17@gmail.com", "<64>"]
    	];
    	dataProvider.setRows(rows);
	}
</script>

{% include realgrid.html
  gridVar="gridView"
  dpVar="dataProvider"
  fieldSet="lookupField"
  columnSet="lookupColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  doneDataSet="onDoneDataSet"
  styleSet="style1"
  dataSet="griddata1"
  gridId="realgrid"
  gridWidth="100%"
  gridHeight="300px" %}