## ModelManagerクラス

## インスタンス

* private final Injector injector;
* private final ObjectMapper objectMapper;
* private final ObjectMapper configObjectMapper;  // configObjectMapper uses different TaskDeserializer
* private final TaskValidator taskValidator;

## クラスメソッド

* public ModelManager(Injector injector, ObjectMapper objectMapper) (@Inject)

## メソッド

* public <T> T readObject(Class<T> valueType, String json)
* public <T> T readObject(Class<T> valueType, JsonParser parser)
* public <T> T readObjectWithConfigSerDe(Class<T> valueType, String json)
* public <T> T readObjectWithConfigSerDe(Class<T> valueType, JsonParser parser)
* public String writeObject(Object object)
* public void validate(Object object)
* JsonNode writeObjectAsJsonNode(Object v)
* ObjectNode writeObjectAsObjectNode(Object v)
* <T> T getInjectedInstance(Class<T> type)


### Memo

* [Apache BVal](http://bval.apache.org/index.html)
* [Jackson](https://github.com/FasterXML/jackson-databind)
* [Google Guice](https://github.com/google/guice)
* javax.validation.Validation

## クラスメソッド

### ModelManager(Injector injector, ObjectMapper objectMapper)

* injectorに引数で渡されたinjectorを登録
* objectMapperに引数で渡されたobjectMaperを登録
* taskValidatorに、javax.validation.ValidationのbyProbyderメソッドにて、ApacheValidationProviderクラスを初期化して登録する。(JSR303)
* objectMapperとそのコピー(objectMapper.copy())であるconfigObjectMapperに対して次の三つのモジュールを登録(registerModule)する。
    * TaskSerDe.TaskSerializerModule
    * TaskSerDe.TaskDeserializerModule
    * DataSourceSerDe.SerDeModule


## インスタンスメソッド

### public <T> T readObject(Class<T> valueType, String json)

例外処理を抜くとやっているのはこれだけ

```java
return objectMapper.readValue(json, valueType);
```

### public <T> T readObject(Class<T> valueType, JsonParser parser)

例外処理を抜くとやっているのはこれだけ

```java
return objectMapper.readValue(parser, valueType);
```

### public <T> T readObjectWithConfigSerDe(Class<T> valueType, String json)

基本`readObject`と一緒だが次の点が異なる。

* objectMapperの代わりにconfigObjectMapperを利用
* validate()を呼び出す。

```java
t = configObjectMapper.readValue(json, valueType);
validate(t);
```


### public <T> T readObjectWithConfigSerDe(Class<T> valueType, JsonParser parser)

* objectMapperの代わりにconfigObjectMapperを利用
* validate()を呼び出す。

```java
t = configObjectMapper.readValue(parser, valueType);
validate(t);
```


### public String writeObject(Object object)

例外処理を抜くとやっているのはこれだけ

```java
return objectMapper.writeValueAsString(object);
```

### public void validate(Object object)

やっているのはこれだけ

```java
taskValidator.validateModel(object);
```

### JsonNode writeObjectAsJsonNode(Object v)

例外処理を抜くとやっているのはこれだけ

```java
// visible for DataSource.set
String json = writeObject(v);
return objectMapper.readValue(json, JsonNode.class);
```

### ObjectNode writeObjectAsObjectNode(Object v)

```java
// visible for TaskInvocationHandler.invokeDump
String json = writeObject(v);
return objectMapper.readValue(json, ObjectNode.class);
```

### <T> T getInjectedInstance(Class<T> type)


```java
// visible for TaskSerDe.set
// TODO create annotation calss and get its instance at the 2nd argument
return injector.getInstance(type);
```
