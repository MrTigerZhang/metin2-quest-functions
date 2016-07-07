# notice_in_map()
Функция **notice_in_map** отправляет сообщение, которое увидят все игроки в локации, где была вызвана функция.

## Параметры функции
### message
Тип *string*. **Обязательный параметр**. Сообщение, которое увидят все игрок на локации.

### big_font
Тип *boolean*. Будет ли сообщение продублировано в окне с большим шрифтом вверху экрана (как на ОХ-эвенте или через чат-команду `/b {message}`). Возможны неточности. По умолчанию параметр равен `false`.

## Примечания
Функция **не** может быть вызвана анонимно.

Вопреки заблуждению многих, указать, в какой именно локации показать уведомление, нельзя.

Цвет уведомления такой же, как у функции [notice_all](../global/notice_all.md)() &mdash; бежевый.