# horse.get_grade()
Функция **horse.get_grade** сообщает тип лошади у игрока.

## Возвращаемые значения
### horse_grade
Тип *number*. Тип лошади. `1` &mdash; обычная лошадь; `2` &mdash; броневая лошадь (можно атаковать с коня); `3` &mdash; армейская лошадь (можно атаковать с коня и использовать навыки). `0`, если у игрока нет коня.

## Примечания
Функция **не** может быть вызвана анонимно.

Эта функция аналогична следующему коду:

````lua
local grade = 0
if horse.get_level() > 0 then
	grade = math.floor(horse.get_level() / 10) + 1
end
````