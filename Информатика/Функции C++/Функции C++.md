## Naming
`l`, `ll` в начале или конце &int; перевод из/в long int / double

## Различные функции
#### Работа с числами
`std::llround ` 
#### Работа с массивом
`std::sort`
`std::count`
[[partial_sum|std::partial_sum]]
`std::accumulate`
`std::min`
`std::max`
#### Бинарный поиск в массиве
`std::upper_bound`
`std::lower_bound`
`std::binary_search`
#### Функции builtin
`std::__builtin_clz`
`std::__builtin_ctz`
`std::__builtin_popcount` 
#### Itertools C++
`std::nex(t)_permutatuion`

#### Приведение типов
`std::to_string` ?

```c++
#include<iostream>
#include<vector>
#include<list>
#include<math.h>
#define ll long long
using namespace std;

ll vars(ll bigger, ll curr, ll ma, ll en){
    //cout << bigger <<" " <<curr <<"\n ";
    if(ma < bigger){
        return 0;
    }
    if(curr == en){
        if(bigger< ma){
            cout << "found!" <<bigger <<"\n";
            return ma - bigger + 1;
        }
        else{
            return 0;
        }
    }
    ll sum = 0;
    for(int j = bigger; j <= ma; j++){
        sum+=vars(std::pow(j, curr), curr+1, ma, en);
    }
    return sum;
}
int main()
{
    ll n, m, sum;
    cin >> n >> m;
    sum = 0;
    for(int i= 1; i <= m; i++){
        sum += vars(i, 1, m, n+1);
    }
    cout << sum;
}


```