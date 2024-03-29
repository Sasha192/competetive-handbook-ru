# Руководство для олимпиадного программиста

> Антти Лааксонен <br>
> Черновик 15 октября 2017 года

<br>
<br>
<br>
<br>

## Оглавление

### Предисловие

### Часть 1. Основные методы

* #### Глава 1. Введение
  * Языки программирования
  * Ввод и вывод
  * Работа с числами
  * Сокращение кода
  * Математика
  * Конкурсы и ресурсы
  
* #### Глава 2. Временная сложность
  * Правила счета
  * Сложные классы
  * Оценка эффективности
  * Максимальная сумма подмассива

* #### Глава 3. Сортировка
  * Теория сортировки
  * Сортировка в C++
  * Двоичный поиск

<br>
<br>
<br>
<br>

## Предисловие

Цель этой книги - ввести вас в олимпиадное программирование. Предполагается, что вы уже знакомы с основами программирования, однако опыт по олимпиадному программированию не требуется.

Данная книга предназначена для студентов, которые хотят изучить алгоритмы программирования и, возможно, принять участие в International Olympiad in Informatics (IOI) или в International Collegiate Programming Contest (ICPC). Соответственно, книга также подойдет для любого другого человека, заинтересованного в программировании.

Понадобится много времени, чтобы стать профессионалом в олимпиадном программировании, но это отличная возможность многому научиться. Вы можете быть уверены, что вы получите всеобщее понимание об алготитмах, если вы проведете время за чтением книги, решая задачи и участвуя в конкурсах.

Книга находится в садии непрерывного развития. Вы всегда можете отправить свой отзыв о ней на *ahslaaks@cs.helsinki.fi*.

> Хельсинки, октябрь 2017 года<br>
> Антти Лааксонен

<br>
<br>

# Часть 1. Основные методы

<br>

# Глава 1
## Введение

Олимпиадное программирование объединяет две темы: (1) **проектирование алгоритмов** и (2) **реализация алгоритмов**.

**Проектирование алгоритмов** состоит из решения задач и математического мышления.Необходимы навыки для анализа проблем и их решения. Алгоритм решения проблемы должен быть как правильным, так и эффективным, и ядро проблемы часто связано с изобретением эффективного алгоритма.

Теоретические знания алгоритмов важны для олимпиадных программистов. Как правило, решение проблемы представляет собой комбинацию хорошо известных методов и новых идей. Методы, которые появляются в олимпиадном программировании, также составляют основу для научных исследований алгоритмов.

Для **реализации алгоритмов** требуются хорошие навыки программирования. В олимпиадном программировании решения оцениваются путем тестирования реализованного алгоритма с использованием набора тестовых примеров. Таким образом, недостаточно, чтобы идея алгоритма была правильной, реализация также должна быть правильной.

Хороший стиль написания кода в конкурсах прост и краток. Программы должны быть написаны быстро, потому что времени мало. В отличие от традиционной разработки программного обеспечения, программы коротки (обычно не более нескольких сотен строк), и их не нужно поддерживать после конкурса.

## Языки программирования

На данный момент самые популярные языки программирования, используемые в конкурсах, C++, Python и Java. Например, в Google Code Jam 2017, среди лучших 3000 участников, 79% использовали C++, 16% использовали Python и 8% использовали Java. Некоторые участники также использовали другие языки.

Многие считают, что C++ - лучший выбор для олимпиадного программиста, C++ почти всегда доступен в конкурсных системах проверки. Преимуществом использования C++ является то, что это очень эффективный язык, и его стандартная библиотека содержит большой набор структурданных и алгоритмов.

С другой стороны, хорошо владеть несколькими языками и понимать их сильные стороны. Например, если нужно использовать большие целые числа, то Python может быть хорошим выбором, поскольку он содержит встроенные операции для вычисления больших целых чисел. Тем не менее, большинство проблем в конкурсах программирования установлены так, что использование конкретного языка программирования не является несправедливым преимуществом.

Все примеры программ в этой книге написаны на C++, а стандартные
библиотеки и алгоритмы используются очень часто.

Программы соответствуют стандарту `C++11`, который можно использовать в большинстве конкурсов в настоящее время. Если ты не умеешь программировать на C++, то сейчас самое подходящее время для начала обучения.

### Шаблон кода на C++

Типичный шаблон кода C++ выглядит следующим образом:

```cpp
#include <bits/stdc++.h>

using namespace std;

int main() {
  // код здесь
}
```

Строка `#include` в начале кода является функцией компилятора g++, что позволяет нам подключить всю стандартную библиотеку. Таким образом, нет необходимости отдельно включать библиотеки, такие как `iostream`, `vector` и `algorithm`.

Строка `using` объявляет, что классы и функции стандартной библиотеки могут быть использованы непосредственно в коде. Без использования строки нам пришлось бы писать, например, `std::cout`, но теперь достаточно написать `cout`.

Код можно скомпилировать, используя следующую команду:

```
g++ -std=c++11 -O2 -Wall test.cpp -o test
```

Эта команда производит бинарный файл test из исходного кода test.cpp. Компилятор следует стандарту `C++11` (-std=c++11), оптимизирует код (-O2) и отображает предупреждения о возможных ошибках (-Wall).

