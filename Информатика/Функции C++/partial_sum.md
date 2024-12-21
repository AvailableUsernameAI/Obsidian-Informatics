## Описание
*partial_sum* делает префиксную сумму по массиву и записывает её в другой. Для записи необходимо указать итератор на начало второго массива (вектора), куда запишется сумма.
## Синтаксис
`std::partial_sum(__first, last, res[, op__])`

```cpp
std::vector<int> 
std::partial_sum<std::vector<int>::iterator, std::vector<int>>
(
	std::vector<int>::iterator __first, // Итератор — начало массива
	std::vector<int>::iterator __last, // Итератор, указывающий на конец
	std::vector<int> __result
)
```

* _res_ - итератор на начало второго массива.
* _op_ - функция для операции над числами.
* Функция возвращает итератор на конец массива для записи.
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