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