## Ввод и вывод

В большинстве конкурсов используются стандартные потоки для чтения ввода и записи вывода.

В C++ стандартными потоками являются `cin` для ввода и `cout` для вывода. Кроме того, можно использовать функции языка C `scanf` и `printf`.

Ввод для программы обычно состоит из чисел и строк, разделенных пробелами и символами новой строки. Они могут быть прочитаны из потока `cin` следующим образом:

```cpp
int a, b;
string x;
cin >> a >> b >> x;
```

Такой код работает всегда, предполагая, что между каждым элементом во входном файле имеется по крайней мере один пробел или новая линия. Например, приведенный выше код может считывать оба следующих входа:

```
123 456 monkey
```

```
123   456
monkey
```

Поток `cout` используется для вывода следующим образом:

```cpp
int a = 123, b = 456;
string x = "monkey";
cout << a << " " << b << " " << x << "\n";
```

Иногда вход и выход являются узким местом в программе. Следующие
строки в начале кода делают ввод и вывод более эффективными:

```cpp
ios::sync_with_stdio(0);
cin.tie(0);
```

Обратите внимание, что новая строка `«\n»` работает быстрее, чем `endl` потому что `endl` всегда вызывает операцию сброса.

Функции языка C `scanf` и `printf` являются альтернативой стандартным потокам C++. Они, как правило, немного быстрее, но сложнее в использовании. Следующий код считывает из ввода два целых числа:

```c
int a, b;
scanf("%d %d", &a, &b);
```
А этот код выводит два целых числа

```c
int a = 123, b = 456;
printf("%d %d\n", a, b);
```

Иногда программа должна cчитать целую строку из ввода, возможно, содержащую пробелы. Это можно выполнить с помощью функции `getline`:

```cpp
string s;
getline(cin, s);
```

Если количество данных неизвестно, полезен следующий цикл:

```cpp
while (cin >> x) {
// код
}
```

Этот цикл считывает элементы из ввода один за другим, пока на входе больше нет данных.

В некоторых системах проверки конкурсов для ввода и вывода используются файлы. Легким решением для этого является запись кода, как обычно, с использованием стандартных потоков, но нужно добавить следующие строки в начало кода:

```cpp
freopen("input.txt", "r", stdin);
freopen("output.txt", "w", stdout);
```

После этого программа считывает ввод из файла *«input.txt»* и записывает вывод в файл *«output.txt»*.

## Работа с числами
### Целые числа (integers)

Наиболее используемым целым типом в конкурентном программировании является `int`, который представляет собой 32-разрядный тип с диапазоном значений −2<sup>31</sup>...2<sup>31</sup>−1 или -2 * 10<sup>-9</sup>...2 * 10<sup>9</sup>
Если типа `int` недостаточно, можно использовать 64-битный тип `long long`. Он имеет диапазон значений −2<sup>63</sup>...2<sup>63</sup>−1 или -2 * 10<sup>-18</sup>...2 * 10<sup>18</sup>.

Следующий код определяет переменную `long long`:

```cpp
long long x = 123456789123456789LL;
```

Суффикс `LL` означает, что тип числа - `long long`.

Общей ошибкой при использовании типа `long long` является то, что тип `int` все еще используется где-то в коде. Например, следующий код содержит тонкую ошибку:

```cpp
int a = 123456789;
long long b = a*a;
cout << b << "\n"; // -1757895751
```

Несмотря на то, что переменная `b` имеет тип `long long`, оба числа в выражении `a * a` имеют тип `int`, а результат также имеет тип `int`. Из-за этого переменная `b` будет содержать неправильный результат. Проблема может быть решена путем изменения типа `a` до `long long` или путем изменения выражения `(long long) a * a`.

Обычно конкурсные задачи устроены так, что достаточно типа `long long`. Тем не менее, хорошо знать, что компилятор g++ также предоставляет 128-битный тип `__int128_t` с диапазоном значений −2<sup>127</sup>...2<sup>127</sup>−1 или -2 * 10<sup>-38</sup>...2 * 10<sup>38</sup>. Однако этот тип недоступен во всех конкурсных системах проверки.

### Модульная арифметика

/// Позже

### Числа с плавающей точкой

Обычными типами с плавающей точкой в олимпиадном программировании являются 64-битный `double` и, как расширение в компиляторе g++, 80-битный `long double`. В большинстве случаев `double` достаточно, но `long double` более точный.

Требуемая точность ответа обычно указывается в условии задачи. Легкий способ вывода ответа - использовать функцию `printf` и указать число десятичных знаков в строке форматирования. Например, следующий код печатает значение `x` с 9 знаками после точки:

```cpp
printf("%.9f\n", x);
```

Трудность при использовании чисел с плавающей точкой состоит в том, что некоторые числа не могут быть точно представлены как числа с плавающей точкой, и, соответственно, будут ошибки округления. Например, результат следующего кода удивляет:

```cpp
double x = 0.3*3+0.1;
printf("%.20f\n", x); // 0.99999999999999988898
```

Из-за ошибки округления значение x немного меньше 1.

Рискованно сравнивать числа с плавающей точкой оператором `==`, потому что возможно, что значения должны быть равны, но они не равны из-за ошибок точности. Лучший способ сравнения чисел с плавающей точкой - предположить, что два числа равны, если разница между ними меньше ε, где ε - меньшее число.

