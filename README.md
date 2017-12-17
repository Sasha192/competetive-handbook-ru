# competetive-handbook-ru

## Введение

Цель этой книги - ввести вас в олимпиадное программирование. Предполагается, что вы уже знакомы с основами программирования, однако опыт по олимпиадному программированию не требуется.

Данная книга предназначена для студентов, которые хотят изучить алгоритмы программирования и, возможно, принять участие в International Olympiad in Informatics (IOI) или в International Collegiate Programming Contest (ICPC). Соответственно, книга также подойдет для любого другого человека, заинтересованного в программировании.

Понадобится много времени, чтобы стать профессионалом в олимпиадном программировании, но это отличная возможность многому научиться. Вы можете быть уверены, что вы получите всеобщее понимание об алготитмах, если вы проведете время за чтением книги, решая задачи и учавтвуя в конкурсах.

Книга находится в садии непрерывного развития. Вы всегда можете отправить свой отзыв о ней на *ahslaaks@cs.helsinki.fi*.

# Глава 1
## Вступление

Олимпиадное программирование объединяет две темы: (1) **дизайн алгоритмов** и (2) **реализация алгоритмов**.

**Дизайн алгоритмов** состоит из решения задач и математического мышления.Необходимы навыки для анализа проблем и их решения. Алгоритм решения проблемы должен быть как правильным, так и эффективным, и ядро проблемы часто связано с изобретением эффективного алгоритма.

Теоретические знания алгоритмов важны для олимпиадных программистов. Как правило, решение проблемы представляет собой комбинацию хорошо известных методов и новых идей. Методы, которые появляются в олимпиадном программировании, также составляют основу для научных исследований алгоритмов.

Для **реализации алгоритмов** требуются хорошие навыки программирования. В олимпиадном программировании решения оцениваются путем тестирования реализованного алгоритма с использованием набора тестовых примеров. Таким образом, недостаточно, чтобы идея алгоритма была правильной, реализация также должна быть правильной.

Хороший стиль написания кода в конкурсах прост и краток. Программы должны быть написаны быстро, потому что времени мало. В отличие от традиционной разработки программного обеспечения, программы коротки (обычно не более нескольких сотен строк), и их не нужно поддерживать после конкурса.

### Языки программирования

На данный момент самые популярные языки программирования, используемые в конкурсах, C++, Python и Java. Например, в Google Code Jam 2017, среди лучших 3000 участников, 79% использовали C++, 16% использовали Python и 8% использовали Java. Некоторые участники также использовали другие языки.

Многие считают, что C++ - лучший выбор для олимпиадного программиста, C++ почти всегда доступен в конкурсных системах. Преимуществом использования C++ является то, что это очень эффективный язык, и его стандартная библиотека содержит большой набор структурданных и алгоритмов.

С другой стороны, хорошо владеть несколькими языками и понимать их сильные стороны. Например, если нужно использовать большие целые числа, то Python может быть хорошим выбором, поскольку он содержит встроенные операции для вычисления больших целых чисел. Тем не менее, большинство проблем в конкурсах программирования установлены так, что использование конкретного языка программирования не является несправедливым преимуществом.

Все примеры программ в этой книге написаны на C++, а стандартные
Библиотечные структуры данных и алгоритмы часто используются.

Программы соответствуют стандарту C++11, который можно использовать в большинстве конкурсов в настоящее время. Если ты не умеешь программировать на C ++, то сейчас самое подходящее время для начала обучения.

### Шаблон кода на C++

Типичный шаблон кода C++ выглядит следующим образом:

```cpp
#include <bits/stdc++.h>

using namespace std;

int main() {
  // код здесь
}
```

Строка **#include** в начале кода является функцией компилятора g++, что позволяет нам подключить всю стандартную библиотеку. Таким образом, нет необходимости отдельно включать библиотеки, такие как iostream, vector и algorithm.

Строка **using** объявляет, что классы и функции стандартной библиотеки могут быть использованы непосредственно в коде. Без использования строки нам пришлось бы писать, например, std::cout, но теперь достаточно написать cout.

Код можно скомпилировать, используя следующую команду:

```
g++ -std=c++11 -O2 -Wall test.cpp -o test
```

Эта команда производит бинарный файл test из исходного кода test.cpp. Компилятор следует стандарту C++11 (-std=c++11), оптимизирует код (-O2) и отображает предупреждения о возможных ошибках (-Wall).

## Ввод и вывод

В большинстве конкурсов используются стандартные потоки для чтения ввода и записи вывода.

В C++ стандартными потоками являются **cin** для ввода и **cout** для вывода. Кроме того, можно использовать функции языка C **scanf** и **printf**.

Ввод для программы обычно состоит из чисел и строк, разделенных пробелами и символами новой строки. Они могут быть прочитаны из потока **cin** следующим образом:

```cpp
int a, b;
string x;
cin >> a >> b >> x;
```

Такой код всегда работает, предполагая, что между каждым элементом во входном файле имеется по крайней мере один пробел или новая линия. Например, приведенный выше код может считывать оба следующих входа:

```
123 456 monkey
```

```
123   456
monkey
```

Поток **cout** используется для вывода следующим образом:

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

Обратите внимание, что новая строка **«\n»** работает быстрее, чем **endl**, потому что **endl** всегда вызывает операцию сброса.

Функции языка C **scanf** и **printf** являются альтернативой стандартным потокам C++. Они, как правило, немного быстрее, но сложнее в использовании. Следующий код считывает из ввода два целых числа:

