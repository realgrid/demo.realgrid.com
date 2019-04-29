#### 피벗 포커스 설정
  
[DisplayOptions.showFocus](http://help.realgrid.com/pivotApi/types/DisplayOptions/){:target="_blank"}속성으로 포커스를 표시하고 키보드로 이동할 수 있습니다. 
포커스가 위한 행과 열에 가이드 라인을 표시할 수 있습니다.   
다음과 같이 setDisplayOptions() 함수를 통해 포커스를 활성화할 수 있습니다.

<a class="btn primary small round lowercase" id="btnSetDisplayOptions">포커스 표시</a>

```
pivot.setDisplayOptions({showFocus:true, showFocusGuide:true})
pivot.drawView();
```

#### 피벗 포커스 이벤트

포커스가 이동될때 [onCurrentChanged](http://help.realgrid.com/pivotApi/RealPivot/onCurrentChanged/){:target="_blank"} 콜백이 발생합니다.  

```
pivot.onCurrentChanged = function (pivot, index) {
    console.log(index); 
}
```

<script>
$('#btnSetDisplayOptions').click(function() {
	pivot.setDisplayOptions({showFocus:true, showFocusGuide:true})
	pivot.drawView();
});

</script>