На практике числа можно сравнить следующим образом (ε = 10<sup>-9</sup>)

```cpp
if (abs(a-b) < 1e-9) {
// a и b равны
}
```

Обратите внимание, что, хотя числа с плавающей точкой неточны, целые числа до определенного предела могут быть представлены точно. Например, используя `double`, можно точно представлять все целые числа, абсолютное значение которых не более 2<sup>53</sup>.

## Сокращение кода

Короткий код идеален в олимпиадном программировании, потому что программы должны быть написаны как можно быстрее. Из-за этого олимпиадные программисты часто определяют более короткие имена для типов данных и других частей кода.

### Имена типов

Используя команду `typedef`, можно присвоить более короткое имя типу данных. Например, имя `long long` длинное, поэтому мы можем определить более короткое имя `ll`:

```cpp
typedef long long ll;
```

После этого код

```cpp
long long a = 123456789;
long long b = 987654321;
cout << a*b << "\n";
```

можно сократить следующим образом:

```cpp
ll a = 123456789;
ll b = 987654321;
cout << a*b << "\n";
```

Команда `typedef` также может использоваться с более сложными типами. Например, следующий код дает имя `vi` для вектора целых чисел и имя `pi` для пары, которая содержит два целых числа.

```cpp
typedef vector<int> vi;
typedef pair<int,int> pi;
```

### Макросы

Другим способом сокращения кода является определение **макросов**. Макрос означает, что некоторые строки кода будут изменены перед компиляцией. В C++ макросы определяются с помощью ключевого слова `#define`.

Например, мы можем определить следующие макросы:
```cpp
#define F first
#define S second
#define PB push_back
#define MP make_pair
```

После этого код

```cpp
v.push_back(make_pair(y1,x1));
v.push_back(make_pair(y2,x2));
int d = v[i].first+v[i].second;
```

можно сократить следующим образом:

```cpp
v.PB(MP(y1,x1));
v.PB(MP(y2,x2));
int d = v[i].F+v[i].S;
```

Макрос может также иметь параметры, которые позволяют сокращать циклы и другие структуры. Например, мы можем определить следующий макрос:

```cpp
#define REP(i,a,b) for (int i = a; i <= b; i++)
```

После этого код

```cpp
for (int i = 1; i <= n; i++) {
  search(i);
}
```

можно сократить следующим образом:

```cpp
REP(i,1,n) {
  search(i);
}
```

Иногда макросы вызывают ошибки, которые трудно обнаружить. Например, рассмотрим следующий макрос, который вычисляет квадрат числа:

```cpp
#define SQ(a) a*a
```
Этот макрос *не всегда* работает должным образом. Например, код

```cpp
cout << SQ(3+3) << "\n";
```

соответствует коду

```cpp
cout << 3+3*3+3 << "\n"; // 15
```

Лучшая версия макроса выглядит следующим образом:

```cpp
#define SQ(a) (a)*(a)
```

Теперь код

```cpp
cout << SQ(3+3) << "\n";
```

соответствует коду

```cpp
cout << (3+3)*(3+3) << "\n"; // 36
```

## Математика

Математика играет важную роль в олимпиадном программировании, и невозможно стать успешным олимпиадным программистом, не имея хороших математических навыков. В этом разделе обсуждаются некоторые важные математические концепции и формулы, которые будут необходимы в книге позже.

### Формулы суммы
### Теория множеств
### Логика
### Функции
### Логарифмы

**Логарифм** числа `x` обозначается log<sub>k</sub>(x), где `k` - основание логарифма. Согласно определению, log<sub>k</sub>(x) = a точен при k<sup>a</sup> = x.

Полезным свойством логарифмов является то, что log<sub>k</sub>(x) равен числу раз, когда мы должны разделить x на k, прежде чем мы достигнем числа 1. Например, log<sub>2</sub>(32) = 5, потому что необходимо 5 раз делить на 2:

32 → 16 → 8 → 4 → 2 → 1

Логарифмы часто используются при анализе алгоритмов, потому что многие эффективные алгоритмы вдвое сокращают что-то на каждом шаге. Следовательно, мы можем оценить эффективность таких алгоритмов, используя логарифмы.

log<sub>k</sub>(ab) = log<sub>k</sub>(a) + log<sub>k</sub>(b),

и следовательно,

log<sub>k</sub>(x<sup>n</sup>) = n * log<sub>k</sub>(x).

Натуральный логарифм ln(x) числа x является логарифмом, основание которого `e ≈ 2,71828`. Другим свойством логарифмов является то, что число цифр целого числа x в основании b является log<sub>b</sub>(x) + 1. Например, представление 123 в основании 2 равно 1111011 и log<sub>2</sub>(123) + 1 = 7.

## Конкурсы и ресурсы
### IOI

*Международная олимпиада по информатике (IOI)* - это ежегодный конкурс программистов для учащихся средних школ. Каждой стране разрешено отправлять на конкурс группу из четырех человек. Как правило, около 300 участников из 80 стран.

