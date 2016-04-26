

### Use takeUntil to watch terminal situations

Example: Stop fetching sensible data when the user logs out
```java 
@Retention(RetentionPolicy.RUNTIME) @Qualifier public @interface SignOut{}

@SignOut @Provides @Singleton
Observable<Void> provideSignOutObservable(@SignOut PublishSubject<Void> subject) {
  return subject;
}

@SignOut @Provides @Singleton
PublishSubject<Void> provideSignOutSubject() {
   return PublishSubject.create();
}

public DrawerView ... {
  void onSignoutClick() {
    //do some signout logic    
    this.signOut.onNext(null); //inform the rest of the app that use has signed out in a decoupled way 
  }
 }
 
@Retention(RetentionPolicy.RUNTIME) @Qualifier public @interface SignOut{}

@SignOut @Provides @Singleton
Observable<Void> provideSignOutObservable(@SignOut PublishSubject<Void> subject) {
  return subject;
}

@SignOut @Provides @Singleton
PublishSubject<Void> provideSignOutSubject() {
   return PublishSubject.create();
}

public DrawerView ... {
  void onSignoutClick() {
    //do some signout logic    
    this.signOut.onNext(null); //inform the rest of the app that use has signed out in a decoupled way 
  }
 }


```

