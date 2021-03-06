# Структура квеста
Каждый квест состоит из такой структуры:

````lua
quest example begin
	state start begin
		when kill begin
			syschat("чай ")
		end
	end
end
````

Все квесты состоят из трех квестовых конструкций: декларирующая конструкция (первая строчка), стадийная конструкция (вторая строчка) и событийная конструкция (третья строчка). Данные три конструкции являются уникальными и ничего подобного в оригинальном Lua нет. Квестовые конструкции всегда открываются не через `then`, а через ключевое слово `begin`, и закрываются ключевым словом `end`.

## Декларирующая конструкция
В декларирующей конструкции только дается имя квесту. В примере выше `example` &mdash; это название квеста. Названия квестов не могут повторяться, а правила именования такие же, как у переменных. Рекомендуется (но не обязательно) называть файлы с квестами так же, как и назван квест. То есть этот квест стоит сохранить под именем `example.quest`. С декларацией квеста нет ничего сложного. Просто заключаете между `quest` и `begin` название квеста и всё.

> **Важно!** В квестах какой-либо код не может идти вне квестового события. Это значит, что вы не можете, например, разместить перед декларирующей конструкцией какие-либо переменные или функции.

## Событийная конструкция
Событийная конструкция всегда начинается с ключевого слова `when`, которое переводится как &laquo;когда&raquo;. Прочитать это можно так: когда игрок входит в игру, тогда отправляем в чат слово &laquo;чай&raquo;. В событийной конструкции указывается триггер. В данном примере [login](../_triggers/login.md) &mdash; это триггер, который означает &laquo;вход в игру&raquo;. Можно также указать несколько триггеров:

````lua
quest example begin
	state start begin
		when login or kill begin
			syschat("чай ")
		end
	end
end
````

Теперь слово &laquo;чай&raquo; будет показываться игрокам при входе в игру и при убийстве монстров (триггер [kill](../_triggers/kill.md) срабатывает при убийстве). Также в событийной конструкции можно задавать условия, при которых они будут выполняться, используя ключевое слово `with`:

````lua
quest example begin
	state start begin
		when login with 50 > 10 begin
			syschat("чай ")
		end
	end
end
````

Если условие справа от `with` равно `true`, то тогда сработает триггер. Можно еще задать условие с несколькими триггерами:

````lua
quest example begin
	state start begin
		when login or kill with 50 > 10 begin
			syschat("чай ")
		end
	end
end
````

Но в таком случае нельзя задать условие для каждого триггера индивидуально. Но можно сделать так:

````lua
quest example begin
	state start begin
		when login with 50 > 10 begin
			syschat("чай ")
		end

		when kill with 123 > 5 begin
			syschat("сок ")
		end
	end
end
````

В данном примере мы задали индивидуальные условия для каждого триггера.

## Стадийная конструкция
Стадийная конструкция отвечает за стадии квеста. Допустим, у вас есть квест на выполнение. Этот квест можно разделить на 3 этапа:

* стадия, когда игрок еще не взял этот квест, но может его взять
* стадия, когда игрок уже взял квест и должен начать его выполнять
* стадия, когда игрок уже выполнил квест и должен вернуться к NPC за наградой

В данном примере описан простейший квест подобного типа. Игроку предстоит по достижении 10 уровня подойти к Торговке мелочными товарами, поговорить с ней, а затем пойти убить одного пса в первом городе. Когда игрок убьет его, то квест будет считаться выполненым и игрок сможет вернуться к NPC за наградой. Квест:

````lua
quest example begin
	state start begin

		--[[
			Некоторые триггеры могут принимать параметры.
			Триггер chat принимает два параметра:
			1. Vnum NPC, с которым игрок должен начать диалог. В нашем случае это 9003
			2. Сообщение, при выборе которого сработает триггер. В нашем случае это "Есть задание? "
		]]

		when 9003.chat."Есть задание? " with pc.get_level() >= 10 begin
			say("Привет. ")
			say("У меня для тебя есть задание. ")
			say("Тебе необходимо убить одного пса. ")
			say("Когда убьешь - приходи ко мне. ")

			--[[
				Функция set_state() меняет стадию квеста.
			]]

			set_state("go_hunt")
		end
	end

	state go_hunt begin

		--[[
			Функция npc.get_race() возвращает vnum убитого монстра.
			Мы проверяем, является ли этот vnum равным vnum собаки (101).
			Проверка необходима для того, чтобы триггер не сработал, например, при убийстве какого-нибудь медведя.
		]]

		when kill with npc.get_race() == 101 begin
			set_state("reward")
		end
	end

	state reward begin
		when 9003.chat."Получить награду " begin	
			say("Отличная работа. ")
			say("Держи Меч+8. ")

			--[[
				Функция pc.give_item2() дает игроку предмет с определенным vnum.
				Мы даем игроку Меч+8 (vnum 18).
				Если не указывать второй параметр (количество), то предмет будет дан в одном экземпляре.
			]]

			pc.give_item2(18)

			set_state("complete")
		end
	end

	--[[
		Мы переводим квест в пустую стадию complete.
		Необходимо это для того, чтобы ни один триггер из квеста выше не сработал.
		Если вы, например, хотите сделать квест повторяющимся, то просто переведите его после выполнения в стадию start.
	]]

	state complete begin
	end
end
````

Стадии задаются через ключевое слово `state`, а затем указывается название стадии. Имена у стадий могут быть любыми в рамках правил наименования переменных, но квест должен начинаться со стадии `start` &mdash; она всегда выполняется первой. Основные принципы работы приведенного выше квеста описаны в комментариях в коде. Самый простой способ понять, как всё это работает &mdash; установить квест на собственный сервер и поэкспериментировать с кодом.

Важно понимать, что находясь в какой-либо стадии, игрок не может вызывать триггеры из других стадий. Таким образом, находясь в стадии `start`, игрок не сможет поговорить с NPC и получить награду, которая выдается в стадии `reward`.