IOI состоит из двух пятичасовых конкурсов. В обоих соревнованиях участникам предлагается решить три задачи алгоритма различной сложности. Задачи делятся на подзадачи, каждый из которых имеет назначенный балл. Даже если конкурсанты делятся на команды, они конкурируют как люди.

Программа IOI регулирует темы, которые могут появляться в задачах IOI. Эта статья охватывает почти все темы в учебной программе IOI.

Участники IOI выбираются по национальным конкурсам. Перед IOI организовано много региональных конкурсов, таких как Балтийская олимпиада по информатике **(BOI)**, Центрально-европейская олимпиада по информатике **(CEOI)** и Азиатско-тихоокеанская олимпиада по информатике **(APIO)**.

Некоторые страны организуют онлайн-конкурсы для будущих участников IOI, таких как *Открытый конкурс хорватов в области информатики* и *компьютерная Олимпиада США*. Кроме того, в Интернете имеется большой набор задач из польских конкурсов.

### ICPC

*Конкурс международного коллегиального программирования (ICPC)* - это ежегодный конкурс программистов для студентов университетов. Каждая команда в конкурсе состоит из трех студентов, и в отличие от ИОИ студенты работают вместе; для каждой команды доступен только один компьютер.

ICPC состоит из нескольких этапов, и, наконец, лучшие команды приглашаются на финал чемпионата мира. Хотя в конкурсе участвуют десятки тысяч участников, доступно лишь небольшое количество финальных слотов, поэтому даже продвижение к финалу является большим достижением в некоторых регионах.

На каждом конкурсе ICPC команды имеют пять часов времени, чтобы решить около десяти задач. Решение задачи принимается только в том случае, если оно эффективно решает все тестовые примеры. Во время соревнований участники могут просматривать результаты других команд, но за последний час табло замерзает, и результаты последних решений невозможны.

Темы, которые могут появиться в ICPC, не так хорошо указаны, как те, что указаны в IOI. В любом случае ясно, что в ICPC требуется больше знаний, особенно математических.

### Онлайн конкурсы

Есть много бесплатных конкурсов, которые доступны для всех. На данный момент самым активным сайтом с конкурсами является `Codeforces`, который организует конкурсы еженедельно. В `Codeforces` участники делятся на два подразделения: новички участвуют в *Div2* и более опытные программисты в *Div1*. Другие сайты - `AtCoder`, `CS Academy`, `HackerRank` и `Topcoder`.

Некоторые компании организуют онлайн-конкурсы с финалами на месте. Примерами таких конкурсов являются *Facebook Hacker Cup*, *Google Code Jam* и *Yandex.Algorithm*. Конечно, компании также используют эти конкурсы для рекрутинга: хорошо выступать в конкурсе - это хороший способ доказать свои навыки.

### Книги

Есть некоторые книги (помимо этой книги), в которых основное внимание уделяется также олимпиадному программированию и алгоритмическому решению проблем:

* S. S. Skiena and M. A. Revilla: Programming Challenges: The Programming Contest Training Manual
* S. Halim and F. Halim: Competitive Programming 3: The New Lower Bound of Programming Contests
* K. Diks et al.: Looking for a Challenge? The Ultimate Problem Set from the University of Warsaw Programming Competitions

Первые две книги предназначены для новичков, тогда как последняя книга содержит усложненные материалы.

Конечно, общие книги также подходят для олимпиадных программистов.
Некоторые популярные книги:

* T. H. Cormen, C. E. Leiserson, R. L. Rivest and C. Stein: Introduction to Algorithms
* J. Kleinberg and É. Tardos: Algorithm Design
* S. S. Skiena: The Algorithm Design Manual

# Глава 2. Временная сложность

В олимпиадном программировании важна эффективность алгоритмов. Обычно легко разработать алгоритм, который решает проблему медленно, но задачей является выработка быстрого алгоритма. Если алгоритм слишком медленный, он получит только частичные решения или не получит вовсе.

Временная сложность алгоритма оценивает, сколько времени алгоритм будет использовать для некоторого ввода. Идея состоит в том, чтобы представить эффективность как функцию, параметром которой является размер ввода. Вычислив временную сложность, мы можем выяснить, достаточно ли быстрый алгоритм, не реализуя его.

## Правила счета

Сложность времени алгоритма обозначается O(...), где три точки представляют некоторую функцию. Обычно переменная `n` обозначает размер ввода. Например, если вход представляет собой массив чисел, `n` будет размером массива, а если вход является строкой, `n` будет длиной строки.

### Циклы

Частой причиной медленного алгоритма является то, что он содержит много циклов, которые проходят через вход. Чем больше вложенных циклов содержит алгоритм, тем он медленнее. Если есть `k` вложенных циклов, сложность времени - O(n<sup>k</sup>).

Например, временной сложностью следующего кода является `O(n)`:

```cpp
for (int i = 1; i <= n; i++) {
  // код
}
```

А временная сложность следующего кода равна O(n<sup>2</sup>):

```cpp
for (int i = 1; i <= n; i++) {
  for (int j = 1; j <= n; j++) {
    // код
  }
}
```

### Порядок величины

Сложность времени не говорит нам о том, сколько раз внутри цикла выполняется код, но она показывает только порядок величины. В следующих примерах код внутри цикла выполняется `3n`, `n + 5` и `n / 2` раз, но временная сложность каждого кода равна `O(n)`.

