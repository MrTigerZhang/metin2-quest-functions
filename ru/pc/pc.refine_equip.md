# pc.refine_equip()
Функция **pc.refine_equip** улучшает определенную надетую часть снаряжения.

## Параметры функции
### cell
Тип *number*. **Обязательный параметр**. ID ячейки окна снаряжения.

### level_limit
Тип *number*. **Обязательный параметр**. Максимальный уровень заточки предмета, который будет подвергаться улучшению. Например, если указать парамерту значение `7`, то можно будет улучшить предметы с заточкой не выше +7.

### success_pct
Тип *number*. Вероятность успешного улучшения предмета в процентах. По умолчанию параметр равен `100`.

## Возвращаемые значения
### status
Тип *boolean*. Результат выполнения функции. При успешном улучшении предмета возвращается `true`. Возвращется `false`, если

* первые два параметра не являются числами
* нет предмета в заданной ячейке
* поле `refined_vnum` в `player.item_proto` у предмета в заданной ячейке равно `0`
* уровень заточки предмета больше, чем параметр [level_limit](#level_limit)
* улучшение предмета не удалось

## Примечания
Функция **не** может быть вызвана анонимно.