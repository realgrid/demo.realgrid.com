#### 날짜 타입

날짜 기준 선택<br/>
<select id="typeList">
  <option value="type1">판매년도</option>
  <option value="type2">판매년도 - 판매분기</option>
  <option value="type3">판매년도 - 판매분기 - 판매월</option>
  <option value="type4">판매년도 - 판매월 - 판매월주차</option>
</select>


적용 버튼 클릭 시 선택된 날짜 기준으로 pivot화면을 재구성합니다.<br/>
<a class="btn primary small round lowercase" id="btnSetPivotFields">적용</a>

<script>
$('#btnSetPivotFields').click(function() {
	var typeValue = $("#typeList").val();     
	if (typeValue == "type1") {
	    pivot.setPivotFields({
		    columns: ["판매년도"],
		    rows: ["국가","브랜드명"],
		    values: [{
		        name: "차량가격",
		        expression: "sum"
		    }, {
		        name: "판매수량",
		        expression: "sum"
		    }]
		});
	}else if(typeValue == "type2"){
		pivot.setPivotFields({
		    columns: ["판매년도","판매분기"],
		    rows: ["국가","브랜드명"],
		    values: [{
		        name: "차량가격",
		        expression: "sum"
		    }, {
		        name: "판매수량",
		        expression: "sum"
		    }]
		});
	}else if(typeValue == "type3"){
		pivot.setPivotFields({
		    columns: ["판매년도","판매분기","판매월"],
		    rows: ["국가","브랜드명"],
		    values: [{
		        name: "차량가격",
		        expression: "sum"
		    }, {
		        name: "판매수량",
		        expression: "sum"
		    }]
		});
	}else if(typeValue == "type4"){
		pivot.setPivotFields({
		    columns: ["판매년도","판매월","판매월주차"],
		    rows: ["국가","브랜드명"],
		    values: [{
		        name: "차량가격",
		        expression: "sum"
		    }, {
		        name: "판매수량",
		        expression: "sum"
		    }]
		});
	}
});

/*
$('#btnSetPivotFields1').click(function() {
	pivot.setPivotFields({
	    columns: ["판매년도"],
	    rows: ["국가","브랜드명"],
	    values: [{
	        name: "차량가격",
	        expression: "sum"
	    }, {
	        name: "판매수량",
	        expression: "sum"
	    }]
	});
});
$('#btnSetPivotFields2').click(function() {
	pivot.setPivotFields({
	    columns: ["판매년도","판매분기"],
	    rows: ["국가","브랜드명"],
	    values: [{
	        name: "차량가격",
	        expression: "sum"
	    }, {
	        name: "판매수량",
	        expression: "sum"
	    }]
	});
});
$('#btnSetPivotFields3').click(function() {
	pivot.setPivotFields({
	    columns: ["판매년도","판매분기","판매월"],
	    rows: ["국가","브랜드명"],
	    values: [{
	        name: "차량가격",
	        expression: "sum"
	    }, {
	        name: "판매수량",
	        expression: "sum"
	    }]
	});
});
$('#btnSetPivotFields4').click(function() {
	pivot.setPivotFields({
	    columns: ["판매년도","판매분기","판매월","판매월주차"],
	    rows: ["국가","브랜드명"],
	    values: [{
	        name: "차량가격",
	        expression: "sum"
	    }, {
	        name: "판매수량",
	        expression: "sum"
	    }]
	});
});
*/
</script>