```cpp
for (int i = 1; i <= 3*n; i++) {
  // код
}
```

```cpp
for (int i = 1; i <= n+5; i++) {
  // код
}
```

```cpp
for (int i = 1; i <= n; i += 2) {
  // код
}
```

В качестве еще одного примера временной сложностью следующего кода является O(n<sup>2</sup>):

```cpp
for (int i = 1; i <= n; i++) {
  for (int j = i+1; j <= n; j++) {
    // код
  }
}
```

### Этапы

Если алгоритм состоит из последовательных этапов, общая временная сложность - это наибольшая временная сложность  одного этапа. Причина этого в том, что самый медленный этап обычно является узким местом кода. Например, следующий код состоит из трех этапов с временными сложностями O(n), O(n<sup>2</sup>) и O(n). Таким образом, общая временная сложность - O(n2).

```cpp
for (int i = 1; i <= n; i++) {
  // код
}
for (int i = 1; i <= n; i++) {
  for (int j = 1; j <= n; j++) {
    // код
  }
}
for (int i = 1; i <= n; i++) {
  // код
}

```

### Несколько переменных

Иногда временная сложность зависит от нескольких факторов. В этом случае формула временной сложности содержит несколько переменных.

Например, временная сложность следующего кода:  O(nm):

```cpp
for (int i = 1; i <= n; i++) {
  for (int j = 1; j <= m; j++) {
    // code
  }
}
```

### Рекурсия

Временная сложность рекурсивной функции зависит от количества вызовов функции и временной сложности одного вызова. Общая временная сложность является произведением этих значений.

Например, рассмотрим следующую функцию:

```cpp
void f(int n) {
  if (n == 1) return;
  f(n-1);
}
```

Вызов f(n) вызывает `n` вызовов функций, а временная сложность каждого вызова - `O(1)`. Таким образом, общая временная сложность -  `O(n)`.

В качестве другого примера рассмотрим следующую функцию:

```cpp
void g(int n) {
  if (n == 1) return;
  g(n-1);
  g(n-1);
}
```

В этом случае каждый вызов функции генерирует два других вызова, кроме `n = 1`. Посмотрим, что произойдет, когда `g` вызывается с параметром `n`. В следующей таблице показаны вызовы функций, вызванные этим единственным вызовом:

Вызов функции      | Количество вызовов 
:-------- |:-----
g(n)  | 1
g(n−1)     | 2
g(n−2)      | 4
...      | ...
g(1)      | 2<sup>n−1</sup>

Исходя из этого, временная сложность:

1 + 2 + 4 + ··· + 2<sup>n−1</sup> = 2<sup>n</sup> − 1 = O(2<sup>n</sup>).

## Сложные классы

Следующий список содержит общие временные сложности алгоритмов:

* O(1) 
Время работы алгоритма с **постоянным временем** не зависит от размера ввода. Типичный алгоритм с постоянным временем - это прямая формула, которая вычисляет ответ.

* O(log n)
**Логарифмический** алгоритм часто уменьшает размер ввода на каждом шаге. Время работы такого алгоритма логарифмическое, так как log2 n равно числу раз n, нужно разделить на 2, чтобы получить 1.

* O(√n)
Алгоритм с **квадратным корнем** медленнее, чем O(log n), но быстрее, чем O(n). Особое свойство квадратных корней состоит в том, что √n = n / √n, поэтому квадратный корень √n лежит в некотором смысле в середине ввода.

* O(n)
**Линейный** алгоритм проходит через вход постоянное число раз. Часто, это самая лучшая временная сложность, потому что обычно требуется доступ к каждому входному элементу, по крайней мере, один раз, прежде чем сообщать ответ.

* O(n log n)
Эта временная сложность часто указывает на то, что алгоритм сортирует входные данные, поскольку временная сложность эффективных алгоритмов сортировки - O(n log n). Другая возможность заключается в том, что алгоритм использует структуру данных, где каждая операция принимает время O(log n).

* O(n<sup>2</sup>)
**Квадратичный** алгоритм часто содержит два вложенных цикла. Можно пройти через все пары входных элементов за O(n<sup>2</sup>) времени.

* O(n<sup>3</sup>)
**Кубический** алгоритм часто содержит три вложенных цикла. Можно пройти через все пары входных элементов за O(n<sup>3</sup>) времени.

* O(2<sup>n</sup>)
Эта временная сложность часто указывает на то, что алгоритм выполняет итерацию через все подмножества входных элементов. Например, подмножества {1, 2, 3} являются: ø, {1}, {2}, {3}, {1, 2}, {1, 3}, {2, 3} и {1, 2, 3}.

* O(n!)
Эта временная сложность часто указывает на то, что алгоритм выполняет итерацию через все перестановки входных элементов. Например, перестановки {1, 2, 3} равны (1, 2, 3), (1, 3, 2), (2, 1, 3), (2, 3, 1), (3, 1, 2) и (3, 2, 1).

Алгоритм является **многочленом**, если его временная сложность не превосходит O(n<sup>k</sup>), где `k`- постоянная. Все перечисленные выше временные сложности, кроме O(2<sup>n</sup>) и O(n!) являются многочленными. На практике константа `k` обычно мала, поэтому полиномиальная временная сложность грубо означает, что алгоритм эффективен.

