# scss

## 자주 사용하는 것

### 1. 공통으로 사용하는 것들은 index에 import 시켜 사용하자.

<img width="248" alt="스크린샷 2022-07-19 오후 11 28 24" src="https://user-images.githubusercontent.com/71499150/179775352-1fed1e1b-d8ca-400f-b41e-1f5a5534075d.png">
<img width="214" alt="스크린샷 2022-07-19 오후 11 28 18" src="https://user-images.githubusercontent.com/71499150/179775376-b80bee8f-2200-4e16-9b9c-7b73f388f9f4.png">

나같은 경우는 자주 사용하는 컬러들은 hex 코드나 rgba 컬러 색상으로 정리해서 모아놓고 필요시 import 시켜 때에 따라 변수로 담은 컬러들을 골라 사용한다.
<img width="334" alt="스크린샷 2022-07-19 오후 11 28 52" src="https://user-images.githubusercontent.com/71499150/179775708-9bb6e4d3-59e1-4d98-a809-734e9c1ee7e2.png">

### mixin

```
@import 'commonColor';

@mixin center {
    display: flex;
    justify-content: center;
    align-items: center;
}

// table 스타일. 기본 너비는 100%
@mixin table($width: 100%, $bgColor: $tableTitle, $borderLine: $borderLine) {
    margin-bottom: 2rem;
    tr {
        border: 1px solid $borderLine;
        .tb--title {
            padding: 2rem;
            background-color: $bgColor;
            width: 10%;
            font-size: 1rem;
        }
        td {
            width: 90%;
            border: 1px solid $borderLine;
            input {
                width: 100%;
            }
        }
    }
}

```

자주 사용되는 레이아웃과 가운데 정렬해주는 스타일을 mixin로 담아놓고 아래와 같이 사용한다.

```
.common-grid--layout {
    @include table;
}
```

사용할 때는 `@include` 를 써서 쓸 수 있다.

------------------------------------

