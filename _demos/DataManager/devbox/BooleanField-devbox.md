#### booleanFormat

셀 에디터의 booleanFormat 속성은 `"false,f:true:0"`과 같은 콜론(:)으로 구분한 형식으로 지정합니다. 

* 첫번째 마디는 false로 해석될 값들을 지정합니다.   
* 두번째 마디에는 true로 해석할 값들을 지정합니다.  
* 세번째 마디에는 대소문자를 구분해야 하는 경우 1, 구분 없이 해석할 경우에는 0을 입력합니다. 


#### booleanFormat 설정

"Values"컬럼을 제외한 각각의 필드에는 원시값을 Boolean 값으로 변환하기 위한 booleanFormat 속성이 지정됐습니다. 
또한, 각각의 "Boolean" 컬럼에게는 스타일의 booleanFormat 속성과 에디터의 booleanFormat이 지정됐습니다.

```js
//필드 설정
var fields = [{
    fieldName: "Boolean1",
    dataType: "boolean",
    booleanFormat: "False,N,0:True,Y,1:0"
}];

dataProvider.setFields(fields);

//컬럼 설정
var columns = [{
    fieldName: "Boolean1",
    width: "120",
    header: {
        text: "Boolean 1"
    },
    editor: {
        booleanFormat: "거짓,f,false:참,t,true:0",
        emptyValue: false
    },
    styles: {
        booleanFormat: "거짓:참"
    }
}];

gridView.setColumns(columns);
```