Большинство алгоритмов в этой книге многочлены. Тем не менее, существует много важных проблем, для которых не известен полиномиальный алгоритм, т. е. никто не знает, как эффективно их решать.

## Оценка эффективности

Вычисляя временную сложность алгоритма, перед выполнением алгоритма можно проверить, что он достаточно эффективен для проблемы. Отправной точкой для оценок является тот факт, что современный компьютер может выполнить несколько сотен миллионов операций за секунду.

Например, предположим, что ограничение времени для одной задачи равно одной секунде, а размер ввода равен `n = 105`. Если временная сложность равна O(n<sup>2</sup>), алгоритм будет выполнять около (10<sup>5</sup>)<sup>2</sup> = `1010` операций. Это должно занимать не менее нескольких десятков секунд, поэтому алгоритм кажется слишком медленным для решения проблемы.

С другой стороны, учитывая размер ввода, мы можем попытаться угадать требуемую временную сложность алгоритма, который решает проблему. В следующей таблице приведены некоторые полезные оценки, предполагающие ограничение на одну секунду.

Размер ввода      | Временная сложность
:-------- |:-----
n ≤ 10 | O(n!)
n ≤ 20 | O(2<sup>n</sup>)
n ≤ 500 | O(n<sup>3</sup>)
n ≤ 5000 | O(n<sup>2</sup>)
n ≤ 10<sup>6</sup> | O(n log n) или O(n)
n больше | O(1) или O(log n)

Например, если размер ввода равен n = 10<sup>5</sup>, вероятно, ожидается, что временная сложность алгоритма равна O(n) или O (n log n). Эта информация упрощает разработку алгоритма, поскольку он исключает подходы, которые могут дать алгоритм с худшей временной сложностью.

Тем не менее, важно помнить, что временная сложность - это только оценка эффективности, поскольку она скрывает *постоянные факторы*. Например, алгоритм, который работает в O(n) времени, может выполнять операции n / 2 или 5n. Это оказывает существенное влияние на фактическое время работы алгоритма.

### Максимальная сумма подмассива

# Глава 3. Сортировка

`Сортировка` - фундаментальная проблема проектирования алгоритма. Многие эффективные алгоритмы используют сортировку в качестве подпрограммы, поскольку часто обрабатываются данные, если элементы находятся в упорядоченном порядке.

Например, проблема «содержит ли массив два равных элемента?», Легко решить с помощью сортировки. Если массив содержит два равных элемента, они будут рядом друг с другом после сортировки, поэтому их легко найти. Кроме того, проблема «что является самым частым элементом в массиве?» Может быть решена аналогичным образом.
Существует множество алгоритмов сортировки, и они также являются хорошими примерами применения различных методов проектирования алгоритмов. Эффективные общие алгоритмы сортировки работают в O (n log n) времени, и многие алгоритмы, которые используют сортировку в качестве подпрограммы, также имеют сложность во времени.

## Теория сортировки

Основная задача при сортировке заключается в следующем:

```
Дан массив, содержащий n элементов, ваша задача состоит в сортировке элементов в порядке возрастания.
```

Например, массив

<img src="https://rawgit.com/maxtereshko/competetive-handbook-ru/master/img/s1.PNG">

будет выглядеть следующим образом после сортировки:

<img src="https://rawgit.com/maxtereshko/competetive-handbook-ru/master/img/s2.PNG">

### Алгоритмы O(n<sup>2</sup>)

Простые алгоритмы сортировки массива работают за время O(n<sup>2</sup>). Такие алгоритмы короткие и обычно состоят из двух вложенных циклов. Известный алгоритм сортировки за время O(n<sup>2</sup>) - это **сортировка пузырьком**, в которой элементы «пузырятся» в массиве в соответствии с их значениями.

Сортировка пузырьом состоит из n этапов. В каждом этапе алгоритм выполняет итерацию через элементы массива. Всякий раз, когда обнаруживаются два последовательных элемента, которые не в правильном порядке, алгоритм меняет их. Алгоритм может быть реализован следующим образом:

```cpp
for (int i = 0; i < n; i++) {
  for (int j = 0; j < n-1; j++) {
    if (array[j] > array[j+1]) {
      swap(array[j],array[j+1]);
    }
  }
}
```

После первого раунда алгоритма наибольший элемент будет в правильном положении, и в целом, после k раундов, k наибольших элементов будут в правильных положениях. Таким образом, после n раундов весь массив будет отсортирован.

Например, в массиве

<img src="https://rawgit.com/maxtereshko/competetive-handbook-ru/master/img/s3.PNG">

первый этап сортировки элементов пузырьком выглядит следующим образом:

<img src="https://rawgit.com/maxtereshko/competetive-handbook-ru/master/img/s4.PNG">

### Инверсия

Сортировка пузырьком - пример алгоритма сортировки, который всегда меняет последовательные элементы массива. Оказывается, временная сложность такого алгоритма всегда не меньше O(n<sup>2</sup>), так как в худшем случае для сортировки массива требуются свопы O(n<sup>2</sup>).

