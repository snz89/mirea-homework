## Домашняя работа 1
### Задание 1.1 «Имя»
```C++
#include <iostream>
#include <cstdlib>
using namespace std;

int main()
{
  setlocate(LC_ALL, "Russian");
  cout << "Имя" << endl;
  system("pause");
  return 0;
}
```

### Задание 1.2 «Арифметика»
```C++
#include <iostream>
using namespace std;

int main()
{
  setlocate(LC_ALL, "Russian");
  float a, b;
  cout << "Введите A" << endl;
  cin >> a;
  cout << "Введите B" << endl;
  cin >> b;
  cout << "Сумма: " << a + b << endl;
  cout << "Вычитание: " << a - b << endl;
  cout << "Произведение: " << a * b << endl;
  if (b == 0)
  {
    cout << "На 0 делить нельзя" << endl;
    return 0;
  }
  else
  {
    cout << "Деление = " << a / b << endl;
  }
  return 0;
}
```

### Задание 1.3 «Уравнение»
```C++
#include <iostream>
using namespace std;

int main()
{
    setlocale(LC_ALL, "Russian");
    float b, c;
    cout << "Введите b" << endl;
    cin >> b;
    cout << "Введите c" << endl;
    cin >> c;
    if (b == 0 and c == 0)
    {
        cout << "X может быть любым действительным числом" << endl;
        return 0;
    }
    if (b == 0 and c != 0)
    {
        cout << "Решений нет :(" << endl;
        return 0;
    }
    else
    {
        float x = (-c) / b;
        cout << "x = " << x;
        return 0;
    }
    return 0;
}
```

### Задание 1.4 «Еще уравнение»
```C++
#include <iostream>
using namespace std;

int main()
{
    setlocale(LC_ALL, "Russian");
    float a, b, c;
    cout << "Введите A" << endl;
    cin >> a;
    cout << "Введите B" << endl;
    cin >> b;
    cout << "Введите C" << endl;
    cin >> c;
    float x;
    if (a == 0)
    {
        if (b == 0 and c == 0)
        {
            cout << "X может быть любым действительным числом" << endl;
            return 0;
        }
        if (b == 0 and c != 0)
        {
            cout << "Решений нет :(" << endl;
            return 0;
        }
        else
        {
            float x = (-c) / b;
            cout << "x = " << x;
            return 0;
        }
        return 0;
    }
    else
    {
        float d = b * b - 4 * a * c;
        if (d > 0)
        {
            float d0 = sqrt(d);
            float x1 = (-b + d0) / (2 * a);
            float x2 = (-b - d0) / (2 * a);
            cout << "x1 = " << x1 << endl;
            cout << "x2 = " << x2 << endl;
            r/eturn 0;
        }
        if (d == 0)
        {
            float x = (-b) / (2 * a);
            cout << "x = " << x << endl;
            return 0;
        }
        else
        {
            cout << "Решений нет" << endl;
            return 0;
        }

    }
    return 0;
}
```

### Задание 1.5 «Лампа со шторой»
```C++
#include <iostream>
using namespace std;

int main()
{
    setlocale(LC_ALL, "Russian");
    bool day, shtori, lamp;
    cout << "На улице день?" << endl;
    cin >> day;
    cout << "Шторы открыты?" << endl;
    cin >> shtori;
    cout << "Лампа включена?" << endl;
    cin >> lamp;
    if (lamp == 1)
    {
        cout << "Светло" << endl;
        return 0;
    }
    else
    {
        if (shtori == 0)
        {
            cout << "Темно" << endl;
            return 0;
        }
        else
        {
            if (day == 1)
            {
                cout << "Светло" << endl;
                return 0;
            }
            else
            {
                cout << "Темно" << endl;
                return 0;
            }
        }
    }
    return 0;
}
```
