
#### 원격(Remote) 데이터 로드

[jQuery.ajax()](http://api.jquery.com/jquery.ajax/)함수를 이용해 원격 데이터를 가져오는
코드를 작성해 보겠습니다.

<a class="btn primary small round lowercase" id="loadRemoteData">원격 데이터 가져오기</a>

```js
// 원격 데이터를 다운로드 하는 동안 프로그래스바를 표시합니다.
treeView.showProgress();

// jQuery ajax() 함수 호출
$.ajax({
    type: "GET",
    url: "http://" + location.host + "{{'/resource/data/' | prepend: site.baseurl}}treedata3.json?__time__=" + new Date().getTime(),
    dataType: "text",
    success: function (data) {
      // 원격 데이터를 비동기로 가져온 경우 호출 되는 콜백
      treeDataProvider.fillJsonData(data, { rows: "rows", icon: "icon" });
      treeView.setFocus();
    },
    error: function (xhr, status, error) {
      // 원격 데이터를 비동기로 가져오는 동안 오류가 발생하면 호출 되는 콜백
      alert(error);
    },
    complete: function (data) {
      // ajax()함수 호출이 완료되면 호출 되는 콜백
      treeView.closeProgress();
    },
    xhr: function () {
        var xhr = new window.XMLHttpRequest();

        // xhr 요청 정보를 이용해 progress 이벤트 리스너 등록
        xhr.addEventListener("progress", function (evt) {
            if (evt.lengthComputable) {
              treeView.setProgress(0, evt.total, evt.loaded);
            }
        }, false);

        return xhr;
    }
});
```

RealGrid의 기반 클래스인 GridBase의
[showProgress()](http://help.realgrid.com/api/GridBase/showProgress/)함수를 사용하면
원격에서 데이터를 가져오는 동안 프로그래스바(Progress Bar)를 보여줄 수 있습니다.

위 버튼을 클릭하면 원격 데이터를 가져오는 동안 프로그래스바(Progress Bar)가 표시 되는데, 이
<mark>프로그래스바(Progress Bar)는 그리드나 트리에 데이터가 입력되는 진행상태가 아니라 원격에 있는 데이터를
비동기로 가져오는 동안 네트워크 진행상태를 의미 합니다.</mark>

자세한 내용은 [jQuery.ajax()](http://api.jquery.com/jquery.ajax/)함수 페이지를 참조하세요.


<script>
$('#loadRemoteData').click(function() {
  treeDataProvider.onLoadCompleted = function (provider) {
        console.log("Data loaded.");
    }

  treeView.showProgress();
  $.ajax({
      type: "GET",
      url: "http://" + location.host + "{{'/resource/data/' | prepend: site.baseurl}}treedata3.json?__time__=" + new Date().getTime(),
      dataType: "text",
      success: function (data) {
          treeDataProvider.fillJsonData(data, { rows: "rows", icon: "icon" });

          treeView.expand(1);
          treeView.expand(0);

          treeView.setFocus();
      },
      error: function (xhr, status, error) {
          alert(error);
      },
      complete: function (data) {
          treeView.closeProgress();
      },
      xhr: function () {
          var xhr = new window.XMLHttpRequest();
          //Download progress
          xhr.addEventListener("progress", function (evt) {
              if (evt.lengthComputable) {
                treeView.setProgress(0, evt.total, evt.loaded);
              }
          }, false);
          return xhr;
      }
  });
});
</script>
