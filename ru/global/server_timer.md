# server_timer()
Функция **server_timer** создает серверный таймер.

## Параметры функции
### timer_name
Тип *string*. **Обязательный параметр**. Имя таймера. Должно начинаться с латинской буквы. Может содержать только латиницу, нижние прочерки и числа.

### time
Тип *number*. **Обязательный параметр**. Количество секунд, по прошествии которых сработает таймер.

### argument
Тип *number*. Аргумент, который будет передан в таймер. Этот аргумент можно будет получить из триггера [server_timer](../_triggers/server_timer.md) с помощью функции [get_server_timer_arg](../global/get_server_timer_arg.md)(). По умолчанию аргумент равен `0`.

## Примечания
Функция может быть вызвана анонимно.

Подробности о работе серверного таймера читайте в статье о триггере [server_timer](../_triggers/server_timer.md).

Обратите внимание на то, что таймер не может вызвать сам себя. Т.е. эта конструкция вызовет ошибку:

````lua
when login begin
	server_timer("example", 3)
end

when example.server_timer begin
	server_timer("example", 3)
end
````