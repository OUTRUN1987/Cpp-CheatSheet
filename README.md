## 1. Базовая структура

```cpp
#include <iostream>
using namespace std;

int main() {
    // Код
    return 0;
}
```

---

## 2. Переменные и типы данных

| Тип         | Размер в байтах       | Диапазон/описание     |
|-------------|-----------------------|-----------------------|
| `void`      | 0                     | пустота               |
| `int`       | 4                     | -2³¹ до 2³¹-1         |
| `char`      | 1                     | -128 до 127           |
| `float`     | 4                     | ~7 десятичных знаков  |
| `double`    | 8                     | ~15 десятичных знаков |
| `bool`      | 1                     | true/false            |
| `string`    | -                     | список `char`'ов      |
| `*short`    | 2                     | -32768 до 32767       |
| `*long`     | 4/8                   | Больший диапазон      |
| `*unsigned` | Также как и основного | Только положительные  |

`*` - модификаторы. Могут писаться перед переменной. Пример: `short int`

```cpp
int a; // объявление
a = 10; // присвоение
cout << a; // использование

short unsigned int b = 20; // объявление с присвоением
```

---

## 3. Операторы

- Арифметические: `+ - * / % ++ --`
% получает остаток от деления
++ и -- увеличивает или уменьшает переменную на 1
- Сравнение: `== != > < >= <=`
== равно
!= не равно
<= или >= меньше/больше или равно
- Логические: `&& || !`
&& И
|| Или
! Не
- Побитовые: `& | ^ ~ << >>`

---

## 4. Обработка командной строки

```cpp
int age;
cout << "Enter" << " age: "; // базовый вывод
cin >> age;  // базовый ввод

string name;
getline(cin, name); // ввод строки

cout << "\n"; // перенос строки, можно заменить "\n" на endl
```

---

## 5. Обработка файла

```cpp
#include <fstream> // импорт библиотеки

// Запись
ofstream outFile("data.txt"); // открытие файла
outFile << "Hello World" << endl; // запись в файл
outFile.close(); // закрытие файла (сохранение)

// Чтение
ifstream inFile("data.txt"); // открытие файла
string line;
while(getline(inFile, line)) { // запуск цикла "Пока есть строки"
    cout << line << endl; // вывод строки с переносом
}
inFile.close(); // закрытие файла
```

---

## 6. Математические операции

```cpp
#include <cmath> // импорт библиотеки

sqrt(x); // квадратный корень x
pow(x,y); // возведение в степень y числа x
abs(x); // модуль (абсолютное значение)
ceil(x); // округление вверх  ceil(1.1) = 2  В переводе - "Потолок"
floor(x); // округление вниз  ceil(1.9) = 1  В переводе - "Пол"
round(x); // округление как в математике
sin(x); cos(x); tan(x); // синус, косинус, тангенс. В радианах (360 градусов = 6.28 = 2 * PI)
log(x); exp(x); // натуральный логарифм, экспонента
```

---

## 7. IF-Else, Switch

```cpp
// If-Else
// if - проверяет условие
// else - выполняется, если условие в if неверно
if (condition) {
    // Код
}
else if (condition) {
    // Код
}
else {
    // Код
}

// Switch
// Быстрый способ сделать проверку при разных значениях. К примеру когда пользователь выбирает номер задачи
// var - переменная, значение которой проверяется
// default выполняется если var не равна значениям из case
// ... - это код. Можно использовать переносы строк, но в конце должен быть break;
switch(var) {
    case 1: ... break;
    case 2: ... break;
    case 3: ... break;
    default: ...
}
```

## 8. Структуры данных

Нумерация начинается с нуля

- **Статичный Массив**
Длинна не меняется

```cpp
int arr[5] = {1,2,3,4,5};
arr[3] // получение четвёртого элемента, который равен числу 4
```

- **Vector** (Динамический массив)

```cpp
#include <vector> // импорт библиотеки
vector<int> vec = {1,2,3}; // создание массива с типом элементов int
vec.size(); // кол-во элементов

vec.clear(); // отчистка
vec.push_back(4); // добавить элемент в конец
vec.pop_back(); // убрать последний элемент
vec.insert(1, 103); // вставить на место с индеком 2 значение 103. Всё что после этого индекса сдвигается вправо
```

- **String**

```cpp
#include <string> // импорт библиотеки
string s = "Hello"; // создание и присвоение
s.length(); // длинна
```

---

## 9. Циклы

