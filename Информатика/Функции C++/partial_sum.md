## Описание
*partial_sum* делает префиксную сумму по массиву и записывает её в другой. Для записи необходимо указать итератор на начало второго массива (вектора), куда запишется сумма.

Находится в файле numeric.
## Синтаксис
`std::partial_sum(__first, __last, __result[, op__])`

* _res_ - итератор на начало второго массива.
* _op_ - функция для операции над числами.
* Функция возвращает итератор на конец массива для записи.

Для работы должен быть создан массив \_\_result ненулевой длины.

`Функция std::partial_sum для массивов`
```cpp
template<typename T> // Любой тип
T * // Возвращает указатель на массив
std::partial_sum<T *, T *>
(
	T *__first, // Указатель на начало массива
	T *__last, // Указатель на конец массива
	T *__result // Заполняемый массив
)
```

`Функция std::partial_sum для векторов`
```cpp
template<typename T> // Любой тип вектора
std::vector<T> // Возвращает вектор
std::partial_sum<std::vector<T>::iterator, std::vector<T>>  (что это)
(
	std::vector<T>::iterator __first, // Итератор,указывающий на начало массива
	std::vector<T>::iterator __last, // Итератор, указывающий на конец
	std::vector<T>::iterator __result // Массив с результатом
)
```
## Примеры
#### Пример 1
`сумма элементов из vec передаётся в res`
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> vec = {5, 10, 15};
    vector<int> res(vec.size());
  
    // Определение границ массива
    auto first = vec.begin();
    auto last = vec.end();
  
    // Использование partial_sum для префиксной суммы элементов
    partial_sum(first, last, res.begin());

    for (int val : res)
        cout << val << " ";
    return 0;
}
```
**вывод:**
`5 15 30`
#### Пример 2
`Благодаря функции op в массив записывается не сумма, а произведение элементов`
```c++
// with custom function
#include <bits/stdc++.h>
using namespace std;

// Своя функция для произведения элементов
int op(int a, int b) {
    return a * b;
}

int main() {
    vector<int> vec = {5, 10, 15};
    vector<int> result(vec.size());
  
    // Определение границ массива
    auto first = vec.begin();
    auto last = vec.end();
  
    // Использование partial_sum с пользовательской функцией
    partial_sum(first, last, result.begin(), op);

    for (int val : result)
        cout << val << " ";
    return 0;
}```
**Вывод:**
`5 50 750`

## Асимптотика
O(n)