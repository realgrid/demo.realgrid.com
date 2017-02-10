
#### 대량 데이터    

csv 형태의 50만건 데이터를 불러옵니다. RealGrid는 행의 제한은 없습니다. 다만 브라우저의 운용 메모리 범위에서 데이터를 처리할 수 있으므로
불러온 데이터의 크기가 크면 브라우저의 가용 메모리가 줄어들고 따라서 개인 사용 환경에 따라 다르겠지만 대량의 데이터를 여러번 반복적으로
가져온다면 브라우저 메모리 풀에 의해 성능이 저하되거나 응답 없음 오류를 발생하기도 합니다.

대량 데이터를 처리하는 일은 Client만의 문제가 아닌 서버에서 대량 쿼리를 처리할 수 있는지 여부도 중요하므로
프로젝트에 성격과 상황에 따라 그 양을 제한할 필요가 있습니다.

<a class="btn primary small round lowercase" id="fillCsvData1">대량 데이터 로드</a>

```js
gridView.showProgress();

var startTime = new Date().getTime();
$.ajax({
    url: "/resource/data/TooLargeDataSet.csv?__time__=" + startTime,
    success: function (data) {
        dataProvider.fillCsvData(data, {});

        var count = dataProvider.getRowCount();
        var ellapse = (new Date().getTime() - startTime) / 1000;
        $("#loadResult").css("color", "green").text(parseInt(count).toLocaleString() + " rows loaded. " + ellapse + " elapsed").show();
        gridView.setFocus();
    },
    error: function (xhr, status, error) {
        $("#loadResult").css("color", "red").text("Load failed: " + error).show();
        $("#btnLoad").removeAttr("disabled");
    },
    complete: function (data) {
        gridView.closeProgress();
    },
    xhr: function () {
        var xhr = new window.XMLHttpRequest();
        //Download progress
        xhr.addEventListener("progress", function (evt) {
            if (evt.lengthComputable) {
                gridView.setProgress(0, evt.total, evt.loaded);
            }
        }, false);
        return xhr;
    }
});
```

<script>

$('#fillCsvData1').click(function() {
  gridView.showProgress();

  var startTime = new Date().getTime();
  $.ajax({
      url: "/resource/data/TooLargeDataSet.csv?__time__=" + startTime,
      success: function (data) {
          dataProvider.fillCsvData(data, {});

          var count = dataProvider.getRowCount();
          var ellapse = (new Date().getTime() - startTime) / 1000;
          $("#loadResult").css("color", "green").text(parseInt(count).toLocaleString() + " rows loaded. " + ellapse + " elapsed").show();
          gridView.setFocus();
      },
      error: function (xhr, status, error) {
          $("#loadResult").css("color", "red").text("Load failed: " + error).show();
          $("#btnLoad").removeAttr("disabled");
      },
      complete: function (data) {
          gridView.closeProgress();
      },
      xhr: function () {
          var xhr = new window.XMLHttpRequest();
          //Download progress
          xhr.addEventListener("progress", function (evt) {
              if (evt.lengthComputable) {
                  gridView.setProgress(0, evt.total, evt.loaded);
              }
          }, false);
          return xhr;
      }
  });
});

$('#fillCsvData2').click(function() {
  var data = ' \
    "국산", "국산", "2", "기아", "15", "더 뉴 K9", "9", "미드나이트 블랙", "2016/01/01", 16, 8620, "대형", "휘발유", "images/215.png", "images/215.png" \n\r \
    "국산", "국산", "5", "르노삼성", "2", "QM6", "3", "이온 실버", "2016/01/01", 71, 3470, "중형SUV", "휘발유", "images/502.png", "images/502.png" \
    ';

  dataProvider.fillCsvData(data, {fillMode: "append", quoted: true});
});

$('#fillCsvData3').click(function() {
  var data = ' \
    "head1", "head2", "head3", "head4", "head5", "head6", "head7", "head8" \n\r \
    "국산", "국산", "2", "기아", "15", "더 뉴 K9", "9", "미드나이트 블랙", "2016/01/01", 16, 8620, "대형", "휘발유", "images/215.png", "images/215.png" \
    ';

  dataProvider.fillCsvData(data, {fillMode: "append", quoted: true, start: 1});
});

$('#fillCsvData4').click(function() {
  var data = ' \
    "국산"\t "국산"\t "5"\t "르노삼성"\t "2"\t "QM6"\t "3"\t "이온 실버"\t "2016/01/01"\t 71\t 3470\t "중형SUV"\t "휘발유"\t "images/502.png"\t "images/502.png" \
    ';

  dataProvider.fillCsvData(data, {fillMode: "append", quoted: true, delimiter: "\t"});
});
</script>
