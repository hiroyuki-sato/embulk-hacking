## ConfigSource インターフェース

* 種類: interface
* 継承: [DataSource](DataSource.java)

## メソッド

### オリジナル

* <T> T loadConfig(Class<T> taskType);

### Override

* ConfigSource getNested(String attrName);
* ConfigSource getNestedOrSetEmpty(String attrName);
* ConfigSource getNestedOrGetEmpty(String attrName);
* ConfigSource set(String attrName, Object v);
* ConfigSource setNested(String attrName, DataSource v);
* ConfigSource setAll(DataSource other);
* ConfigSource remove(String attrName);
* ConfigSource deepCopy();
* ConfigSource merge(DataSource other);
