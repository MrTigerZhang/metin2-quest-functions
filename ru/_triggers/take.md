# take
Триггер **take** срабатывает, когда игрок переносит предмет на NPC.

## Параметры
### npc_vnum
Тип *number*. Vnum NPC, на которого игрок должен перенести предмет.

## Примечания
При переносе предмета на NPC предмет и NPC автоматически выделяются, что позволяет использовать на них функции из семейств [item](../item) и [npc](../npc) соответственно.

Очень желательно делать проверку через функцию [item.get_id](../item/item.get_id.md)(), она возвращает уникальный ID предмета, а если предмет не существует, то возвращает 0. Без этой проверки вероятнее всего триггер можно обмануть, перенеся на NPC искусственно-воссозданный предмет с помощью изменений в коде клиента.