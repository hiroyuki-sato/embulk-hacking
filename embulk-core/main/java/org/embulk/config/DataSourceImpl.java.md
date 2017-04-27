## DataSourceImplクラス

* 実装インターフェース
  * [ConfigSource](ConfigSource.java.md)
  * [ConfigDiff](ConfigDiff.java.md)
  * [TaskReport](TaskReport.java.md)
      * [CommitReport](CommitReport.java.md)  (@Deprecated)
  * [TaskSource](TaskSource.java.md)


## インスタンス

* protected final ObjectNode data;
* protected final ModelManager model;

## コンストラクタ

* public DataSourceImpl(ModelManager model)
* public DataSourceImpl(ModelManager model, ObjectNode data)
* protected DataSourceImpl newInstance(ModelManager model, ObjectNode data)

## メソッド

### クラスメソッド

* private static void mergeJsonObject(ObjectNode src, ObjectNode other)
* private static void mergeJsonArray(ArrayNode src, ArrayNode other)

### Override

DataSourceインターフェース

* public List<String> getAttributeNames()
* public Iterable<Map.Entry<String, JsonNode>> getAttributes()
* public boolean isEmpty()
* public boolean has(String attrName)
* public <E> E get(Class<E> type, String attrName)
* public <E> E get(Class<E> type, String attrName, E defaultValue)
* public DataSourceImpl getNested(String attrName)
* public DataSourceImpl getNestedOrSetEmpty(String attrName)
* public DataSourceImpl getNestedOrGetEmpty(String attrName)
* public DataSourceImpl set(String attrName, Object v)
* public DataSourceImpl setNested(String attrName, DataSource v)
* public DataSourceImpl setAll(DataSource other)
* public DataSourceImpl remove(String attrName)
* public DataSourceImpl deepCopy()
* public DataSourceImpl merge(DataSource other)
* public ObjectNode getObjectNode()

TaskSourceインターフェース

* public <T> T loadTask(Class<T> taskType)

ConfigSourceインターフェース

* public <T> T loadConfig(Class<T> taskType)

Objectクラス？

* public String toString()
* public boolean equals(Object other)
* public int hashCode()




}
```
