# chat
Триггер **chat** запускает событие, когда игрок выбирает определенный пункт в диалоге у определенного NPC.

## Параметры
### mob_vnum
Тип *number*. **Обязательный параметр**. Vnum NPC, с которым необходимо начать диалог.

### message
Тип *string*. **Обязательный параметр**. Пункт, который игроку необходимо выбрать в диалоге с NPC.

## Примечания
Функция [setskin](../global/setskin.md)() с параметром `0` удаляет черные полосы с экрана и заставляет UI снова отображаться. Если после вызова этого триггера не идет функция [say](../global/say.md)(), то черные полосы остаются. В этом случае их надо убирать самостоятельно.