## ConfigDiff インターフェース

* 種類: interface
* 継承: [DataSource](DataSource.java.md)

## メソッド

### オリジナル

なし

### Override

* ConfigDiff getNested(String attrName);
* ConfigDiff getNestedOrSetEmpty(String attrName);
* ConfigDiff getNestedOrGetEmpty(String attrName);
* ConfigDiff set(String attrName, Object v);
* ConfigDiff setNested(String attrName, DataSource v);
* ConfigDiff setAll(DataSource other);
* ConfigDiff remove(String attrName);
* ConfigDiff deepCopy();
* ConfigDiff merge(DataSource other);
