## TaskValidatorクラス

* 親クラス: Object

## インスタンス変数

* private final Validator validator;

## メソッド

### コンストラクタ

* public TaskValidator(Validator validator)

### メソッド

* public <T> void validateModel(T model) throws TaskValidationException


## メモ

* [JavaEE使い方メモ（Bean Validation）](http://qiita.com/opengl-8080/items/3926fbde5469c0b330c2)


###

メインとなるのは次の部分

```java
public <T> void validateModel(T model) throws TaskValidationException
{
    Set<ConstraintViolation<T>> violations = validator.validate(model);
    if (!violations.isEmpty()) {
        throw new TaskValidationException(violations);
    }
}
```
