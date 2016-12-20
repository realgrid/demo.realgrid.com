#### 토스트 메시지창 설정
그리드의 sorting, filtering, grouping 옵션에 아래와 같은 속성을 갖는 toast 옵션을 추가로 지정하면 됩니다. 
기본 설정값은 Toast View를 표시하지 않는 것입니다.

현재 토스트 메시지창이 설정되어 있지 않기 때문에 소트나 그룹핑, 필터링시 아무 메시지창이 표시 되지 않습니다. `토스트 메시지창 설정` 버튼을 클릭한 후 확인해 보세요.    

<a class="btn primary small round lowercase" id="btnSetToastView">토스트 메시지창 설정</a>

```js
gridView.setOptions({
  sorting: {
    toast: {
      visible: true,
      message: "정렬 중입니다..."
    }
  },
  filtering: {
    toast: {
      visible: true,
      message: "필터링 중입니다..."
    }
  },
  grouping: {
    toast: {
      visible: true,
      message: "그룹핑 중입니다..."
    }
  }
});
```

<script>

  $('#btnSetToastView').click(function() {
    gridView.setOptions({
      sorting: {
        toast: {
          visible: true,
          message: "정렬 중입니다..."
        }
      },
      filtering: {
        toast: {
          visible: true,
          message: "필터링 중입니다..."
        }
      },
      grouping: {
        toast: {
          visible: true,
          message: "그룹핑 중입니다..."
        }
      }
    });
  });
</script>
