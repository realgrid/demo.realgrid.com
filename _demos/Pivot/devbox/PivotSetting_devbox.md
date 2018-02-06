
#### 피벗필드 재설정

pivot 화면을 구성할 값들을 선택 후 버튼 클릭 시 피벗필드를 재설정 합니다.

<a class="btn primary small round lowercase" id="btnSetPivot">피벗 필드 재설정</a>

---

- columns 설정

<form name="columnsFrm">
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="checkbox" name="columnsBox"  value="판매년도" checked="checked"/>&nbsp;판매년도<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="checkbox" name="columnsBox" value="판매분기" checked="checked"/>&nbsp;판매분기<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="checkbox" name="columnsBox" value="판매월"/>&nbsp;판매월<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="checkbox" name="columnsBox" value="판매요일"/>&nbsp;판매요일<br>
</form>

---

- rows 설정

<form name="rowsFrm">
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="checkbox" name="rowsBox" value="국가" checked="checked"/>&nbsp;국가<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="checkbox" name="rowsBox" value="브랜드명" checked="checked"/>&nbsp;브랜드명<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="checkbox" name="rowsBox" value="차종" checked="checked"/>&nbsp;차종<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="checkbox" name="rowsBox"  value="연료"/>&nbsp;연료<br>
</form>

---

- values 설정

<form name="valuesFrm">
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="checkbox" name="valuesBox" value="차량가격" checked="checked"/>&nbsp;차량가격
	<select name="valueType">
	    <option value="sum">sum</option>
	    <option value="count">count</option>
	    <option value="min">min</option>
	    <option value="max">max</option>
	    <option value="average">average</option>
	    <option value="DISTINCT">distinct</option>
	</select>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="checkbox" name="valuesBox" value="판매수량" checked="checked"/>&nbsp;판매수량
	<select name="valueType">
	    <option value="sum">sum</option>
	    <option value="count">count</option>
	    <option value="min">min</option>
	    <option value="max">max</option>
	    <option value="average">average</option>
	    <option value="DISTINCT">distinct</option>
</form>

***


<script>

function columnsCheck(){
	var columnsArr = []


	for(var i = 0; i < columnsFrm.columnsBox.length; i++)
	{
		if(columnsFrm.columnsBox[i].checked)
		{
			columnsArr.push(columnsFrm.columnsBox[i].value);
		}
	}


	if(columnsArr.length == 0){ 
		alert("하나 이상의 columns 목록을 체크해야 합니다.")
		return false
	}

	return columnsArr;
}
function rowsCheck(){
	var rowsArr = []
	 
	for(var i = 0; i < rowsFrm.rowsBox.length; i++)
	{
		if(rowsFrm.rowsBox[i].checked)
		{
			rowsArr.push(rowsFrm.rowsBox[i].value);
		}
	}

	if(rowsArr.length == 0){ 
		alert("하나 이상의 rows 목록을 체크해야 합니다.")
		return false
	}

	return rowsArr;
}
function valuesCheck(){
	var valuesArr = [];
	for(var i = 0; i < valuesFrm.valuesBox.length; i++)
	{
		if(valuesFrm.valuesBox[i].checked)
		{
			valuesArr.push({name:valuesFrm.valuesBox[i].value, expression:valuesFrm.valueType[i].value});
		}
	}

	if(valuesArr.length == 0){ 
		alert("하나 이상의 values 목록을 체크해야 합니다.")
		return false
	}

	return valuesArr;
}

	$('#btnSetPivot').click(function() {
		if(columnsCheck() == false || rowsCheck() == false || valuesCheck() == false){

		} else {
			pivot.setPivotFields({
		        columns: columnsCheck(),
		        rows: rowsCheck(),
		        values: valuesCheck()
		    });
		}
    });
</script>