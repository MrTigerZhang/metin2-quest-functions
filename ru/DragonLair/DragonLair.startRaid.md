# DragonLair.startRaid()
Функция **DragonLair.startRaid** запускает игроков в комнату голубого дракона.

## Параметры функции
### map_index
Тип *number*. **Обязательный параметр**. Индекс локации, куда будут телепортированы игроки.

## Примечания
Функция **не** может быть вызвана анонимно.

Эта функция создает инстанс (подземелье) в указанной локации. В него будут телепортированы все участники гильдии, которые находятся на той же локации, что и игрок, вызвавший функцию. Телепортация будет совершена на серверные координаты (8440, 10669), а после телепортации будет запущен один раз regen-файл (независимо от настроек внутри файла, монстры появятся только один раз) `instance_regen.txt`, который находится в папке с картой в папке maps.

Из-за того, что создается подземелье, внутри него можно использовать функции из семейства [d](../d).

При убийстве монстра с ID `2493` (Голубой Дракон) игроков телепортирует в первые города.