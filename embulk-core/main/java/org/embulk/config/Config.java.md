## @Config インターフェース

次のようなアノテーションを作成するための定義

```java
public interface MySQLPluginTask
        extends PluginTask
{
    @Config("port")
    @ConfigDefault("3306")
    public int getPort();

    // ....
```

## 実装

```java
@Documented
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface Config
{
    String value();
}
```
