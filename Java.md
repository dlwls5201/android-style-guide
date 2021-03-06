# Java

아래 정의되어 있는 가이드외에는 [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html)를 따른다.

## Parameter/Argument
### Parameter 순서
- Context류의 parameter를 가장 앞에 위치한다.
(Context, Activity, Fragment, View등)
- Callback류의 parameter를 가장 뒤에 위치한다.
(XXXListener, XXXCallback, XXXSubject등)
```java
public Car getCar(Context context, int hashId);
public void loadCar(Context context, int hashId, CarListener listener);
```

### Key

| Prefix | 설명 |
| ------------- | ------------- |
| `EXTRA_` | Intent |
| `PREF_` | SharedPreferences |
| `ARGUMENT_` | Fragment Arguments |

- Key-Value로 활용되는 컴포넌트들의 Key는  `static final`로 정의한다.
- Key로 정의된 이름의 String값은 동일하게 맞춰준다.

```java
public static final String EXTRA_HASH_ID = "EXTRA_HASH_ID";
public static final String EXTRA_TRADE = "EXTRA_TRADE";
```

### Key with Activity/Fragment
#### Activity
- Activity Intent에 `EXTRA_`를 넣어주는 경우, 해당 Activity에 `startActivity()` 혹은 `getIntent()`를 구현하고 이를 사용한다.
```java
public static void startActivity(Context context, @DrawableRes int photoResourceId) {  
  Intent intent = new Intent(context, PhotoDetailActivity.class);  
  intent.putExtra(EXTRA_PHOTO_RESOURCE_ID, photoResourceId);  
  context.startActivity(intent);  
}
```
```java
public static Intent getIntent(Context context, String brandId, String brandName) {  
  Intent intent = new Intent(context, SelectCarActivity.class);  
  intent.putExtra(EXTRA_BRAND_ID, brandId);  
  intent.putExtra(EXTRA_BRAND_NAME, brandName);  
  return intent;  
}
```
#### Fragment
- Fragment에 `ARGUMENT_`를 넣어주는 경우, 해당 Fragment에 `newInstance()`를 구현하고 이를 사용한다.
- Fragment 생성자의 Parameter로 넘기지 않는다.
[Best Practice to Instantiate Fragments with Arguments in Android](https://gunhansancar.com/best-practice-to-instantiate-fragments-with-arguments-in-android/)
```java
public static UserFragment newInstance(User user) {
	UserFragment fragment = new UserFragment();
	Bundle args = new Bundle();
	args.putParcelable(ARGUMENT_USER, user);
	fragment.setArguments(args)
	return fragment;
}
```
#### 기타
- `startActivity()` / `getIntent()` / `newInstance()`에서 쓰이는 Key는 항상 `private static final`로 만든다.


### Parameter
- Parameter개수가 많아서 줄바꿈이 필요한 경우, **`,`다음부터 줄바꿈한다.**
```java
public InputSingleTextView(Context context,  
  @RegisterStep String step,  
  String hint,  
  String validationMessage,  
  @NonNull CompleteListener completeListener) {  
  ...
}
```
- 줄바꿈이 필요한 부분부터 줄바꿈 하지 않고 위의 예시처럼 1개 단위로 줄바꿈을 해준다.
- 이런 함수를 호출하는 코드에서도 같은 패턴으로 맞춰서 호출한다.
```java
new InputSingleTextView(this,
   RegisterStep.XXX,
   getString(R.string.xxx),
   getString(R.string.xxx),
   completeListener);
```


### Operator
- 많은 operator의 연산으로 줄바꿈이 필요한 경우, **operator 전에 줄바꿈한다.**
```java
int longName = anotherVeryLongVariable + anEvenLongerOne - thisRidiculousLongOne
        + theFinalOne;
```
- 연산자의 경우는 줄바꿈이 필요한 위치부터 줄바꿈한다.

### Method chain
- Builder/RxJava 등 여러 함수를 chaining으로 사용하면서 줄바꿈이 필요한 경우, **`.`전에 줄바꿈한다.**
```java
ImageLoader.load(user.getProfileUrl())  
        .placeholder(R.drawable.img_user_placeholder)  
        .fitCenter()  
        .into(binding.ivUser);
```

## Util/Helper
- 특정기능을 수행하거나 상태를 관리하거나 분리되어 동작을 수행하는 클래스에 대한 사용처별 이름을 정의한다.

### Util
- `public static void AAA`등으로 쓰이는 여러곳에서 사용되는 util성 기능을 보아둔 클래스
- `aa.bb.cc.util` 패키지에 모두 모아둔다.
- 예) `DateFormatUtil`, `PixelUtil`, `BitmapUtil`등

### Helper
- 특정 패키지나 기능에서 한정되어 사용되는 `public static void AAA` 클래스
- 공통으로 쓰이지 않고 특정 기능의 코드를 분리하기 위한 용도로 사용한다.
- 비즈니스 로직을 갖고 있는 Util이라고 생각하면 된다.
- 예) `NotificationChannelHelper`등
