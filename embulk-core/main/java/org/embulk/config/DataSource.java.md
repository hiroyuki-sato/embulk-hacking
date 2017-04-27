## DataSource インターフェース

* 種類: interface
* 継承: なし
* 本インターフェースを継承しているインターフェース
  * [ConfigSource](ConfigSource.java.md)
  * [ConfigDiff](ConfigDiff.java.md)

## メソッド

* List<String> getAttributeNames();
* Iterable<Map.Entry<String, JsonNode>> getAttributes();
* boolean isEmpty();
* boolean has(String attrName);
* <E> E get(Class<E> type, String attrName);
* <E> E get(Class<E> type, String attrName, E defaultValue);
* DataSource getNested(String attrName);
* DataSource getNestedOrSetEmpty(String attrName);
* DataSource getNestedOrGetEmpty(String attrName);
* DataSource set(String attrName, Object v);
* DataSource setNested(String attrName, DataSource v);
* DataSource setAll(DataSource other);
* DataSource remove(String attrName);
* DataSource deepCopy();
* DataSource merge(DataSource other);
* ObjectNode getObjectNode();
