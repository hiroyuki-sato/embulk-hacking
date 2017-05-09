

* private final Injector injector;
* private final ILoggerFactory loggerFactory;
* private final ModelManager modelManager;
* private final PluginManager pluginManager;
* private final BufferAllocator bufferAllocator;
* private final Timestamp transactionTime;
* private final TempFileSpace tempFileSpace;
* private final boolean preview;



## ネストしたインターフェースとクラス

* public interface SessionTask (@Deprecated)
* public static class Builder

### コンストラクタ

コンストラクタはprivate宣言されており、`ExecSession.Builder`経由でのみ呼び出される。

* public ExecSession(Injector injector, ConfigSource configSource) (@Deprecated)

次の二つは`private`宣言されており、ExecSession.Builderクラスからのみ呼び出される。
* private ExecSession(Injector injector, Timestamp transactionTime, Optional<ILoggerFactory> loggerFactory)
* private ExecSession(ExecSession copy, boolean preview)

一般的に次のように利用される。


embulk-core/src/main/java/org/embulk/EmbulkEmbed.java

```java
return ExecSession.builder(injector).fromExecConfig(execConfig).build();
```

embulk-core/src/main/java/org/embulk/exec/BulkLoader.java
```java
ExecSession exec = ExecSession.builder(injector).fromExecConfig(resume.getExecSessionConfigSource()).build();
```

embulk-core/src/test/java/org/embulk/EmbulkTestRuntime.java

```java
this.exec = ExecSession.builder(injector).fromExecConfig(execConfig).build();
```




## メソッド

* public ExecSession forPreview()
* public ConfigSource getSessionExecConfig()
* public Injector getInjector()
* public Timestamp getTransactionTime()
* public Logger getLogger(String name)
* public Logger getLogger(Class<?> name)
* public BufferAllocator getBufferAllocator()
* public ModelManager getModelManager()
* public <T> T newPlugin(Class<T> iface, PluginType type)
* public TaskReport newTaskReport()
* public ConfigDiff newConfigDiff()
* public ConfigSource newConfigSource()
* public TaskSource newTaskSource()
* public TimestampFormatter newTimestampFormatter(String format, DateTimeZone timezone)
* public TempFileSpace getTempFileSpace()
* public boolean isPreview()
* public void cleanup()


### Deprecated

* public CommitReport newCommitReport() (@Deprecated)
