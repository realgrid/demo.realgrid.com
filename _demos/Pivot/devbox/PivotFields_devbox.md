#### 피벗 설정 정보 확인

현재 피벗이 어떤 설정으로 적용되어 있는지 한번에 확인할 수 있다.
<a class="btn primary small round lowercase" id="btnGetPivotFields">피벗 정보 가져오기</a>

```js
alert(JSON.stringify(pivot.getPivotFields()));
```


<script>
	$('#btnGetPivotFields').click(function() {	
	    alert(JSON.stringify(pivot.getPivotFields()));
    });
</script>