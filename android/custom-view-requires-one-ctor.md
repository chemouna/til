
## Android Custom View requires only one constructor

For an Android custom view to work it requires only on constructor, no need to override all 
the framework constructor just override : 
```java 
  
  public MyView(Context context, AttributeSet attrs) {
    super(context, attrs);
    init();
  }

```