Полезной концепцией при анализе алгоритмов сортировки является инверсия: пара элементов массива `(array[a], array[b])`, так что `a < b и array[a] > array[b]`, т. е. элементы находятся в неправильном порядке. Например, массив

<img src="https://rawgit.com/maxtereshko/competetive-handbook-ru/master/img/s5.PNG">

имеет три инверсии: (6, 3), (6, 5) и (9, 8). Количество инверсий указывает, какая работа необходима для сортировки массива. Массив полностью отсортирован, когда нет инверсий. С другой стороны, если элементы массива находятся в обратном порядке, число инверсий максимально возможное:

<img src="https://rawgit.com/maxtereshko/competetive-handbook-ru/master/img/s6.PNG">

Перестановка пары последовательных элементов, которые находятся в неправильном порядке снимает ровно одна инверсию из массива. Следовательно, если алгоритм сортировки может заменять только последовательные элементы, каждый своп удаляет не более одной инверсии, а временная сложность алгоритма - не менее O(n<sup>2</sup>).

### Алгоритмы O(n log n)

Можно эффективно сортировать массив за время O(n log n) с использованием алгоритмов, которые не ограничиваются заменой последовательных элементов. Одним из таких алгоритмов является **сортировка слиянием**, основанная на рекурсии.

Сортировка слиянием сортирует массив `array[a...b]` следующим образом:

1. Если `a = b`, ничего не делать, потому что подмассив уже отсортирован.
2. Вычислить положение среднего элемента: `k = b (a + b) / 2`.
3. Рекурсивно отсортировать подмассив `array[a...k]`.
4. Рекурсивно отсортировать подмассив `array[k + 1...b]`.
5. *Слить* отсортированный подмассив `array[a...k]` и `array[k + 1...b]` в отсортированный массив `array[a...b]`.

Сортировка слиянием - эффективный алгоритм, поскольку он уменьшает размер подмассива на каждом шаге. Рекурсия состоит из уровней O(log n), и обработка каждого уровня занимает O(n). Слияние массивов `array[a...k]` и `array[k + 1...b]` возможно в линейном времени, потому что они уже отсортированы.

<img src="https://rawgit.com/maxtereshko/competetive-handbook-ru/master/img/s7.PNG">

Массив будет разделен на два подмассива:

<img src="https://rawgit.com/maxtereshko/competetive-handbook-ru/master/img/s8.PNG">

Затем подмассивы будут отсортированы рекурсивно следующим образом:

<img src="https://rawgit.com/maxtereshko/competetive-handbook-ru/master/img/s9.PNG">

Наконец, алгоритм объединяет отсортированные подмассивы и создает окончательный
отсортированный массив:

<img src="https://rawgit.com/maxtereshko/competetive-handbook-ru/master/img/s10.PNG">

## Сортировка в C++

Почти никогда не рекомендуется использовать самодельный алгоритм сортировки в конкурсах потому, что в языках программирования уже есть хорошие реализации. Например, стандартная библиотека C++ содержит функцию сотрировки, которая может быть легко использована для сортировки массивов и других структур данных.

Есть много преимуществ в использовании библиотечной функции. Во-первых, это экономит время, потому что нет необходимости заново изобретать велосипед. Во-вторых, реализация библиотеки, безусловно, правильна и эффективна: не всегда самописная функция сортировки оказывается лучше.

В этом разделе мы увидим, как использовать функцию сортировки C++. Следующий код сортирует вектор в порядке возрастания:

```cpp
vector<int> v = {4, 2, 5, 3, 5, 8, 3};
sort(v.begin(), v.end());
```

После сортировки содержимое вектора будет `[2, 3, 3, 4, 5, 5, 8]`. По умолчанию сортировка происходит в порядке возрастания, но возможен обратный порядок:

```cpp
sort(v.rbegin(), v.rend());
```

Обычный массив можно отсортировать следующим образом:

```cpp
int n = 7; // Размер массива
int a[] = {4, 2, 5, 3, 5, 8, 3};
sort(a, a + n);
```

Следующий код сортирует строку s:

```cpp
string s = "monkey";
sort(s.begin(), s.end());
```

Сортировка строки означает, что символы строки выстроятся по алфавиту. Например, строка «monkey» становится «ekmnoy».

### Операторы сравнения

Функция `sort` требует **оператор сравнения**, определеный для типа данных элементов, подлежащих сортировке. При сортировке этот оператор будет использоваться всякий раз, когда необходимо выяснить порядок двух элементов.

Большинство типов данных C++ имеют встроенный оператор сравнения, и элементы этих типов могут быть отсортированы автоматически. Например, числа сортируются в соответствии с их значениями, а строки сортируются в алфавитном порядке.

Пары (пара) сортируются в первую очередь в соответствии с их первыми элементами (сначала). Однако, если первые элементы двух пар равны, они сортируются в соответствии со своими вторыми элементами:

```cpp
vector<pair<int, int>> v;
v.push_back({1, 5});
v.push_back({2, 3});
v.push_back({1, 2});
sort(v.begin(), v.end());
```

После этого порядок пар равен (1, 2), (1, 5) и (2, 3).

Аналогичным образом в первую очередь пары сортируются по первому элементу, во вторую, вторым элементом и т.д.:

