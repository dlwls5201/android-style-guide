# Resource

## Layout
- `<WHAT>_<WHERE>`

### WHAT
| Prefix | 설명 |
| ------------- | ------------- |
| `activity_` | Activity에서 쓰이는 layout |
| `fragment_` | Fragment에서 쓰이는 layout |
| `dialog_` | Dialog에서 쓰이는 layout |
| `view_` | CustomView에서 쓰이는 layout |
| `item_` | RecyclerView, GridView, ListView등에서 ViewHolder에 쓰이는 layout |
| `layout_` | `<include/>`로 재사용되는 공통의 layout |

### 예시
- `activity_main`: MainActivity의 layout
- `fragment_main`: MainFragment의 layout
- `dialog_contact`: Dialog의 layout
- `view_rating`: 커스텀으로 만든 RatingView의 layout
- `item_my_car`: 목록에서 사용되는 각각의 item의 layout
- `layout_dealer_review`: 재사용되는 뷰 layout

## ID
- 코를린 익스텐션 적용을 위헤 카멜 케이스로 네이밍 합니다.
- `<WHAT>_<WHERE>_<DESCRIPTION>`
- View의 대문자를 축약하여 `<WHAT>`의 Prefix로 사용한다.
- 아래 이름규칙을 적용한다.
1. Android의 View는 CamelCase의 대문자를 축약한 형태로 정한다.
</br>: `TextView -> tv`
2. 만약 View의 이름이 Space, Switch와 같이 1개의 대문자만 존재한다면 모두 소문자인 아이디로 정한다.
</br>: `Switch -> switch`
3. CustomView는 전체View의 이름으로 정한다.
</br>: `MyCustomView -> myCustomView`
4. 아래표에 해당 View의 Prefix가 정의되어 있지 않다면 팀에서 상의해서 이름을 정한뒤 추가한다.

### WHAT
| View | Prefix |
| ------------- | ------------- |
| TextView | `tv_` |
| ImageView | `iv_` |
| CheckBox | `cb_` |
| RecyclerView | `rv_` |
| EditText | `et_` |
| ProgressBar | `pb_` |
| NestedScrollView | `nsv_` |
| Space | `space_` |
| Switch | `switch_` |
| FrameLayout | `fl_` |
| LinearLayout | `ll_` |
| ReleativeLayout | `rl_` |
| ConstraintLayout | `cl_` |
| MyCustomView | `my_custom_view` |

### WHERE
- Acitivty, Fragment명 없이 사용되는 곳을 적는다.
</br>: MainActivity이면 Main만 `<where>`에 적어줍니다.
</br>: MainActivity의 제목 용도인 textView 경우 -> `tvMainTitle`

## Drawable
- `<WHAT>(_<WHERE>)_<DESCRIPTION>`
- 이미지가 여러군데에서 활용될 경우, `<WHERE>`는 생략 가능하다.

### What
| Prefix | 설명 |
| ------------- | ------------- |
| `btn_` | 버튼으로 쓰이는 이미지 |
| `ic_` | 버튼이 아닌 화면에 보여지는 이미지 |
| `bg_` | 버튼이 아닌 화면에 보여지는 이미지 |
| `img_` | 실제사진이거나 아이콘형태가 아닌 일러스트형태의 이미지 |
| `div_` | divider로 활용되는 이미지 |
| `rect_` | 네모 모양의 drawable |
| `circle_` | 원 모양의 drawable |

- 공통으로 사용하는 회색 네모인 Drawable
: `rect_gray_rad0`
- 공통으로 사용하는 모서리가 10라운드가 들어간 회색 네모인 Drawable
: `rect_gray_rad10`

## Dimension
- `<WHERE>_<DESCRIPTION>_<WHAT>`

## String
-  `<WHERE>_<DESCRIPTION>`
- 특정화면에서 쓰이는 텍스트 아니라 여러군데에서 공통으로 재사용될 텍스트라면 `<DESCRIPTION>`로 이름을 짓는다

### 예시
- `permission_dialog_camera_title`: 카메라권한을 요구하는 Dialog의 제목
- `permission_dialog_camera_description`: 카메라권한을 요구하는 Dialog의 설명내용
- `yes`: 네
- `ok_understand`: 여러 Dialog에서 `네, 알겠습니다`로 쓰이는 공통의 텍스트

### 문단
- 문단형태의 긴 문자열로 개행(`\n`)이 필요한 경우, `\n`을 다음줄의 앞에 쓴다.
```xml
 <string name="sample">문단 첫번째줄
        \n문단 두번째줄
        \n문단 세번째줄</string>
````
