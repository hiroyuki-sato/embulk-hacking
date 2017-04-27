## @Config インターフェース

次のようなアノテーションを作成するための定義

src/main/java/org/embulk/spi/time/TimestampParser.java

```java
public interface Task
{
          //  ....
    @ConfigInject
    public ScriptingContainer getJRuby();
}
```

src/main/java/org/embulk/spi/util/LineEncoder.java

```java
public interface EncoderTask
        extends Task
{
      // ...

    @ConfigInject
    public BufferAllocator getBufferAllocator();
```

## 実装

このように書かれているだけ

```
@Documented
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface ConfigInject
{
}
```


## 使われどころ(TODO)


src/main/java/org/embulk/config/TaskSerDe.java

```
protected Map<String, FieldEntry> getterMappings(Class<?> iface)
{
    ImmutableMap.Builder<String, FieldEntry> builder = ImmutableMap.builder();
    for (Map.Entry<String, Method> getter : TaskInvocationHandler.fieldGetters(iface).entrySet()) {
        Method getterMethod = getter.getValue();
        String fieldName = getter.getKey();

        if (getterMethod.getAnnotation(ConfigInject.class) != null) {
            // InjectEntry
            continue;
        }

        Type fieldType = getterMethod.getGenericReturnType();

        Optional<String> jsonKey = getJsonKey(getterMethod, fieldName);
        if (!jsonKey.isPresent()) {
            // skip this field
            continue;
        }
        Optional<String> defaultJsonString = getDefaultJsonString(getterMethod);
        builder.put(jsonKey.get(), new FieldEntry(fieldName, fieldType, defaultJsonString));
    }
    return builder.build();
}
```
