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

#### Шаблон кода на C++

Типичный шаблон кода C++ выглядит следующим образом:

```cpp
#include <bits/stdc++.h>

using namespace std;

int main() {
  // решение здесь
}
```

Строка **#include** в начале кода является функцией компилятора g++, что позволяет нам подключить всю стандартную библиотеку. Таким образом, нет необходимости отдельно включать библиотеки, такие как iostream, vector и algorithm.

Строка **using** объявляет, что классы и функции стандартной библиотеки могут быть использованы непосредственно в коде. Без использования строки нам пришлось бы писать, например, std::cout, но теперь достаточно написать cout.

Код можно скомпилировать, используя следующую команду:

```
g++ -std=c++11 -O2 -Wall test.cpp -o test
```

Эта команда производит двоичный текстовый файл из исходного кода test.cpp. Компилятор следует стандарту C++11 (-std=c++11), оптимизирует код (-O2) и отображает предупреждения о возможных ошибках (-Wall).




