```cpp
vector<tuple<int, int, int>> v;
v.push_back({2, 1, 4});
v.push_back({1, 5, 3});
v.push_back({2, 1, 3});
sort(v.begin(), v.end());
```

После этого порядок пар равен (1, 5, 3), (2, 1, 3) и (2, 1, 4).

### Пользовательские структуры

Пользовательские структуры не имеют оператора сравнения автоматически. Оператор должен быть определен внутри структуры как оператор функции `<`, параметр которого является другим элементом того же типа. Оператор должен возвращать значение true, если элемент меньше параметра, а false - в противном случае.

Например, следующая структура P содержит координаты x и y точки. Оператор сравнения определен так, что точки сортируются в первую очередь по координате x и, во вторую, по координате y.

```cpp
struct P {
  int x, y;
  bool operator<(const P &p) {
    if (x != p.x) return x < p.x;
    else return y < p.y;
  }
};
```

### Функция сравнения

Также можно предоставить внешнюю функцию сравнения функции сортировки в качестве функции обратного вызова. Например, следующая функция сравнения comp сортирует строки в первую очередь по длине, а во вторую по алфавиту:

```cpp
bool comp(string a, string b) {
  if (a.size() != b.size()) return a.size() < b.size();
  return a < b;
}
```

(можно еще так)

```cpp
bool comp(int a, int b) {
  if (a > b)
  return a > b;
}
```

Теперь вектор строк можно отсортировать следующим образом:

```cpp
sort(v.begin(), v.end(), comp);
```

## Двоичный поиск

Общий метод поиска элемента в массиве - это использовать цикл for, который выполняет итерацию через элементы массива. Например, следующий код ищет элемент x в массиве:

```cpp
for (int i = 0; i < n; i++) {
  if (array[i] == x) {
  // x ищется по индексу i
}
```

Временная сложность такого подхода является O(n), потому что в самом худшем случае, необходимо проверить все элементы массива. Если порядок элементов произволен, это также наилучший возможный подход, поскольку нет дополнительной информации, доступной там, где в массиве мы должны искать элемент x.

Однако, если массив отсортирован, ситуация другая. В этом случае можно выполнить поиск намного быстрее, потому что порядок элементов в массиве ведет поиск. Следующий алгоритм бинарного поиска эффективно ищет элемент в отсортированном массиве за время O(log n).

### Способ 1

Обычный способ реализации двоичного поиска похож на поиск слова в словаре. Поиск поддерживает активную область в массиве, которая изначально содержит все элементы массива. Затем выполняется ряд шагов, каждый из которых уменьшает размер области.

На каждом шаге поиск проверяет средний элемент активной области. Если средний элемент является целевым элементом, поиск завершается. В противном случае поиск рекурсивно продолжается в левую или правую половину области, в зависимости от значения среднего элемента.

Вышеупомянутая идея может быть реализована следующим образом:

```cpp
int a = 0, b = n-1;
while (a <= b) {
  int k = (a+b)/2;
  if (array[k] == x) {
  // x ищется по индексу k
  }
  if (array[k] > x) b = k-1;
  else a = k+1;
}
```

В этой реализации активной областью является a...b, и первоначально областью 0...n - 1. Алгоритм уменьшает размер области на каждом шаге, поэтому временная сложность O(log n).

### Способ 2

Альтернативный метод реализации двоичного поиска основан на эффективном способе итерации элементов массива. Идея состоит в том, чтобы делать прыжки и замедлять скорость, когда мы приближаемся к целевому элементу.

Поиск проходит через массив слева направо, а начальная длина перехода - n / 2. На каждом шаге длина скачка будет уменьшена наполовину: сначала n / 4, затем n / 8, n / 16 и т. д., пока, наконец, длина не будет равна 1. После прыжков найден либо целевой элемент, либо мы знаем, что его нет в массиве.

Следующий код реализует вышеупомянутую идею:

```cpp
int k = 0;
for (int b = n/2; b >= 1; b /= 2) {
  while (k+b < n && array[k+b] <= x) k += b;
}
if (array[k] == x) {
  // x ищется по индексу k
```

Во время поиска переменная b содержит текущую длину перехода. Временная сложность алгоритма - O(log n), поскольку код в цикле while выполняется не более двух раз для каждой длины перехода.

## Функции C++

Стандартная библиотека C++ содержит следующие функции, основанные на двоичном поиске и работающие в логарифмическом времени:

* lower_bound возвращает указатель на первый элемент массива, значение которого не меньше x.
* upper_bound возвращает указатель на первый элемент массива, значение которого больше x.
* equal_range возвращает оба указателя.

Функции предполагают, что массив отсортирован. Если такого элемента нет, указатель указывает на элемент после последнего элемента массива. Например, следующий код узнает, содержит ли массив элемент со значением x:

```cpp
auto k = lower_bound(array,array+n,x)-array;
if (k < n && array[k] == x) {
  // x ищется по индексу k
}

```

Затем следующий код подсчитывает количество элементов, значение которых равно x:

```cpp
auto a = lower_bound(array, array + n, x);
auto b = upper_bound(array, array + n, x);
cout << b - a << "\n";
```

Используя equal_range, код становится короче:

```cpp
auto r = equal_range(array, array + n, x);
cout << r.second-r.first << "\n";
```



















