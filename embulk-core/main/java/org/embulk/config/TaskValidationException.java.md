## TaskValidationException クラス

* 種類: クラス
* 継承: [ConfigException](ConfigException.java.md)

## インスタンス

* private final Set violations;
    * @SuppressWarnings("unchecked")


## メソッド

### コンストラクタ

* public <T> TaskValidationException(Set<ConstraintViolation<T>> violations)

### メソッド

* public Set<ConstraintViolation<?>> getViolations()
    * @SuppressWarnings("unchecked")
* private static <T> String formatMessage(Set<ConstraintViolation<T>> violations)



## memo

* import java.util.Set;
* import javax.validation.ConstraintViolation;
