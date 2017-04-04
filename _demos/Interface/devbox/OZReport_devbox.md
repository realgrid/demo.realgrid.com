#### 리포트 페이지에 데이터 전달

출력 미리보기 버튼 클릭 시 리포트 페이지에 표시될 getOutputRows()함수로 그리드에서 가져온 데이터를 팝업되어 보여질 리포트 페이지에 전달합니다.

**ozGroupSample.html**

```js
function preview() {
    var popup = window.open("http://URL/oz70/ozGroup.html", "open", "height=900,width=1300,resizable=yes");
    popup.sampleData = JSON.stringify(dataProvider.getOutputRows({datetimeFormat: "yyyy/MM/dd"}));
}
```


#### 리포트 서버에 데이터 채우기 및 화면 출력

리포트 서버에 등록된 리포트 양식에 전달받은 데이터로 채워 리포트 화면을 출력합니다.

**ozGroup.html**

```js
var gridData = sampleData;

function SetOZParamters_OZViewer(){
    var oz;
    oz = document.getElementById("OZViewer");
    oz.sendToActionScript("connection.servlet","http://URL/oz70/server");
    oz.sendToActionScript("connection.reportname","ozGroup.ozr");
    oz.sendToActionScript("connection.pcount", "1");
    oz.sendToActionScript("connection.args1",  "jsondata={'sample':" + gridData + " }");

    return true;
}
start_ozjs("OZViewer","http://URL/oz70/ozhviewer70/");
```