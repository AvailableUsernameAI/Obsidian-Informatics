## Описание
*partial_sum* делает префиксную сумму по массиву и записывает её в другой. Для записи необходимо указать итератор на начало второго массива (вектора), куда запишется сумма.
## Синтаксис
`std::partial_sum (__first, last, res, op__);`
first, last - *см. [как задавать функции]*
res - итератор на начало второго массива.
op - функция для операции над числами. (*подробнее в примерах*).
partial_sum возвращает итератор на конец массива для записи.
## Примеры
`сумма элементов из vec передаётся в res`
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> vec = {5, 10, 15};
    vector<int> res(vec.size());
  
    // Defining range as the whole array
    auto first = vec.begin();
    auto last = vec.end();
  
    // Use partial_sum to calculate the cumulative sum of elements
    partial_sum(first, last, res.begin());

    for (int val : res)
        cout << val << " ";
    return 0;
}
```
**вывод**
`5 15 30`
