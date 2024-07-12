
# kana-transcription

Мини-библиотека, с помощью который вы сможете:
- Привести хирагану/катакану к русскому или английскому алфавиту
- Преобразовать слоги русского или английского алфавита к хирагане/катакане
- Перевести одну кану в другую

Для выполнения каждого пункта есть своя функция. Перед использованием посмотрите ниже некоторые ограничения и рекомендации к  применению, описанные для каждой функции.

Скажу сразу: иногда вывод будет не тем, что вы могли ожидать. Для повышения точности учитывайте рекомендации.

_Проблемы, которые стали причиной появления рекомендаций и ограничений, описаны в [отельном документе](docs/explanation.md)._

## Функции

Общая рекомендация для всех функций: если вы обрабатываете сразу нескольких слов, разделяйте их пробелом (в т. ч. частицы). Это позволит отследить положение слога в слове, от чего нередко зависит его произношение.

<details>

  <summary><h3>`transformToKana(text, fromLang, toKana)`</h3></summary>

  #### Что делает
  
  Приводит текст, написанный русскими или английскими слогами, к одной из японских азбук.
  
  #### Параметры
  
  - text - строка к преобразованию
  - fromLang - _необязательный_ - язык, с которого преобразовывать
    - en (по умолчанию)
    - ru
  - toKana - _необязательный_ - азбука, к которой привести
    - hiragana (по умолчанию)
    - katakana

  #### Рекомендации
  
  - Если после слоговой _н_ (_n_) в слове идёт гласная, сопровождайте _н_: 
    -  _(на русском)_ - _ъ_ - твёрдым знаком 
    -  _(на английском)_ - _'_ - апострофом
  
  - _(на русском)_ Если вы столкнулись с неслышной гласной, и согласная этого слога мягкая, используйте мягкий знак _ь_

  #### Ограничения
  
  При получении результата имейте в виду:
  
  - Долгота гласных отображается только их повторением
  - Неслышная い 
  	- _(с русского)_ выводится при употреблении мягкого знака или всегда мягких согласных
  	- _(с английского)_ не выводится
  - **Не используется** _символ ー_
  - Две одинаковые согласные подряд в одном слове **всегда** понимаются как двойной согласный
</details>

<details>

<summary><h3>`transcriptKana(text, toLang)`</h3></summary>

#### Что делает
Преобразует кану к русским (по системе Поливанова) или английским (по пересмотренной системе Хепбёрна) слогам.

_Обращаю внимание, что указанные системы не используются в полной мере. Например, длинные гласные обозначаются только их повторением._

#### Параметры

- text - кана к преобразованию
- toLang - _необязательный_ - язык, к которому привести
  - en (по умолчанию)
  - ru

#### Ограничения

- Пары гласных えい, おう переводятся побуквенно. Выходит [эи] и [оу] соответственно
</details>

<details>

<summary><h3>`reverseKana(text, toKana)`</h3></summary>

#### Что делает

Оборачивает одну кану в другую

#### Параметры

- text - кана для оборота
- toKana - _необязательный_ - кана, к которой привести
  - hiragana (по умолчанию)
  - katakana

#### Ограничения

- При приведении к катакане ***не используется знак ー***
</details>
