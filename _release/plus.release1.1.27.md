---
layout: page
title: RealGridPlus Release 1.1.27
releaseDate: 2016-03-22
version: 1.1.27.2635
sidebar: false
---

- 셀 데이터에 따옴표가 들어 있는 경우 다중 행을 복사 후 붙여넣을 때 따옴표 사이의 데이터가 하나의 셀로 인식되는 문제를 개선하기 위해 복사/붙여넣기 로직을 개선하였습니다.
- 엑셀 Export시 윤달을 포함한 3월달에 날짜가 하루씩 앞당겨지는 문제를 개선하였습니다.
- RowGroupOptions.mergeMode가 true일 때 여러 컬럼을 Grouping한 상태에서 엑셀 Export시 RowGroup의 Header,Footer행의 상위level에 해당하는 컬럼에 경계선이 다르게 표시되는 문제를 개선하였습니다.
- Row Grouping한 상태에서 컬럼의 경계선을 더블클릭하거나 fitColumnWidth() 함수를 이용해 컬럼 fitting하는 경우 발생하는 오류를 개선하였습니다.
- Validation Error표시할 때 순수한 Validation Message만 표시하도록 수정하였습니다.
