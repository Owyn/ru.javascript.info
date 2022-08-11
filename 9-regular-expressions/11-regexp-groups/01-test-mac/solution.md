Двузначное шестнадцатеричное число - это `pattern:[0-9a-f]{2}` (предполагается, что флаг `pattern:i` стоит).

Нам нужно число `NN`, после которого `:NN` повторяется ещё 5 раз.

Регулярное выражение: `pattern:[0-9a-f]{2}(:[0-9a-f]{2}){5}`

Теперь давайте покажем, что шаблон должен захватить весь текст (всю строку): от начала и до конца. Для этого обернём шаблон в `pattern:^...$`.

Итог:

```js run
let regexp = /^[0-9a-f]{2}(:[0-9a-f]{2}){5}$/i;

alert( regexp.test('01:32:54:67:89:AB') ); // true

alert( regexp.test('0132546789AB') ); // false (нет двоеточий)

alert( regexp.test('01:32:54:67:89') ); // false (5 чисел, должно быть 6)

alert( regexp.test('01:32:54:67:89:ZZ') ) // false (ZZ в конце строки)
```