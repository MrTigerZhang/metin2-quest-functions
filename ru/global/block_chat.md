# block_chat()
Функция **block_chat** блокирует чат определенному игроку на определенное время.

## Параметры функции
### player_name
Тип *string*. **Обязательный параметр**. Имя игрока, чей чат будет заблокирован.

### duration
Тип *string*. **Обязательный параметр**. Длительность. Указывается длительность так: `45s` &mdash; если надо заблокировать на 45 секунд; `45m` &mdash; 45 минут; `45h` &mdash; 45 часов; `45d` &mdash; 45 дней.

## Возвращаемые значения
### status
Тип *boolean*. Статус выполнения функции. `false`, если один из параметров не является строкой или если функция была вызвана от имени сервера и `true`, если функция была выполнена успешно.

## Примечания
Функция **не** может быть вызвана анонимно.