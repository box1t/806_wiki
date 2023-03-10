# 7 день. Схемы МТ, теорема Бойма, Универсальная МТ

## Словарик программиста:

**Термины с лекции:**


## Лирическое отступление:

```yaml
- © МАИ > ВМК > МИСиС
- © Мы можем выиграть стали и сплавов! 
- А у них проходные выше!
- У них проходные под 300!
```

***

# 2.7 Схемы машин Тьюринга

## 2.7.1 Конструирование МТ "сверху вниз"

Нормирование тьюринговских вычислений и теорема о сочетании алгоритмов позволяют конструировать более простые МТ.
- Эта процедура называется конструированием "сверху вниз".

Для конструирования МТ для функции `f` выразим её через более простые функции и составим диаграммы для них. 
- Абсолютно все диаграммы представимы в виде МТ.
- По частям писать программу проще, постепенно декомпозируя её.
- Т.е. надо распараллелить задачи, разбить на куски.
- При разбиении сложных алгоритмов возникают более простые машины (при нисходящей разработке).
- Процесс будем продолжать, пока не получатся диаграммы, включающие только символы элементарных МТ. Это и будет искомая диаграмма.

> Программирование не должно быть подвигом, не должно содержать жестокости и мучений у рабочего...

> Любой ли алгоритм возможно составить путём таких упрощений?

![image](https://user-images.githubusercontent.com/113284506/211112754-8f9dc0ee-e04e-49e9-abdc-2dfa48bc9487.png)

![image](https://user-images.githubusercontent.com/113284506/211112669-8c66bb1a-d5b2-4967-bf67-4971f5b18fe2.png)

***

© В двух соснах человек не путается: сено-солома. А в трёх путается!

> - Первое упрощение на экзамене: двоичная С/С или натуральная (во времена Евклида не было нуля).
> - Алгоритм Евклида портит числа, поэтому работаем с копиями чисел.
> - Два НОДа не надо печатать! Ответ один.
> - Алгоритм Евклида, который что-то делит — шпион!
- Алгоритм может разбиться на: `компаратор` (сравнитель) и `машину вычитания` (вычитает разность чисел, subtract).

***

<details>
<summary>Официальные хитрости на экзамене:</summary>
<br>

  > Диаграммы должны быть нормированными! Мы не хотим `скидки`!
  - 3 вспомогательные буквы в конце работы алгоритма не выводятся.
  - На экзамене для простоты и удобства мы тратим 6$, но клянёмся, что знаем теорему о нормированности.
  - В позиционных системах эти вычисления не применяют. Но здесь, для скорости на жкзамене (а ведь МТ работает мгновенно), мы идём на этот шаг.
  
</details>

<details>
<summary>Немного лирики о МТ:</summary>
<br>

  - Дискретная математика объясняет истину и ложь в МТ (машина конъюнкции в частности, компаратор).
  - Длина числового слова в позиционное системе счисления растёт ***логарифмически***, а не линейно (см. материал 2 лекции)
  - Отношение компактности систем — отношение логарифмов!
    
</details>

***

```yaml
© Кто не умеет решать задачи, тот лыжник-теоретик!
```

## 2.7.2 Определение схемы МТ 

- `Собственная МТ` имеет одно начальное и одно конечное состояние.
- В состав диаграммы для этой МТ могут входить ***несобетвенные МТ***.
- Если диаграмма содержит только собственные МТ, то `МТ структурная`.

В процессе конструирования ***"сверху вниз"*** мы применяем декомпозиции, при которых получаются только `структурные МТ`.
- `Схемой` будем называть диаграммы структурных МТ.

> Таким образом, схема МТ — частный случай диаграммы Тьюринга.

### Условия, чтобы МТ являлась схемой:

1) символ точки составляет схему
2) последовательная композиция схем `s1, s2, sn` является схемой
3) если ряд схем `c1, c2, cn` МТ вычисляет ряд предикатов `p1, p2, pn` этих МТ, и `s1, s2, sn` — схемы, то и диаграммы этих схем будут схемами.
4) символы элементарных МТ являются схемами.
5) никакие другие объекты схемами не являются. 

```yaml
- © Маруся — это Яндекс-колонка от Мэил-ру!
- © Олимпиады по математике — это скучно! Перья скрипят..
```

***

## 2.7.3 Эквивалентность программ и диаграмм (+ т. Б-Дж-М)

Поскольку при конструировании "сверху вниз" получаются обязательно схемы, возникает вопрос:

> Для любого ли алгоритма можно составить МТ нисходящим образом?

Ответ на вопрос нам даёт теорема Бойма-Джакопини-Миллса.


### Теорема 2.7.3 Бойма-Джакопини-Миллса

> Или теорема о двух итальянцах и примкнувшем к ним американце.

- Для любой МТ можно эффективным образом построить МТ (S), которая является структурой (т.е. диаграмму, которая является схемой) этой МТ.

<details>
<summary>Рассказ про Миллса:</summary>
<br>

  - Раньше в США программистами становились люди без высшего образования.
  - Фирма IBM наняла Миллса, чтобы он научил этих неучей писать программы правильной и простой структуры.
  > - © Английским языком неплохо владеют даже тупые англичане!
  > - © Инженер `минус` математик = программист. Но так говорят те, кто нам завидует..!
    
</details>

`Идея доказательства теоремы`:

- МТ может быть переписана за счёт увеличения алфавита (игра состояний за счет чехарды букв!)
- Вместо команд МТ будет использоваться вспомогательная буква.
- Каждой `нетерминальной команде` поставим в соответствие некоторую структурную машину B:

