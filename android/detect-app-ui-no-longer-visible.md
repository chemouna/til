
### Detect when an app ui is hidden

[TRIM_MEMORY_UI_HIDDEN](http://developer.android.com/reference/android/content/ComponentCallbacks2.html#TRIM_MEMORY_UI_HIDDEN) is very handy : parameter of ComponentCallbacks2 onTrimMemory(int level) which indicates that the app passed to the background (since the UI is hidden).
to use it register ComponentCallbacks2 with [registerComponentCallbacks](http://developer.android.com/reference/android/app/Application.html#registerComponentCallbacks(android.content.ComponentCallbacks)) to your application and when level is TRIM_MEMORY_UI_HIDDEN it means that the ui is hidden.

TODO: add a gist for the complete solution
