

- Use a syncronized accessor when using lazy initialization.

```java 
// Lazy initialization of instance field - synchronized accessor
private FieldType field;
synchronized FieldType getField() {
    if (field == null)
        field = computeFieldValue();
    return field;
}
```

- If you need to use lazy initialization for performance on a static field, use
  the lazy initialization holder class idiom. 
```java 
// Lazy initialization holder class idiom for static fields
private static class FieldHolder {
    static final FieldType field = computeFieldValue();
}
static FieldType getField() { return FieldHolder.field; }
```

- If you need to use lazy initialization for performance on an instance field, use the double-check idiom. 
```java 
// Double-check idiom for lazy initialization of instance fields
private volatile FieldType field;

FieldType getField() {
    FieldType result = field;
    if (result == null) { // First check (no locking)
    synchronized(this) {
        result = field;
        if (result == null) // Second check (with locking)
            field = result = computeFieldValue();
        }
    }
    return result;
}
```

local variable result ensures that field is read only once in the common case where it’s already initialized. While not
strictly necessary it improves performance.

- singlecheck idiom in case where the lazily initialized instance field can tolerate repeated initialization.
```java 
// Single-check idiom - can cause repeated initialization!
private volatile FieldType field;
private FieldType getField() {
    FieldType result = field;
    if (result == null)
        field = result = computeFieldValue();
    return result;
}
```