```c
int a, b;
scanf("%d %d", &a, &b);
```
А этот код выводит два целых числа

```c
int a = 123, b = 456;
printf("%d %d\n", a, b);
```

Иногда программа должна cчитать целую строку из ввода, возможно, содержащую пробелы. Это можно выполнить с помощью функции **getline**:

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

В некоторых системах проверки конкурсов для ввода и вывода используются файлы. Легким решением для этого является запись кода, как обычно, с использованием стандартных потоков, но добавьте следующие строки в начало кода:

```cpp
freopen("input.txt", "r", stdin);
freopen("output.txt", "w", stdout);
```

После этого программа считывает ввод из файла *«input.txt»* и записывает вывод в файл *«output.txt»*.

## Работа с числами
### Целые числа (integers)

Наиболее используемым целым типом в конкурентном программировании является *int*, который представляет собой 32-разрядный тип с диапазоном значений −2<sup>31</sup>...2<sup>31</sup>−1 или -2 * 10<sup>-9</sup>...2 * 10<sup>9</sup>
Если типа *int* недостаточно, можно использовать 64-битный тип *long long*. Он имеет диапазон значений −2<sup>63</sup>...2<sup>63</sup>−1 или -2 * 10<sup>-18</sup>...2 * 10<sup>18</sup>.

Следующий код определяет переменную *long long*:

```cpp
long long x = 123456789123456789LL;
```

Суффикс LL означает, что тип числа *long long*

Общей ошибкой при использовании типа *long long* является то, что тип *int* все еще используется где-то в коде. Например, следующий код содержит тонкую ошибку:

```cpp
int a = 123456789;
long long b = a*a;
cout << b << "\n"; // -1757895751
```

Несмотря на то, что переменная `b` имеет тип `long long`, оба числа в выражении `a * a` имеют тип `int`, а результат также имеет тип `int`. Из-за этого переменная *b* будет содержать неправильный результат. Проблема может быть решена путем изменения типа `a` до `long long` или путем изменения выражения `(long long) a * a`.

Обычно конкурсные задачи устанавливаются так, что достаточно типа `long long`. Тем не менее, хорошо знать, что компилятор g++ также предоставляет 128-битный тип `__int128_t` с диапазоном значений −2<sup>127</sup>...2<sup>127</sup>−1 или -2 * 10<sup>-38</sup>...2 * 10<sup>38</sup>. Однако этот тип недоступен во всех конкурсных системах проверки.

### Модульная арифметика

/// Позже

### Числа с плавающей запятой

Обычными типами с плавающей запятой в конкурентном программировании являются 64-битный `double` и, как расширение в компиляторе g++, 80-битный `long double`. В большинстве случаев `double` достаточно, но `long double` более точный.

Требуемая точность ответа обычно указывается в постановке задачи. Легкий способ вывода ответа - использовать функцию `printf` и указать число десятичных знаков в строке форматирования. Например, следующий код печатает значение `x` с 9 знаками после запятой:

```cpp
printf("%.9f\n", x);
```

Трудность при использовании чисел с плавающей запятой состоит в том, что некоторые числа не могут быть точно представлены как числа с плавающей запятой, и будут ошибки округления. Например, результат следующего кода удивляет:

```cpp
double x = 0.3*3+0.1;
printf("%.20f\n", x); // 0.99999999999999988898
```

Из-за ошибки округления значение x немного меньше 1, в то время как правильное значение - 1.

Это рискованно сравнивать числа с плавающей запятой оператором ==, потому что возможно, что значения должны быть равны, но они не равны из-за ошибок точности. Лучшим способом сравнения чисел с плавающей запятой является предположить, что два числа равны, если разница между ними меньше ε, где ε - меньшее число.

На практике числа можно сравнить следующим образом (ε = 10<sup>-9</sup>)

```cpp
if (abs(a-b) < 1e-9) {
// a и b равны
}
```

Обратите внимание, что, хотя числа с плавающей запятой неточны, целые числа до определенного предела могут быть представлены точно. Например, используя `double`, можно точно представлять все целые числа, абсолютное значение которых не более 2<sup>53</sup>.

## Сокращение кода

Короткий код идеален в конкурентном программировании, потому что программы должны быть написаны как можно быстрее. Из-за этого конкурентные программисты часто определяют более короткие имена для типов данных и других частей кода.

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

На каждом конкурсе ICPC команды имеют пять часов времени, чтобы решить около десяти задач. Решение проблемы принимается только в том случае, если оно эффективно решает все тестовые примеры. Во время соревнований участники могут просматривать результаты других команд, но за последний час табло замерзает, и результаты последних представлений невозможны.

Темы, которые могут появиться в ICPC, не так хорошо указаны, как те, что указаны в IOI. В любом случае ясно, что в ICPC требуется больше знаний, особенно больше математических навыков.

### Онлайн конкурсы

Есть много бесплатных конкурсов, которые доступны для всех. На данный момент самым активным сайтом с конкурсами является *Codeforces*, который организует конкурсы еженедельно. В Codeforces участники делятся на два подразделения: новички участвуют в *Div2* и более опытные программисты в *Div1*. Другие сайты - AtCoder, CS Academy, HackerRank и Topcoder.

Некоторые компании организуют онлайн-конкурсы с финалами на месте. Примерами таких конкурсов являются *Facebook Hacker Cup*, *Google Code Jam* и *Yandex.Algorithm*. Конечно, компании также используют эти конкурсы для рекрутинга: хорошо выступать в конкурсе - это хороший способ доказать свои навыки.



