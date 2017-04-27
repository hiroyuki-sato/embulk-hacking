## CommitReport インターフェース  (@Deprecated)

* 種類: interface
* 継承: [TaskReport](TaskReport.java.md)

## メソッド

### オリジナル

なし

### Override

* CommitReport getNested(String attrName);
* CommitReport getNestedOrSetEmpty(String attrName);
* CommitReport getNestedOrGetEmpty(String attrName);
* CommitReport set(String attrName, Object v);
* CommitReport setNested(String attrName, DataSource v);
* CommitReport setAll(DataSource other);
* CommitReport remove(String attrName);
* CommitReport deepCopy();
* CommitReport merge(DataSource other);