```cpp
// Цикл for, перебор.
// первый аргумент (int i = 0) выполняется до начала цикла
// второй аргумент (i < 5) - условие выхода их цикла. Проверяется в конце каждого прохода
// третий аргумент (i++) выполняется в конце прохода
for(int i = 0; i < 5; i++) { 
   // Код
}

// Цикл While
// Выполняется пока истино условие в скобках
while(условие) {
    // Код
}

// Цикл Do-While
// обычный while, но он сначала делает код, потом его проверяет
do {
    // Код
} while(условие);

// Для массивов, векторов, строк (C++11)
// <тип данных элемента> <переменная элемента> : <что перебирать>
for(int num : vec) {
    // Код
}
```

---

## 10. Функции

```cpp
<возвращаемые данные> <название функции>([аргументы]);
<возвращаемые данные> <название функции>([аргументы]) {
    // Код
}

аргумент: <тип данных> <название>

// Объявление (можно сразу присваивать, но тогда код функции должен быть написан раньше кода, где эта функция используется)
// функция должна вернуть тип int
// принимает два аргумента типа int
int add(int a, int b); 

// Присвоение 
int add(int a, int b) {
    return a + b;
}

// Параметры со стандартным значением
// если вызвать просто greet(), без аргументов, значение name автоматически поставится на "User"
void greet(string name = "User") {
    // Код
}

// Перегрузка
// функции могут иметь одно и то же название, но должны иметь разные входные типы данных. Обычно такое делают для разных типов чисел: int, double, float
void print(int x) {
    // Код
}
void print(string s) {
    // Код
}
```

---

## 11. Ссылки и Указатели

---

### Указатели (Pointers)

**Что это:** Переменная, хранящая адрес памяти другой переменной.

```cpp
int x = 10;
int* ptr = &x; // ptr хранит адрес x
```

**Особенности:**

1. Могут быть `nullptr` (нулевой указатель).
2. Можно менять адрес, на который указывают.
3. Требуют явного разыменования через `*`.
4. Используются для динамического выделения памяти (`new`, `delete`).

**Примеры:**

```cpp
int a = 5;
int* p = &a; // Получение адреса a
cout << *p; // 5 (доступ к значению через указатель)

*p = 20; // Изменение a через указатель
cout << a; // 20

// Динамическая память
int* arr = new int[10];
delete[] arr; // Обязательное освобождение!
```

### Ссылки (References)

**Что это:** Псевдоним для существующей переменной.

```cpp
int y = 30;
int& ref = y; // ref - другое имя для y
```

**Особенности:**

1. Должны быть инициализированы при объявлении.
2. Не могут быть перенаправлены на другую переменную.
3. Нет синтаксиса разыменования (работают как обычные переменные).
4. Безопаснее указателей (не могут быть null).

**Примеры:**

```cpp
int b = 7;
int& r = b; // Ссылка на b
r = 15; // Изменяет b
cout << b; // 15

// Использование в функциях
void increment(int& num) {
    num++;
}
increment(b); // b станет 16
```


### Ключевые различия

| **Критерий**         | **Указатели**                          | **Ссылки**                          |
|----------------------|----------------------------------------|--------------------------------------|
| Инициализация        | Могут быть `nullptr`                   | Обязательна при объявлении          |
| Перенаправление      | Можно менять адрес                     | Нельзя изменить после инициализации |
| Синтаксис            | `*` для разыменования, `->` для классов | Работают как обычные переменные     |
| Безопасность         | Риск утечек памяти и null-разыменования | Безопаснее                          |
| Передача в функции   | Модифицируемый адрес                   | Псевдоним для исходной переменной   |

---

### Когда что использовать?

- **Указатели**:
  - Динамические структуры данных (списки, деревья).
  - Опциональные параметры функций (может быть `nullptr`).
  - Низкоуровневое управление памятью.

- **Ссылки**:
  - Передача больших объектов в функции без копирования.
  - Возврат значений из функций через параметры.
  - Перегрузка операторов (например, `operator<<`).

---

## Const-ссылки и указатели

```cpp
// Немодифицируемая ссылка
const int& cref = x; 
// cref = 5; Ошибка!

// Указатель на константу
const int* cp = &x; 
// *cp = 5; Ошибка!

// Константный указатель
int* const pc = &x; 
// pc = nullptr; Ошибка!
```

**Совет:** Используйте ссылки, когда возможно, а указатели — только для низкоуровневых задач или при работе с динамической памятью.

---

## Заметки

1. Использовать `endl` или `\n` для вывода на новую строку
2. Переменные и функции должны быть объявлены до использования
3. В массивах порядок (индексация) начинается с нуля
