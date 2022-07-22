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

## style.module.scss 모듈 스타일

### JSX

```
import styles from './style.module.scsss';

const App = () => (
  <div className={styles.item}>
    {item}
  </div>
)

```

### style.module.scss

```
.item {
  display: flex;
}
```

이렇게 사용하면 해당 클레스에만 고유하게 `display: flex;` 이 적용된다. 

### SCSS의 단점

일반 scss 파일로 작성하여 import 시킨다면 고유한 클래스명이 아니면 스타일이 겹칠 우려가 있다.
그래서 scss 파일을 Module해서 사용하면 클래스에 해시값이 붙어 고유한 클래스명으로 작업할 수 있다.
즉, 스타일 정의를 각 컴포넌트 단위로 자동으로 겹치지 않게끔 로컬화 할 수 있다는 것이다.
이러한 scss의 단점들을 극복하고자 나온것이 `styled-components`와 `emotion` 이라는 스타일 라이브러리다.
scss를 사용할 때 class명이 겹치지 않도록 해결방안이 `BEM`이다. 이는, class 이름이 길어지고, 길어진 이름을 매번 코드에 입력해가며 관리하는 것도 단점이다. 

### BEM 이란 이렇게 쓰인다.

```
<ul class="menu">     
  <li class="menu__item--disabled">피자</li>     
  <li class="menu__item"/>치킨</li>   
  <li class="menu__item"/>스파게티</li> 
</ul>
```

이처럼 엘리먼트나 블록에 대명사로 지정하고 (= menu) 이 뒤에 `__` 언더바를 사용하여 그에 대한 기능명으로 표기해준다. 
> 예 : `menu__item` // 이렇게 사용. 그리고 더 디테일한 부분에는 `menu__item--red` 이렇게 명명 규칙을 세워 작업하면 유지보수 하기에도 수월하다.


```
import styles from './styles.module.scss';
import classNames from 'classnames/bind';
const cx = classNames.bind(styles);
```
