## Спиннеры
```C++
#include <iostream>
using namespace std;


int main()
{
    setlocale(LC_ALL, "Russian");

    int a, b, c, n = 0, price;

    // Ввод значений
    cout << "Введите A: ";
    cin >> a;
    cout << "Введите B: ";
    cin >> b;
    cout << "Введите c: ";
    cin >> c;

    price = a + b * n;

    // Проверка на условие
    if (a > c) {
        cout << "A должен быть <= C";
        return 0;
    }

    // Расчет лопастей
    while (price < c) {
        n++;
        price = a + b * n;
    }

    cout << n - 1;
}
```

## Снова спиннеры
```C++
#include <iostream>
using namespace std;


int main()
{
    setlocale(LC_ALL, "Russian");

    int m, spinner_3, spinner_4;
    cout << "Введите m: ";
    cin >> m;

    spinner_4 = m % 3;
    spinner_3 = (m - 4 * spinner_4) / 3;
    
    if (spinner_3 < 0) {
        cout << "0" << endl;
        cout << "0" << endl;
    }

    else {
        cout << "Спиннеры с 3 лопастями: " << spinner_3 << endl;
        cout << "Спиннеры с 4 лопастями: " << spinner_4 << endl;
    }

    return 0;
}
```
