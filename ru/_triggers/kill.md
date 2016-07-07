# kill
Триггер **kill** срабатывает, когда игрок убивает игрока или монстра.

## Параметры
### mob_vnum
Тип *number*. Vnum монстра.

## Примечания
Использовать конструкцию `when 123.kill begin` крайне не рекомендуется, поскольку если у вас в друх разных квестах есть `when 123.kill begin`, то работать этот триггер будет только в одном из них. Чтобы избежать этого, следует заменить конструкцию на `when kill with npc.get_race() == 123 begin`.

При использовании данного триггера монстр автоматически &laquo;выделяется&raquo;, что позволяет использовать на нем функции из семейства npc.

Если необходимо определить, кого убил игрок (игрока или монстра), то следует использовать функцию [npc.is_pc](../npc/npc.is_pc.md)().

Чтобы выполнять функции от имени убитого игрока, следует использовать функцию [pc.select](../pc/pc.select.md)() вместе с [npc.get_vid](../npc/npc.get_vid.md)().

Не сработает, если монстр после смерти был перерожден. Например, не сработает на первой форме &laquo;Гнусных демонов&raquo; в Башне Демонов &mdash; только на второй.