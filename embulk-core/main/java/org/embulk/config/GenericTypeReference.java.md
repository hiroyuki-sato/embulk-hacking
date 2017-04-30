## GenericTypeReference クラス

* 種類: interface
* 継承: [com.fasterxml.jackson.core.type.TypeReference<Object>](http://fasterxml.github.io/jackson-core/javadoc/2.0.0/com/fasterxml/jackson/core/type/TypeReference.html)

## 概要

[embulk-core/src/main/java/org/embulk/config/TaskSerDe.java](TaskSerDe.java.md) で利用される。

## インスタンス

* private final Type type;
    * java.lang.reflect.Type

## メソッド

### コンストラクラタ

* public GenericTypeReference(Type type)

### インスタンスメソッド

* public Type getType()
