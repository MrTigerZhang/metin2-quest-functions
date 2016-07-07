# add_ox_quiz()
Функция **add_ox_quiz** добавляет вопрос в OX-эвент.

## Параметры функции
### question_group
Тип *number*. **Обязательный параметр**. Группа, к которой будет добавлен вопрос. Этот параметр нужен для работы функции [oxevent.quiz](../oxevent/oxevent.quiz.md)(), которая вызывает случайный вопрос из случайной группы.

### question
Тип *string*. **Обязательный параметр**. Вопрос.

### answer
Тип *boolean*. **Обязательный параметр**. Ответ на этот вопрос. `true` &mdash; это &laquo;да&raquo; или &laquo;O&raquo;; `false` &mdash; это &laquo;нет&raquo; или &laquo;X&raquo;.

## Примечания
Функция может быть вызвана анонимно.

Использовать эту функцию во время запущенного сервера нецелесообразно, поскольку после перезапуска сервера сервер забудет все добавленные в него вопросы. Единственный правильный выход &mdash; это добавлять вопросы с файл oxquiz.lua, который должен находиться в той же папке, где лежат папки quest и map и файлы дропа. Этот файл автоматически подгружается сервером в момент вызова функции [oxevent.open](../oxevent/oxevent.open.md)(), поэтому единственным правильным выходом будет хранить вопросы именно там. Синтаксис файла предельно прост: по одному вопросу на строку и пустая строка в конце файла:

````lua
add_ox_quiz(1, "Правда ли, что Владыка Пламени не имеет сосков? ", true)
````

Чтобы эвент был интереснее, я рекомендую записывать один и тот же вопрос с двумя разными вариантами ответов: &laquo;да&raquo; и &laquo;нет&raquo;. При этом оба вопроса должны быть соответственно изменены.