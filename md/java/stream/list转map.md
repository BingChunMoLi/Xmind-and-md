常规方式(字段不可为空，否则NPE)
```java
    Map<String, String> map = list.stream().collect(Collectors.toMap(Obj::getField, Obj::getField));
```
调用源码位置
```java
default V merge(K key, V value, BiFunction<? super V, ? super V, ? extends V> remappingFunction) {
    Objects.requireNonNull(remappingFunction);
    // 在这里判断了value不可为null
    Objects.requireNonNull(value);
    V oldValue = get(key);
    V newValue = (oldValue == null) ? value : remappingFunction.apply(oldValue, value);
    ...
```

可为null
```java
list.stream().collect(Collectors.toMap(Obj::getField, v -> v.getField() == null ? "" : v.getField()));
list.stream().collect(HashMap::new,(k, v) -> k.put(v.getField(), v.getField()), HashMap::putAll);
list.stream().collect(Collectors.toMap(Obj::getField, v -> Optional.ofNullable(obj.getField())));
```

key重复时会抛出 
> java.lang.IllegalStateException: Duplicate key

覆盖
```java
list.stream().collect(HashMap::new,(k, v) -> k.put(v.getField(), v.getField()), HashMap::putAll);

list.stream().collect(Collectors.toMap(Obj::getField, Obj::getField, (k1, k2) -> k2));
```
拼接
```java
list.stream().collect(Collectors.toMap(Obj::getField, Obj::getField, (k1, k2) -> k1 + "," + k2));
```
集合
```java
list.stream().collect(Collectors.toMap(Obj::getField,
    v -> {
        List<String> t = new ArrayList<>();
        t.add(v.getField());
        return t;
    },
    (List<String> v1, List<String> v2) -> {
        v1.addAll(v2);
        return v1;
    }));
```