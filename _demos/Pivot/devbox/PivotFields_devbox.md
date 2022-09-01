#### 피벗 설정 정보 확인

현재 피벗이 어떤 설정으로 적용되어 있는지 한번에 확인할 수 있다.
<a class="btn primary small round lowercase" id="btnGetPivotFields">피벗 정보 가져오기</a>

extend인자 값이 true이면 columns, rows, values를 객체배열형태로 가져온다.  
false이면 columns, rows는 해당 field의 이름만 배열형태로 가져온다.

```js
alert(JSON.stringify(pivot.getPivotFields(true)));
//pivot.getPivotFields(false)
```


<script>
	$('#btnGetPivotFields').click(function() {	
	    alert(JSON.stringify(pivot.getPivotFields(true)));
    });
</script>