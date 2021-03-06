# d.spawn_mob()
Функция **d.spawn_mob** призывает монстра или NPC в подземелье.

## Параметры функции
### mob_vnum
Тип *number*. **Обязательный параметр**. ID монстра.

### x
Тип *number*. **Обязательный параметр**. Локальная координата по оси X без двух нулей на конце, куда будет призван монстр.

### y
Тип *number*. **Обязательный параметр**. Локальная координата по оси Y без двух нулей на конце, куда будет призван монстр.

### radius
Тип *number*. Допустимая погрешность в координатах при появлении монстра. Если параметр равен, допустим, 15, то координаты появления монстра будут равны ([x](#x) &plusmn; 15, [y](#y) &plusmn; 15); тоже самое в виде квеста: 

````lua
local mob_vnum = 101
local x = pc.get_local_x()
local y = pc.get_local_y()
local radius = 15
local count = 3
d.spawn_mob(
	mob_vnum,
	x + number(radius * -1, radius),
	y + number(radius * -1, radius),
	0,
	count
)
````

Параметр по умолчанию равен `0`.

### count
Тип *number*. Количество призываемых монстров. Параметр по умолчанию равен `1`.

## Возвращаемые значения
### mob_vid
Тип *number*. VID призванного монстра.

## Примечания
Функция может быть вызвана анонимно.

Эта функция работает только в подземельях.