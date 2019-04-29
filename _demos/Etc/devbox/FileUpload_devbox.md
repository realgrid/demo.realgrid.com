#### 파일 업로드

파일 첨부 컬럼의 버튼 클릭 후 첨부할 파일을 선택해서 파일 첨부와 같은 동작을 하도록 설정한 기능을 확인해 보세요.

upload 버튼 클릭 시 아래 값들을 확인 할 수 있습니다.  
*datas  
*selectFiles

```
var selectFiles = {};

//파일 선택창 실행
gridView.onCellButtonClicked = function (grid, itemIndex, column) {
    if (column.name === "fileUpload") {
        var input = document.createElement("input");
        input.type="file"
        input.onchange = function(event) {
            var file = event.currentTarget.files[0];     
            grid.setValue(itemIndex, "fileUpload", file.name);
            selectFiles[file.name] = file;
        };
        input.display = "none";
        input.click();
    }
} 

$("#btnUpload").on("click",function(event) {
    // FormData 인스턴스 생성
    var formData = new FormData();
    formData.method="post";
    formData.enctype = "multipart/form-data";
    for (var fileName in selectFiles) {
    	//파일을 담기 위해서 FormData객체를 사용하였으며 append() 메소드는 전달할 파일이나 다른 데이터를 추가할 수 있습니다.
        formData.append("uploadFiles", selectFiles[fileName]);
    }
    var datas = [];
    var rows = dataProvider.getAllStateRows();
    for (var state in rows) {
        if (state == "createAndDeleted" || state == "none") continue;
        if (rows[state].length > 0) {
            for (var i =0, cnt = rows[state].length; i < cnt ;i++) {
                var data = dataProvider.getJsonRow(rows[state][i]);
                data.__state__ = state;
                datas.push(data);
            }
        };
    };
      
    datas.length > 0 && formData.append("datas", JSON.stringify(datas));
      
    //FormData() Ajax 파일업로드 SUBMIT 스크립트 코드
    //Ajax 파일업로드 SUBMIT 코드는 직접 구현해서 사용해야 합니다.
    var ajaxReq = $.ajax({
        url : './fileupload.do',
        type : 'POST',
        data : formData,
        cache : false,
        contentType : false,
        processData : false,
        xhr: function(){
            //Get XmlHttpRequest object
    
            var xhr = $.ajaxSettings.xhr();
            //Set onprogress event handler
            xhr.upload.onprogress = function(event){
                var perc = Math.round((event.loaded / event.total) * 100);
                $('#progressBar').text(perc + '%');
                $('#progressBar').css('width',perc + '%');
            };
            return xhr ;
        },
        beforeSend: function( xhr ) {
            //Reset alert message and progress bar
            $('#alertMsg').text('');
            $('#progressBar').text('');
            $('#progressBar').css('width','0%');
        },
        success: function(data){
            //업로드 파일 값, 행 상태 초기화
            selectFiles = {};
            dataProvider.clearRowStates(true, false);
        }
    })
});
```