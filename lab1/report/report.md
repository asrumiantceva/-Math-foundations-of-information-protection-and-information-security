---
# Front matter
lang: ru-RU
title: 'Отчёт по лабораторной работе 1'
subtitle: 'Шрифты простой замены'
author: 'Румянцева Александра Сергеевна'

# Formatting
toc-title: 'Содержание'
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4paper
documentclass: scrreprt
polyglossia-lang: russian
polyglossia-otherlangs: english
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase
indent: true
pdf-engine: lualatex
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Приобретение практических навыков шифрования и дешифрования текстов методом простой замены. Изучение шифра Цезаря и Атбаша.

# Задание

Лабораторная работа подразумевает реализацию шифра Цезаря с произвольным ключом k и шифра Атбаш.

# Теория

## Шифр Цезаря

Шифр Цезаря, также известный, как шифр сдвига, код Цезаря или сдвиг Цезаря — один из самых простых и наиболее широко известных методов шифрования. Он является моноалфавитным, то есть имеет подстановочный тип, где каждая буква в открытом тексте заменяется на другую букву, смещенную на определенное количество позиций в алфавите.

Шифр Цезаря называется так благодаря Юлию Цезарю, который использовал его со сдвигом 3, чтобы защищать военные сообщения. Несмотря на то, что Цезарь считается первым зафиксированным человеком, использующим эту схему, другие шифры подстановки, как известно, использовались и раньше.

Например, в шифре со сдвигом вправо на 3, А была бы заменена на Г, Б станет Д, и так далее.

Пример шифрования со сдвигом 5:

|Сообщение	|К	|Р	|И	|П	|Т	|О	|Г	|Р	|А	|Ф	|И	|Я	|
|------		|---	|----	|----	|----	|----	|----	|----	|----	|----	|----	|----	|----	|
|Номер п/п	|12	|18	|10	|17	|20	|16	|4	|18	|1	|22	|10	|33	|
|Номер п/п +5	|17	|23	|15	|22	|25	|21	|9	|23	|6	|27	|15	|5	|
|Шифр		|П	|Х	|Н	|Ф	|Ч	|У	|З	|Х	|Е	|Щ	|Н	|Д	|

Шаг шифрования, выполняемый шифром Цезаря, часто включается как часть более сложных схем, таких как шифр Виженера, и все ещё имеет современное приложение в системе ROT13. Как и все моноалфавитные шифры, шифр Цезаря легко взламывается и не имеет практически никакого применения на практике.

Если сопоставить каждому символу алфавита его порядковый номер (нумеруя с 0), то шифрование и дешифрование можно выразить формулами модульной арифметики:

y = (x + k) mod n
x = (y - k + n) mod n

где: x — символ открытого текста, y — символ шифрованного текста, n — мощность алфавита, k — ключ.

## Шифр Атбаш

Шифр простой замены Атбаш использовался для еврейского алфавита и оттуда же получил свое название. Шифрование происходит заменой первой буквы алфавита на последнюю, второй на предпоследнюю. (алеф(первая буква) заменяется на тау(последнюю), бет(вторая) заменяется на шин(предпоследняя) из этих сочетаний шифр и получил свое название).

Шифр Атбаш для английского алфавита:

Исходный алфавит:	A	B	C	D	E	F	G	H	Я	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z

Алфавит замены:  	Z	Y	X	W	V	U	T	S	R	Q	P	O	N	M	L	K	J	Я	H	G	F	E	D	C	B	A

Правило шифрования состоит в замене i-й буквы алфавита буквой с номером n − i + 1 , где n — число букв в алфавите.

# Выполнение лабораторной работы

1. Реализация шифра Цезаря на языке Python для английского алфавита

Мною был написан код для шифрования текста (рис. 1) и разшифровки (рис. 2) шифром Цезаря.

   ![рис. 1. Шифрование текста шифром Цезаря.](images/1.jpg){ #fig:008 width=60% }

   ![рис. 2. Разшифровка текста шифром Цезаря.](images/2.jpg){ #fig:008 width=60% }

Как можно заметить, для шифра Цезаря использовался ключ шифрования k=3. 

2. Реализация шифра Атбаш на языке Python для английского алфавита

Был написан код для шифрования текста (рис. 3) и разшифровки (рис. 4) шифром Абташ.

   ![рис. 3. Шифрование текста шифром Атбаш.](images/3.jpg){ #fig:008 width=60% }

   ![рис. 4. Разшифровка текста шифром Атбаш.](images/4.jpg){ #fig:008 width=60% }

Для шифра Атбаш уже не использовался ключ шифромания, поскольку сам шифр не подразумевает его присутствие.

Можно заметить что сама шифровка шифром Атбаш является и дешефровкой при повтороном применении шифрования (рис. 5).

   ![рис. 5. Повторное шифрование текста шифром Атбаш = дешифрование.](images/5.jpg){ #fig:008 width=60% }

# Библиография

1. ТУИС РУДН

2. Статья "Шифр Атбаш" <https://ru.wikipedia.org/wiki/Атбаш>

# Выводы

Мною были приобретены практические навыки шифрования и дешифрования текстов методом простой замены. Успешно осовоены шифры Цезаря и Атбаша.
