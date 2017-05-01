## top

* EmbulkEmbed.java
* EmbulkService.java
* EmbulkVersion.java

## command

* PreviewPrinter.java
* TablePreviewPrinter.java
* VerticalPreviewPrinter.java

## config

### DataSourceを継承するインターフェース群とその実装クラス

- [x] [DataSource.java](main/java/org/embulk/config/DataSource.java.md)
    - [x] [ConfigDiff.java](main/java/org/embulk/config/ConfigDiff.java.md)
    - [x] [ConfigSource.java](main/java/org/embulk/config/ConfigSource.java.md)
    - [x] [TaskReport.java](main/java/org/embulk/config/TaskReport.java.md)
        - [x] [CommitReport.java](main/java/org/embulk/config/CommitReport.java.md) (@Deprecated)
    - [x] [TaskSource.java](main/java/org/embulk/config/TaskSource.java.md)

上記インターフェースを全て実装したクラス

- [ ] [DataSourceImpl.java](main/java/org/embulk/config/DataSourceImpl.java.md)

### アノテーション

- [x] [Config.java](main/java/org/embulk/config/Config.java.md)
- [x] [ConfigDefault.java](main/java/org/embulk/config/ConfigDefault.java.md)
- [x] [ConfigInject.java](main/java/org/embulk/config/ConfigInject.java.md)

### シリアライザ・デシリアライザ

- [ ] TaskSerDe.java
- [ ] DataSourceSerDe.java

### Config

- [ ] ConfigLoader.java


### Tasks

- [x] [Task.java](main/java/org/embulk/config/Task.java.md)
- [ ] TaskInvocationHandler.java
- [x] [TaskValidator.java](main/java/org/embulk/config/TaskValidator.java.md)

### Exception

- [x] [ConfigException.java](main/java/org/embulk/config/ConfigException.java.md) (implment [UserDataException.java](main/java/org/embulk/config/UserDataException.java.md))
    - [x] [TaskValidationException.java](main/java/org/embulk/config/UserDataException.java.md)
- [x] [UserDataException.java](main/java/org/embulk/config/UserDataException.java.md)
- [ ] UserDataExceptions.java

### Others

- [x] [GenericTypeReference.java](main/java/org/embulk/config/GenericTypeReference.java.md)
- [ ] [ModelManager.java](main/java/org/embulk/config/ModelManager.java.md)
    * コンストラクタインジェクション?が使われている(@Inject)
* YamlTagResolver.java

## exec

### Executor

* BulkLoader.java
* PreviewExecutor.java
* GuessExecutor.java

### Plugin

* BufferFileInputPlugin.java
* ConfigurableGuessInputPlugin.java
* LocalExecutorPlugin.java
* SamplingParserPlugin.java

### Exception

* ExecutionInterruptedException.java
* PartialExecutionException.java
* NoSampleException.java
* SkipTransactionException.java

### Module

* ExecModule.java
* ExtensionServiceLoaderModule.java
* SystemConfigModule.java

### Allocator

* PooledBufferAllocator.java
* TempFileAllocator.java

### Result

* ExecutionResult.java
* PreviewResult.java

### Others

* ForGuess.java
* ForSystemConfig.java
* LoggerProvider.java
* PreviewedNoticeError.java
* ResumeState.java
* SetCurrentThreadName.java
* TransactionStage.java

## jruby

* JRubyPluginSource.java
* JRubyScriptingModule.java

## plugin

* BuiltinPluginSourceModule.java
* InjectedPluginSource.java
* PluginClassLoader.java
* PluginClassLoaderFactory.java
* PluginClassLoaderModule.java
* PluginManager.java
* PluginSource.java
* PluginSourceNotMatchException.java
* PluginType.java

### compat

* InputPluginWrapper.java
* PluginWrappers.java
* TransactionalFileInputWrapper.java
* TransactionalFileOutputWrapper.java
* TransactionalPageOutputWrapper.java

## spi

### Column

* Column.java
* ColumnConfig.java
* ColumnVisitor.java

### Buffer

* Buffer.java
* BufferAllocator.java


### Plugins

* DecoderPlugin.java
* EncoderPlugin.java
* ExecutorPlugin.java
* FileInputPlugin.java
* FileOutputPlugin.java
* FilterPlugin.java
* FormatterPlugin.java
* GuessPlugin.java
* InputPlugin.java
* OutputPlugin.java
* ParserPlugin.java

### Page

* Page.java
* PageBuilder.java
* PageFormat.java
* PageOutput.java
* PageReader.java

### exec

* Exec.java
* ExecAction.java
* ExecSession.java

### schema

* Schema.java
* SchemaConfig.java
* SchemaConfigException.java

## transactional

* Transactional.java
* TransactionalFileInput.java
* TransactionalFileOutput.java
* TransactionalPageOutput.java


### temp

* TempFileException.java
* TempFileSpace.java

### File

* FileInput.java
* FileInputRunner.java
* FileOutput.java
* FileOutputRunner.java

### State

* ProcessState.java
* TaskState.java

### Others

* AbortTransactionResource.java
* CloseResource.java
* DataException.java
* Extension.java
* ProcessTask.java

## sub

* json
* time
* type
* unit
* util
