# pc.setqf()
Функция **pc.setqf** изменяет флаг, привязанный к квесту, из которого была вызвана функция

## Параметры функции
### flag_name
Тип *string*. **Обязательный параметр**. Имя флага.

### value
Тип *number*. **Обязательный параметр**. Значение, которое будет установлено.

## Примечания
Функция **не** может быть вызвана анонимно.

Квестовый флаг привязывается к названию квеста, в котором он был установлен. Это значит, чтобы получить, например, квестовый флаг, заданный в Башне Демонов, можно использовать такую конструкцию:

````lua
local value = pc.getf("deviltower_zone", "flag_name")
````

Если вы хотите узнать значение флага, находясь в квесте Башни Демонов, это можно сделать так:

````lua
local value = pc.getqf("flag_name")
````