# chat()
Функция **chat** отправляет уведомление в чат, которое увидит только игрок, вызвавший функцию.

## Параметры функции
### message
Тип *string*. **Обязательный параметр**. Уведомление, которое увидит игрок.

## Примечания
Функция **не** может быть вызвана анонимно.

Цвет текста обычно белый. Он такой же, как цвет сообщения, отправляемый в обычный чат игроком.

Для уведомления пользователя рекомендуется использовать функцию [syschat](../global/syschat.md)() или [notice](../global/notice.md)().