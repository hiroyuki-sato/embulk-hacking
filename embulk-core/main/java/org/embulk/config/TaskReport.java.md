## TaskReport インターフェース

* 種類: interface
* 継承: [DataSource](DataSource.java.md)

## メソッド

### オリジナル

なし

### Override

* TaskReport getNested(String attrName);
* TaskReport getNestedOrSetEmpty(String attrName);
* TaskReport getNestedOrGetEmpty(String attrName);
* TaskReport set(String attrName, Object v);
* TaskReport setNested(String attrName, DataSource v);
* TaskReport setAll(DataSource other);
* TaskReport remove(String attrName);
* TaskReport deepCopy();
* TaskReport merge(DataSource other);
