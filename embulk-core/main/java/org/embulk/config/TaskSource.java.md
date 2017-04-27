## TaskSource インターフェース

* 種類: interface
* 継承: [DataSource](DataSource.java.md)

## メソッド

### オリジナル

* <T> T loadTask(Class<T> taskType);

### Override

* TaskSource getNested(String attrName);
* TaskSource getNestedOrSetEmpty(String attrName);
* TaskSource getNestedOrGetEmpty(String attrName);
* TaskSource set(String attrName, Object v);
* TaskSource setNested(String attrName, DataSource v);
* TaskSource setAll(DataSource other);
* TaskSource remove(String attrName);
* TaskSource deepCopy();
* TaskSource merge(DataSource other);
