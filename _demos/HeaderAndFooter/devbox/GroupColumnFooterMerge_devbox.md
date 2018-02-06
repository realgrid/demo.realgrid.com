#### 그룹컬럼 푸터 병합

그룹컬럼 푸터 병합은 동일한 columnGroup에 있으며 group.orientation 설정이 horizental인 경우에만 그룹컬럼 푸터 병합 기능을 사용할 수 있습니다.  
`ProductName, Quantity 컬럼을 서로 다른 그룹이기 때문에 병합을 할 수 없습니다.`

<a class="btn primary small round lowercase" id="btnSetFooterMerge">GroupIds Footer Cell 병합</a>  

```js
gridView.setFooter({
    mergeCells: [
        ["OrderID", "CustomerID", "EmployeeID"]
    ]
});
```

<a class="btn primary small round lowercase" id="btnSetFooterMergeRelease">병합 해제</a>  

```js
gridView.setFooter({
    mergeCells: [
        []
    ]
});
```

<script>
$('#btnSetFooterMerge').click(function() {
    gridView.setFooter({
        mergeCells:
            [
                ["OrderID", "CustomerID", "EmployeeID"]
            ]
    });
});

$('#btnSetFooterMergeRelease').click(function() {
    gridView.setFooter({
        mergeCells:
            [
                []
            ]
    });
});


</script>