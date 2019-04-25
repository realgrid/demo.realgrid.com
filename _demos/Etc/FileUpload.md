---
layout: page
title: 파일 업로드
order: 1
devbox: true
devboxfile: FileUpload_devbox.md
published: false
categories:
  - 기타
tags: ['업로드', '파일', 'upload', 'file']
---

그리드에 실제 파일이 올라가는것은 아니며 파일 첨부 기능과 같이 동작하도록 구현 할 수 있습니다.

`그리드는 클라이언트단 까지만 지원할 수 있으며 서버 모듈은 직접 구현해서 사용해주셔야 합니다.`

<script>
  var selectFiles = {};
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {    
  	dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {    
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
      var formData = new FormData();
      formData.method="post";
      formData.enctype = "multipart/form-data";
      for (var fileName in selectFiles) {
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
      

      var selectText = "";
      var keys = Object.keys(selectFiles);
      for(var i = 0; i < keys.length; i++){
          selectText += " name: " + selectFiles[keys[i]].name + ", size: " + selectFiles[keys[i]].size + ", type: " + selectFiles[keys[i]].type + "\n"
      }
      alert("datas: \n" + JSON.stringify(datas) + "\nselectFiles: \n" + selectText)

      selectFiles = {};
      dataProvider.clearRowStates(true, false);

      /*
      var ajaxReq = $.ajax({
        url : './insertAnimation.do',
        type : 'POST',
        data : formData,
        cache : false,
        contentType : false,
        processData : false,
        
        xhr: function(){
        //Get XmlHttpRequest object
        
          var xhr = $.ajaxSettings.xhr() ;
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
          selectFiles = {};
          dataProvider.clearRowStates(true, false);
        }
      })
      */
    });
  }
</script>

<input type="button" id="btnUpload" value="upload"><br/>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="fileUploadFields"
  columnSet="fileUploadColumns"
  dpOptionSet="DefaultDataProviderOption"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="MaskEditorData.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}