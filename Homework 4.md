## Домашняя работа 4
### Задача 4.1 «Файл»
```C++
#include <iostream>
#include <windows.h>
#include <fstream>
#include <string>
using namespace std;

int main()
{
	setlocale(LC_ALL, "Russian");

	int count = 0;
	double start = 1000; // Начальное число
	double step = 250; // Шаг
	ofstream file;
	file.open("test.txt");
	while (count < 10)
	{
		file << start << endl;
		start += step;
		count += 1;
	}

	ifstream file2; // Создание fstream для чтения данных из файла
	file2.open("test.txt");
	string line;
	double sum = 0;

	// Считывание чисел из файла
	for (int j = 0; j < 10; ++j)
	{
		if (!getline(file2, line)) // Проверка
		{
			cout << "Ошиба чтения строки " << j + 1 << "из файла" << endl;
			return 1;
		}

		double number = stod(line); // stod - преобразование string в double
		sum += number;
	}
	file2.close();
	cout << "Сумма чисел = " << sum << endl;
	return 0;
}
```

### Задача 4.2 «Знак числа»
```C++
#include <iostream>
#include <windows.h>
using namespace std;

int sign(double x)
{
	if (x > 0)
	{
		return 1;
	}
	if (x < 0)
	{
		return -1;
	}
	if (x == 0)
	{
		return 0;
	}
}


int main()
{
	setlocale(LC_ALL, "Russian");

	double x;
	cout << "Введите число: ";
	cin >> x;

	cout << "Знак числа: " << sign(x) << endl;
	return 0;
}
```

### Задача 4.3 «Геометрические фигуры»
```C++
#include <iostream>
#include <windows.h>
#include <cmath>
using namespace std;



double rectangle(double w, double h)
{
	return w * h;
}

double triangle(double a, double h2)
{
	return 0.5 * a * h2;
}

double circle(double r)
{
	return 3.1415926535 * pow(r, 2);
}

int main()
{
	setlocale(LC_ALL, "Russian");
	double w, h, a, h2, r;

	cout << "Введите ширину прямоугольника: ";
	cin >> w;
	cout << "Введите высоту прямоугольника: ";
	cin >> h;

	cout << "Введите основание треугольника: ";
	cin >> a;
	cout << "Введите высоту треугольника: ";
	cin >> h2;

	cout << "Введите радиус круга: ";
	cin >> r;

	cout << "Площадь прямоугольника = " << rectangle(w, h) << endl;
	cout << "Площадь треугольника = " << triangle(a, h2) << endl;
	cout << "Площадь круга = " << circle(r) << endl;

	return 0;
}
```

### Задача 4.4 «Былая слава»
```C++
#include <iostream>
#include <windows.h>
#include <string>
using namespace std;

int main()
{
	setlocale(LC_ALL, "Russian");

	string stars;
	string stars2;
	string line("------------------------------------------");
	for (int i = 0; i < 8; i++)
	{
		stars += "* ";
	}

	stars2 += stars;
	stars2 += "--------------------------";

	for (int j = 0; j < 3; j++)
	{
		cout << stars2 << endl;
		cout << stars << endl;
	}

	for (int j = 0; j < 4; j++)
	{
		cout << line << endl;
		cout << "" << endl;
	}
	return 0;
}
```

### Задача 4.5 «Синусоида»
```C++
#include <iostream>
#include <windows.h>
#include <math.h>
using namespace std;

int main()
{
	setlocale(LC_ALL, "Russian");

	double x = 0;
	for (double y = 1; y >= -1; y -= 0.1)
	{
		for (double x = 0; x <= 200; x++)
		{
			if (y < sin(x / 5) + 0.1 && y > (sin(x / 5) - 0.1))
			{
				cout << 'I';
			}
			else
			{
				cout << ' ';
			}
		}
		cout << endl;
	}
	
	return 0;
}
```

### Задача 4.6 «Автоматный распознаватель»
```C++
#include <iostream>
#include <windows.h>
#include <string>
using namespace std;

int replace(string i)
{
	if (i == "I")
	{
		return 1;
	}
	if (i == "V")
	{
		return 5;
	}
	if (i == "X")
	{
		return 10;
	}
	if (i == "L")
	{
		return 50;
	}
	if (i == "C")
	{
		return 100;
	}
	if (i == "D")
	{
		return 500;
	}
	if (i == "M")
	{
		return 1000;
	}
	else
	{
		return 0;
	}
}

int main()
{
	setlocale(LC_ALL, "Russian");
	
	string number = "";
	cout << "Введите число: ";
	cin >> number;

	int k = size(number) - 1;
	int* array = new int[k + 1];

	for (int i = 0; i <= k; i++)
	{
		string roman_num(1, number[i]);
		int num = replace(roman_num);
		array[i] = num;
	}

	for (int j = 0; j < k; j++)
	{
		if (array[j] < array[j + 1])
		{
			array[j] = -array[j];
		}
	}

	int sum = 0;

	for (int h = 0; h <= k; h++)
	{
		sum += array[h];
	}

	cout << sum << endl;
	delete[] array;
	return 0;
}
```

