# pc.set_level()
Функция **pc.set_level** меняет уровень игрока, вызвавшего функцию.

## Параметры функции
### level
Тип *number*. **Обязательный параметр**. Уровень, который будет установлен персонажу.

## Примечания
Функция **не** может быть вызвана анонимно.

Статы и навыки при изменении уровня не обнуляются, даже если указать уровень меньший, чем текущий уровень игрока.