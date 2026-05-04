🐱 CatLang

Функциональный язык программирования с кошачьим синтаксисом!  
«Мяукает, но вычисляет как надо» ✨



👥 Команда

Участник	Роль	Вклад
Сысоева Кира	Разработчик интерпретатора, документация	AST-деревья, интерпретатор (eval/apply), замыкания, GitHub Pages, документация
Янкавцев Кирилл	Разработчик парсера, тестирование	Парсер (FParsec), модульные тесты, примеры программ


📋 О проекте

CatLang — это функциональный язык программирования с кошачьим синтаксисом, разработанный в рамках курсового проекта. Язык основан на лямбда-исчислении и реализован на F# с использованием FParsec и платформы .NET 8.0.

Концепция

Каждая синтаксическая конструкция языка стилизована под кошачьи звуки и повадки. Код на CatLang выглядит так, будто котик объясняет алгоритм другому котику, но под капотом — строгое лямбда-исчисление с замыканиями и каррированием.


🌸 Синтаксис

Три принципа CatLang

1. Всё — котики

Обычный язык	CatLang
function	play_again!
let	meow
if/then/else	UwU ... happy:) ... OwO
lambda	cat_game x ->
true/false	yesss;3 / nooo:(
print	say:3
read	listen:3
[] (пустой список)	hug()
head	first_cat
tail	last_cat



2. Префиксная запись с please

Обычный синтаксис	CatLang
fact(5)	fact please 5
2 + 3	2 :) 3
head(list)	first_cat please list



3. Выражения, а не инструкции

Всё — выражение. Нет return, нет оператора присваивания.

UwU n smaller_cat 2
    happy:) 1
    OwO n :* (factorial please (n :( 1))



📐 Таблица токенов

Токен	Значение
play_again! f 0.0 cat_game x -> ... nya	Определение рекурсивной функции
meow x 0.0 значение nya	Let-биндинг
UwU ... happy:) ... OwO ...	Условное выражение
cat_game x -> выражение	Лямбда-функция
f please x	Применение функции (аппликация)
yesss;3	Истина (true)
nooo:(	Ложь (false)
hug()	Пустой список
a :: b	Cons (добавить элемент в голову)
first_cat	Голова списка
last_cat	Хвост списка
:)	Сложение (+)
:(	Вычитание (-)
:*	Умножение (*)
}:(	Деление (/)
same_cats	Равенство (==)
not_same_cats	Неравенство (!=)
smaller_cat	Меньше (<)
bigger_cat	Больше (>)
smol_or_equal_cat	Меньше или равно (<=)
big_or_equal_cat	Больше или равно (>=)
say:3	Вывод на экран (print)
listen:3	Ввод с клавиатуры (read)
two_halves:3 ... love>.<	Pattern matching


🚀 Быстрый старт

git clone https://github.com/sparrUwU/cutelang.git
cd cutelang
dotnet run -- examples/fact.cat
dotnet test


🎯 Примеры

Факториал

play_again! factorial 0.0 cat_game n ->
    UwU n smaller_cat 2
        happy:) 1
        OwO n :* (factorial please (n :( 1))
nya

say:3 (factorial please 5)

Результат: 120

Числа Фибоначчи

play_again! fib 0.0 cat_game n ->
    UwU n smaller_cat 3
        happy:) 1
        OwO (fib please (n :( 1)) :) (fib please (n :( 2))
nya

say:3 (fib please 6)

Результат: 8

Map

play_again! map 0.0 cat_game f lst ->
    two_halves:3 lst love>.<
        | hug() -> hug()
        | h :: t -> (f please h) :: (map please f please t)
nya

play_again! double 0.0 cat_game x -> x :* 2 nya

meow numbers 0.0 (1 :: 2 :: 3 :: 4 :: hug()) nya
say:3 (map please double please numbers)

Результат: (2 :: 4 :: 6 :: 8 :: hug())

Списки

meow mylist 0.0 (10 :: 20 :: 30 :: 40 :: hug()) nya

say:3 (first_cat please mylist)    | 10
say:3 (last_cat please mylist)     | (20 :: 30 :: 40 :: hug())

Pattern Matching

meow lst 0.0 (1 :: 2 :: 3 :: hug()) nya

two_halves:3 lst love>.<
    | hug() -> say:3 "Empty list"
    | h :: t -> 
        say:3 "First:"
        say:3 h
        say:3 "Rest:"
        say:3 t
nya


✨ Реализованные возможности

Возможность	Статус	Синтаксис
Именованные привязки (let)	✅	meow x 0.0 ... nya
Рекурсия	✅	play_again!
Функции первого класса	✅	cat_game x ->
Замыкания	✅	—
Списки / Последовательности	✅	::, hug(), first_cat, last_cat
Библиотечные функции списков	✅	first_cat, last_cat
Pattern matching	✅	two_halves:3 ... love>.<
Ввод-вывод	✅	say:3, listen:3
Арифметические операции	✅	:), :(, :*, }:(
Операции сравнения	✅	smaller_cat, bigger_cat, same_cats, not_same_cats


🏛️ Архитектура

src/
├── Ast.fs              # Абстрактное синтаксическое дерево
├── Value.fs            # Типы значений (VClosure, VRecClosure, VList)
├── Parser.fs           # Парсер на FParsec
├── Interpreter.fs      # Интерпретатор (eval/apply)
├── Program.fs          # Точка входа
└── CatLang.fsproj      # Проект F# (.NET 8.0)

examples/
├── fact.cat            # Факториал
├── fib.cat             # Числа Фибоначчи
├── map.cat             # Map над списком
├── lists.cat           # Работа со списками
├── match.cat           # Pattern matching
└── simple_math.cat     # Арифметика


📄 Лицензия

MIT — Мяукайте свободно (◕‿◕✿)
