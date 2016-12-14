---
layout: page
title: 날짜 타입 필드
order: 4
devbox: true
devboxfile: DatetimeField-devbox.md
published: true
categories:
  - 데이터 관리
tags: ['data', 'date', 'datetime', 'time']
---

DataProvider로 로드하거나, 편집기를 통해 Datetime 필드의 값을 입력할 때 또는, 렌더러가 Datetime 필드 값을 표시할 때는 적절한 변환 형식을 설정하고 설정된 형식으로 데이터를 표시합니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
	var data = [
        ["20141114", "20141114PM051215008", "20141114171215008", "2014/11/14 17:12", "2014-11-14T17:12:15+09:00"],
        ["20141115", "20140304AM040805556", "20140304040805556", "2014/03/04 04:08", "2014-03-04T04:08:05+09:00"],
        ["20010215", "20010215PM124236721", "20010215124236721", "2001/02/15 12:42", "2001-02-15T12:42:36+09:00"],
        ["20111025", "20111025AM103637426", "20111025103637426", "2011/10/25 10:36", "2011-10-25T10:36:37+09:00"],
        ["20070626", "20070626PM030456962", "20070626150456962", "2007/06/26 15:04", "2007-06-26T15:04:56+09:00"],
        ["20040807", "20040807AM013302430", "20040807013302430", "2004/08/07 01:33", "2004-08-07T01:33:02+09:00"],
        ["20050530", "20050530AM105829932", "20050530105829932", "2005/05/30 10:58", "2005-05-30T10:58:29+09:00"],
        ["20071030", "20071030AM083042626", "20071030083042626", "2007/10/30 08:30", "2007-10-30T08:30:42+09:00"],
        ["20030629", "20030629PM063304071", "20030629183304071", "2003/06/29 18:33", "2003-06-29T18:33:04+09:00"],
        ["20130807", "20130807PM082825025", "20130807202825025", "2013/08/07 20:28", "2013-08-07T20:28:25+09:00"]
    ];

	dataProvider.setRows(data);
}
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="datetimeField"
  columnSet="datetimeColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="griddata1.json"
  successDataSet="onGridSuccessDataSet"

  gridWidth="100%"
  gridHeight="300px" %}