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
