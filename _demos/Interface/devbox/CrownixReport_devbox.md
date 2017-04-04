#### 리포트 페이지에 데이터 전달

미리보기 버튼 클릭 시 리포트 데이터를 생성하고 생성된 데이터를 리포트 페이지에 전달합니다.

**m2soft_report.html**

```js
// 리포팅 데이터 생성
function dataProduction() {
    var dataValue = "";
    var count = dataProvider.getRowCount();
    for (var i = 0; i < count; i++){
        idx = gridView.getDataRow(i);
        dataValue += dataProvider.getValues(idx) + "," + "\n";
    }
    // 최종 리포트 데이터
    reportingData = dataValue;
} 

// 출력 미리보기
function preview() {
	var f = document.reportingForm;

    dataProduction();
	var Report_Data = reportingData;

	f.R_data.value = encodeURIComponent(Report_Data);
	f.action = "http://URL/preview.jsp";
    f.target = "";
	f.submit();
}

// 출력 팝업 미리보기
function popupPreview() {
    var f = document.reportingForm;
    var cellStyle = gridView.getColumnProperty(gridView.columnByField("Country"), "styles").background;
    var myWin = window.open('','POP','location=no,status=no,toolbar=no,scrollbars=no,width=1000,height=800');

    dataProduction(); // 리포트 데이터 생성
    var Report_Data = reportingData;

    f.R_data.value = encodeURIComponent(Report_Data);
    f.action = "http://URL/preview.jsp";
    f.target = "POP";
    f.method = "post";
    f.submit();
}
```

#### 리포트 서버에 데이터 채우기 및 화면 출력

리포트 서버에 등록된 리포트 양식에 전달받은 데이터로 채워 리포트 화면을 출력합니다.

**preview.jsp**

```js
var RD_data = decodeURIComponent("<%=R_data%>");
var RD_style = "<%=R_style%>";
window.onload = function(){
    var viewer = new m2soft.crownix.Viewer('http://URL/service', 'crownix-viewer');
    viewer.setRData(RD_data);
    viewer.openFile('gridSample.mrd', '/rnl [^^&]');
};
```