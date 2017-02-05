
### When to use CompositeSubscription/CompositeDispossable unsubscribe or clear ?

- If you add/remove Subscriptions to/from it according to a lifecycle (like onCreate starts all your Observables 
and onDestroy stops them), you can simply use clear. However, if some off-thread task keeps starting your Observables, 
you need unsubscribe and replacement of the entire CompositeSubscription to prevent latecommers to keep runnning.

- If the lifetime of the subscription outlives the activity you should not be tying it to a composite subscription which is. 
If the Observable is mutating (either directly or with various doOnXxx) you can simply call .subscribe() without an argument. 
Otherwise you should tie to the subscription to something which has a lifetime that matches that of the observable. 
For example, if the Observable interacts with global state then a service or even a singleton is more appropriate to hold the subscription.

- once a Subscription is unsubscribed it remains so. It can not be revived. All Subscriptions should behave that way. 
  It’s similar to the concept of an Observable instance, once a terminal state is received no further events can be emitted. 

- according to Rx guideline 6.17: Unsubscription Should Be Idempotent : calling the Dispose method multiple times should be allowed. 
Only the first call the side-effect of cleaning up the subscription should occur.

 