### Задача 4.7 «Генератор псевдослучайных чисел»
```C++
#include <iostream>
#include <windows.h>
using namespace std;

int main()
{
	setlocale(LC_ALL, "Russian");

	int n = 15;
	int m = 37, b = 3, c = 64, s0 = 0, si;
	int m_2 = 25173, b_2 = 13849, c_2 = 65537, s0_2 = 0, si_2;
	
	cout << "Вариант 1: " << endl;
	for (int i = 1; i <= n; i++)
	{
		si = (m * s0 + b) % c;
		cout << "s[" << i << "] = " << si << endl;
		s0 = si;
	}

	cout << "" << endl;

	cout << "Вариант 2: " << endl;
	for (int i = 1; i <= n; i++)
	{
		si_2 = (m_2 * s0_2 + b_2) % c_2;
		cout << "s[" << i << "] = " << si_2 << endl;
		s0_2 = si_2;
	}
	return 0;
}
```

### Задача 4.8 «Умножение матриц»
```C++
#include <iostream>
#include <windows.h>
using namespace std;

int main()
{
	setlocale(LC_ALL, "Russian");

	// Размеры таблиц
	const int rows_A = 3;
	const int columns_A = 4;
	const int rows_B = 4;
	const int columns_B = 2;
	const int rows_C = 3;
	const int columns_C = 2;

	double table_A[rows_A][columns_A] =
	{
		{5, 2, 0, 10},
		{3, 5, 2, 5},
		{20, 0, 0, 0}
	};

	double table_B[rows_B][columns_B] =
	{
		{1.2, 0.5},
		{2.8, 0.4},
		{5.0, 1.0},
		{2.0, 1.5}
	};

	double table_C[rows_C][columns_C] =
	{
		{table_A[0][0] * table_B[0][0] + table_A[0][1] * table_B[1][0] + table_A[0][2] * table_B[2][0] + table_A[0][3] * table_B[3][0], table_A[0][0] * table_B[0][1] + table_A[0][1] * table_B[1][1] + table_A[0][2] * table_B[2][1] + table_A[0][3] * table_B[3][1]},
		{table_A[1][0] * table_B[0][0] + table_A[1][1] * table_B[1][0] + table_A[1][2] * table_B[2][0] + table_A[1][3] * table_B[3][0], table_A[1][0] * table_B[0][1] + table_A[1][1] * table_B[1][1] + table_A[1][2] * table_B[2][1] + table_A[1][3] * table_B[3][1]},
		{table_A[2][0] * table_B[0][0] + table_A[2][1] * table_B[1][0] + table_A[2][2] * table_B[2][0] + table_A[2][3] * table_B[3][0], table_A[2][0] * table_B[0][1] + table_A[2][1] * table_B[1][1] + table_A[2][2] * table_B[2][1] + table_A[2][3] * table_B[3][1]},
	};

	double max_profit = 0;
	double min_profit = 99999999999999999;

	// Максимальный доход
	for (int seller_number = 0; seller_number <= 2; seller_number++)
	{
		if (table_C[seller_number][0] > max_profit)
			max_profit = table_C[seller_number][0];
	}

	for (int seller_number = 0; seller_number <= 2; seller_number++)
	{
		if (table_C[seller_number][0] == max_profit)
			cout << "Максимальный доход получил продавец " << seller_number + 1 << endl;
	}

	// Наименьший доход
	for (int seller_number = 0; seller_number <= 2; seller_number++)
	{
		if (table_C[seller_number][0] < min_profit)
			min_profit = table_C[seller_number][0];
	}

	for (int seller_number = 0; seller_number <= 2; seller_number++)
	{
		if (table_C[seller_number][0] == min_profit)
			cout << "Минимальный доход получил продавец " << seller_number + 1 << endl;
	}

	// Сумма денег за все товары
	double profit_sum = table_C[0][0] + table_C[1][0] + table_C[2][0];
	cout << "Общая сумма денег, вырученных за проданные товары: " << profit_sum << endl;

	// Сумма комисионных за все товары
	double commission_sum = table_C[0][1] + table_C[1][1] + table_C[2][1];
	cout << "Общая сумма комиссионных, полученных продавцами: " << commission_sum << endl;

	// Сумма комисионных за все товары
	double overall_sum = profit_sum + commission_sum;
	cout << "Общая сумма денег, прошедших через руки продавцов : " << overall_sum << endl;
	return 0;
}
```

### Задача 4.9 «Системы счисления»
```C++
#include <iostream>
#include <windows.h>
#include <string>
using namespace std;

// Перевод цифры в десятичное число
int number(int i, string number_1)
{
	if (int(number_1[i]) >= 48 and int(number_1[i]) <= 57)
	{
		return int(number_1[i]) - 48;
	}
	else
	{
		return int(number_1[i]) - 55;
	}
}

int main()
{
	setlocale(LC_ALL, "Russian");

	int system_1 = 16;
	int system_2 = 8;

	string number_1 = "";
	string number_2 = "";

	cout << "Введите исходное число: ";
	cin >> number_1;
	cout << "Введите основание исходного числа: ";
	cin >> system_1;
	cout << "Введите новое основание: ";
	cin >> system_2;

	int k = size(number_1) - 1;

	int decimal = 0;

	for (int i = k; i >= 0; i += -1)
	{
		int temp = number(k - i, number_1);
		decimal += temp * pow(system_1, i);
	}

	while (decimal > 0)
	{
		int remainder = decimal % system_2;
		string remainder_str = to_string(remainder);
		number_2 = number_2 + remainder_str;
		decimal = decimal / system_2;
	}

	reverse(number_2.begin(), number_2.end());
	cout << "Результат: " << number_2 << endl;
	return 0;
}
```
