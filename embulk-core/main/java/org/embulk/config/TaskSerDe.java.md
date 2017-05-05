## TaskSeDeクラス

* 種類: クラス
* 継承: Object

## TaskSeDeで定義されているクラス

* TaskSerDe
    * public static class TaskSerializer extends JsonSerializer<Task>
    * public static class TaskDeserializer <T> extends JsonDeserializer<T>
        * private static class FieldEntry
        * private static class InjectEntry  
    * public static class TaskSerializerModule extends SimpleModule
    * public static class ConfigTaskDeserializer <T> extends TaskDeserializer<T>
    * public static class TaskDeserializerModule extends Module
    * public static class ConfigTaskDeserializerModule extends TaskDeserializerModule

### 継承関係

* com.fasterxml.jackson.Module
    * TaskDeserializerModule
        * ConfigTaskDeserializerModule
* com.fasterxml.jackson.databind.JsonDeserializer<T>
    * TaskDeserializer<T>
        * ConfigTaskDeserializer<T>
* com.fasterxml.jackson.databind.JsonSerializer<Task>
    * TaskSerializer
* com.fasterxml.jackson.databind.module.SimpleModule
    * TaskSerializerModule


## Memo


TaskSerDe.TaskSerializerの中の`serialize`というメソッドの中に

`jgen.writeStartObject()`, `jgen.writeEndObject()`というメソッドがある

https://github.com/FasterXML/jackson-databind#5-minute-tutorial-streaming-parser-generator

このURLの中の`{"message":"Hello world!"}`とするところが次のようになっている。

```java
g.writeStartObject();
g.writeStringField("message", "Hello world!");
g.writeEndObject();
```

このメソッドは、`jgen.writeStartObject()`, `jgen.writeEndObject()`は一緒だが、

`writeStringField`の代わりに次のようなものを使っている。

```java
jgen.writeFieldName(pair.getKey());
nestedObjectMapper.writeValue(jgen, pair.getValue());
```

```java
public void serialize(Task value, JsonGenerator jgen, SerializerProvider provider)
        throws IOException
{
    if (value instanceof Proxy) {
        Object handler = Proxy.getInvocationHandler(value);
        if (handler instanceof TaskInvocationHandler) {
            TaskInvocationHandler h = (TaskInvocationHandler) handler;
            Map<String, Object> objects = h.getObjects();
            jgen.writeStartObject();
            for (Map.Entry<String, Object> pair : objects.entrySet()) {
                if (h.getInjectedFields().contains(pair.getKey())) {
                    continue;
                }
                jgen.writeFieldName(pair.getKey());
                nestedObjectMapper.writeValue(jgen, pair.getValue());
            }
            jgen.writeEndObject();
            return;
        }
    }
    // TODO exception class & message
    throw new UnsupportedOperationException("Serializing Task is not supported");
}
```

##

[com.fasterxml.jackson.databind.Module](https://fasterxml.github.io/jackson-databind/javadoc/2.7/com/fasterxml/jackson/databind/Module.html)


このクラスでは、次のメソッドがabstractとして定義されており、サブクラス内で実装が必要
* abstract String getModuleName();
* abstract void setupModule(Moule.SetupContext context)
* abstract Version

TaskSeDe.TaskDeserializerModuleクラスでは次のような実装をしている。

* getModuleName: "embulk.config.TaskSerDe"を返す。
* Version: Version.unknownVersion


```java
@Override
public void setupModule(SetupContext context)
{
    context.addDeserializers(new Deserializers.Base() {
        @Override
        public JsonDeserializer<?> findBeanDeserializer(JavaType type, DeserializationConfig config,
                BeanDescription beanDesc) throws JsonMappingException
        {
            Class<?> raw = type.getRawClass();
            if (Task.class.isAssignableFrom(raw)) {
                return newTaskDeserializer(raw);
            }
            return super.findBeanDeserializer(type, config, beanDesc);
        }
    });
}
```

```java
@SuppressWarnings("unchecked")
protected JsonDeserializer<?> newTaskDeserializer(Class<?> raw)
{
    return new TaskDeserializer(nestedObjectMapper, model, raw);
}
```
