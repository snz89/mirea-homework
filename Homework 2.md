## Домашняя работа 2
### Задание 2.1 «Конус»
```C++
#include <iostream>
using namespace std;

int main()
{
    setlocale(LC_ALL, "Russian");
    float h, R, r, l;
    double pi = 3.141592653589793;
    cout << "Введите высоту конуса" << endl;
    cin >> h;
    cout << "Введите большой радиус конуса" << endl;
    cin >> R;
    cout << "Введите маленький радиус конуса" << endl;
    cin >> r;
    l = pow(pow(h, 2) + pow(R - r, 2), 0.5);
    cout << "V = " << (1.0 / 3.0) * pi * h * (pow(R, 2) + R * r + pow(r, 2)) << endl;
    cout << "S = " << pi * (pow(R, 2) + (R + r) * l + pow(r, 2)) << endl;
    return 0;
}
```

### Задание 2.2 «Разветвление»
```C++
#include <iostream>
#include <cstdlib>
#include <cmath>
using namespace std;

int main()
{
    setlocale(LC_ALL, "Russian");
    double a, x;
    cout << "Введите число a" << endl;
    cin >> a;
    cout << "Введите число x" << endl;
    cin >> x;
    if (abs(x) < 1)
    {
        if (a ==0 or log(abs(x)) == 0)
        {
           cout << "W = 0" << endl; 
        }
        else
        {
            cout << "W = " << a*log(abs(x)) << endl;
        }
        return 0;
    }
    else
    {
        if (a - pow(x, 2) >= 0)
        {
            cout << "W = " << sqrt(a - pow(x, 2)) << endl;
            return 0;
        }
        else
        {
            cout << "Нельзя извлечь корень" << endl;
            return 0;
        }
    }
    return 0;
}
```

### Задание 2.3 «Функция»
```C++
#include <iostream>
#include <cstdlib>
using namespace std;

int main()
{
    setlocale(LC_ALL, "Russian");
    float x, y, b;
    cout << "Введите число x" << endl;
    cin >> x;
    cout << "Введите число y" << endl;
    cin >> y;
    cout << "Введите число b" << endl;
    cin >> b;
    if (b - y > 0)
    {
        if (b - x >= 0)
        {
            cout << "Z = " << log(b - y) * sqrt(b - x) << endl;
            return 0;
        }
        else
        {
            cout << "Нельзя извлечь корень" << endl;
            return 0;
        }
        return 0;
    }
    else
    {
        if (b - x >= 0)
        {
            cout << "Нельзя вычислить логарифм" << endl;
            return 0;
        }
        else
        {
            cout << "Нельзя вычислить логарифм и извлечь корень" << endl;
            return 0;
        }
        return 0;
    }
    return 0;
}
```

### Задание 2.4 «Порядок»
```C++
#include <iostream>
using namespace std;

int main()
{
    setlocale(LC_ALL, "Russian");
    int n, k;
    cout << "Введите число N" << endl;
    cin >> n;
    k = n;
    cout << n << endl;
    while (k <= n + 8)
    {
        k = k + 1;
        cout << k << endl;
    }
    return 0;
}
```

### Задание 2.5 «Порядок»
```C++
#include <iostream>
using namespace std;

int main()
{
    setlocale(LC_ALL, "Russian");
    for (float x = -4; x < 4; x+= 0.5)
    {
        if (x - 1 != 0)
        {
            cout << "При x = " << x << " --> y = " << (pow(x, 2) - 2 * x + 2) / (x - 1) << endl;
        }
        else
        {
            cout << "При x = " << x << " на 0 делить нельзя" << endl;
        }
    }
}
```