1) Если команда имеет вид записи букв, то ей соответствует машина перезаписи букв.
2) Если команда МТ имеет вид движения, то ей соответствует машина движения.
3) Если МТ останавливается и меняет состояние, то ей соответствует стоп-машина.

- `Нетерминальная команда` — либо действие (движение?), либо пишет букву. 

- © 1 метр — это 3 страницы! Док-ва меньше метра мы должны приводить!

> © Идея доказательства строится на теореме Шеннона

Следствие теоремы Бойма-Джакопини-Миллса:
Всякая программа может быть написана без стрелок, меток и goto.
- goto — источник ошибок `(как спагетти, не вытянуть из раковины!)`

![image](https://user-images.githubusercontent.com/113284506/211115136-f4253e7d-42a1-4a60-b727-f6653772b962.png)

![image](https://user-images.githubusercontent.com/113284506/211115156-9406ed23-485a-4880-a463-16830c5ccc69.png)

![image](https://user-images.githubusercontent.com/113284506/211115178-0f16efc2-1019-491d-ba35-555cf5336c85.png)

<details>
<summary>Анекдот про нашу кафедру:</summary>
<br>

  - За 40 лет наша кафедра переезжала 7 раз.
  - А вы, наверное, знаете, что 2 переезда равны по силе одному пожару.
  > © Так вот, наша кафедра — это пепелище!
    
</details>

***

## 2.7.4 Док-во теоремы о нормированной вычислимости

Функция нормированно вычислимая по Тьюрингу, если вычисляет функцию, и в то же время удовлетворяет условиям:

1) никогда не может остановиться после применения

2) перечисляет значения функции и останавливается (*на правильных словах МТ отказать и остановиться не может!*)

> При нормированных вычислениях головка не должна заходить левее λ.

```yaml
- Выкинь '#' и ставь пометки.
- Согласно теореме, диез - преступление!
- © 6$!
```

- `Теорема 2.5.4` 
Всякая ВТ-функция является НВТ функцией, причем соответствующая МТ не использует никаких вспомогательных букв.



```yaml
Доказательство просто не поместилось сюда
```

![image](https://user-images.githubusercontent.com/113284506/211115424-c53a54b9-e271-4455-beb5-54efd0011d90.png)


> © Все уважающие себя математики не могли пройти мимо информатики!

***

## 2.8 Развитие алгоритмической модели Тьюринга

## 2.8.1 Понятие об Универсальной МТ:

Все МТ до этого были конкретными константами. 

> © Настоящая прошивка: немки из фирмы Siemens брали провода в иголки и прошивали ими ботинки!
В 1936 году Тьюринг предложил не МТ. Он предложил Универсальную МТ!

- Это машина, моделирующая любую МТ. У обычной МТ программа ***зашита*** внутри (немками из фирмы Siemens).
Линейно записав программу МТ, мы ожидаем, что УМТ может выполнить ВСЁ. 
И сегодня это неудивительно. А вот лет 20 назад сложно было представить перезапись (перепрошивку) МТ.

- Универсальная МТ могла иметь десятки тысяч строк (прошитых в корпусе).

> Первая т. Шеннона рассказывает, как реализовать УМТ, вторая тоже!

- Построение УМТ доказало возможность аппаратной реализации автоматического утройства, `выполняющего любые алгоритмы по их описаниям`.
- Построив аппаратуру УМТ, мы получили бы возможность автоматически обрабатывать данные.
- `Универсальность` — способность системы моделировать работу любой другой системы, когда описание последней подаётся на вход в закодированном виде.
- `Доказать универсальность системы` — значит показать, что она может моделировать поведение системы, универсальность которой доказана. 


Стивен Вольфрам построил МТ из 2 состояний и 5 букв.

![image](https://user-images.githubusercontent.com/113284506/211116235-081a8791-efa4-4c14-8ed1-b5c2e62c3059.png)

![image](https://user-images.githubusercontent.com/113284506/211116253-184fba0b-8bf2-48e3-8e76-9e69210e3451.png)

```yaml
© Математики — недотёпы:
- они делают то, что нужно, так, как нужно!
```

***

## 2.8.2 Линейная запись схем МТ

Трудность записи схем МТ в том, что они двумерны, хотя на ленту можно поместить только линейную запись.
- Схемы допускают всего 3 вида сочетаний: `композицию`, `ветвление` и `цикл`.

1) `Композиция` — последовательность выполнения нескольких действий. Она и так линейна, ведь композиция записывает символы действий друг за другом. 

2) `Ветвление` 

![image](https://user-images.githubusercontent.com/113284506/211117097-a27158d9-b64c-4c6f-93d2-2e4966a79779.png)

![image](https://user-images.githubusercontent.com/113284506/211117135-c876b8dd-f6ba-4b1d-bf27-633c81c051f5.png)

![image](https://user-images.githubusercontent.com/113284506/211116954-3fce8c50-ac40-4a3d-b6aa-db28ba735e31.png)


3) `Цикл` 

![image](https://user-images.githubusercontent.com/113284506/211117186-47d70b3c-27cd-4480-9686-bdf0b4db9778.png)

***

## 2.8.3 Язык ОСТ (описания схем Тьюринга) 

![image](https://user-images.githubusercontent.com/113284506/211117257-5a2e2b49-de4c-4b8d-ae6d-0d8571e2e842.png)

```yaml
прекрасный, лаконичный язык!
```
