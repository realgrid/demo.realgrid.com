#### 푸터 병합

- `rowGroup.footerCellMerge`: GroupFooter의 그룹핑 컬럼들의 Cell을 Merge합니다.
- `footer.cellMerge`: Footer내 특정 Cell들을 Merge합니다.

```js
grid.setRowGroup({
    footerCellMerge: true
});

grdMain.setFooter({
    mergeCells: [
            ["QuantityPerUnit Column", "Country Column", "CompanyName Column", "Order Column"],
            ["UnitPrice Column", "Customer Column"]
        ]
});
```


<a class="btn primary small round lowercase" id="btnSetGroupFooterMerge">그룹핑 컬럼 Cell 병합</a>
```js
  gridView.setRowGroup({ footerCellMerge: true });  
```

<a class="btn primary small round lowercase" id="btnSetFooterMerge">Footer Cell 병합</a>
```js
  gridView.setFooter({
            mergeCells:
                [
                    ["QuantityPerUnit Column", "Country Column", "CompanyName Column", "Order Column"],
                    ["UnitPrice Column", "Customer Column"]
                ]
        });
```

Help 사이트의 [summary Mode](http://help.realgrid.com/api/types/SummaryMode/){:target="_blank"} 참고 바랍니다.  

<script>

  $('#btnSetGroupFooterMerge').click(function() {
    gridView.setRowGroup({ footerCellMerge: true });  
  });

  $('#btnSetFooterMerge').click(function() {
    gridView.setFooter({
                mergeCells:
                    [
                        ["QuantityPerUnit Column", "Country Column", "CompanyName Column", "Order Column"],
                        ["UnitPrice Column", "Customer Column"]
                    ]
            });
  });

</script>
