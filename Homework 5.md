## Домашняя работа 5
### Задание «Алгоритм Евклида»
```C++
#include <iostream>
#include <windows.h>
#include <math.h>
using namespace std;

int main()
{
	setlocale(LC_ALL, "Russian");

	int number_1, number_2;
	cout << "Число 1: ";
	cin >> number_1;
	cout << "Число 2: ";
	cin >> number_2;

	// Деление

	int remainder, max_div, temp_max, temp_min;
	remainder = max(number_1, number_2) % min(number_1, number_2);

	if (remainder == 0)
	{
		max_div = min(number_1, number_2);
	}
	else
	{
		temp_max = min(number_1, number_2);
		temp_min = remainder;

		while (remainder != 0)
		{
			remainder = temp_max % temp_min;
			temp_max = temp_min;
			temp_min = remainder;
		}
		max_div = temp_max;
	}

	cout << "НОД, полученный делением: " << max_div << endl;

	// Вычитание
	int temp_1, temp_2, k = 1;
	temp_1 = number_1;
	temp_2 = number_2;

	while (temp_1 != temp_2)
	{
		if (temp_1 > temp_2)
		{
			temp_1 = temp_1 - temp_2;
		}
		else
		{
			temp_2 = temp_2 - temp_1;
		}
	}

	cout << "НОД, полученный вычитанием: " << temp_1 << endl;
	return 0;
}
```

```C++
// Задание «Решето Эратосфена»
#include <iostream>
#include <windows.h>
#include <math.h>
using namespace std;

bool prime(int i)
{
	if (i <= 1)
	{
		return 0;
	}
	for (int k = 2; k < i; k++)
	{
		if (i % k == 0)
		{
			return 0;
		}
	}
	return 1;
}

int main()
{
	setlocale(LC_ALL, "Russian");

	int n;
	cout << "Введите число N: ";
	cin >> n;

	cout << "Простые числа от 2 до " << n << ":" << endl;
	for (int i = 2; i <= n; i++)
	{
		if (prime(i) == 1)
		{
			cout << i << endl;
		}
	}

	return 0;
}
```

### Задание «Обработка текстовых файлов» (13 - Запись текста в текстовый файл)
```C++
#include <iostream>
#include <windows.h>
#include <string>
#include <fstream>
using namespace std;

int main()
{
	setlocale(LC_ALL, "Russian");
	
	string enter;
	cout << "Введите текст: ";
	cin >> enter;

	ofstream file;
	file.open("file.txt");
	file << enter;
	file.close();

	char buf[50];
	fstream read;
	read.open("file.txt");
	read.getline(buf, 50);
	read.close();
	cout << buf << endl;

	return 0;
}
```

### Задание «Ряды» - 1
```C++
#include <iostream>
#include <windows.h>
#include <math.h>
using namespace std;

int main()
{
	setlocale(LC_ALL, "Russian");

	double n, n_start = 1, div = 0, y = 0, temp = 0;
	cout << "Введите n: ";
	cin >> n;
	
	while (n_start <= n)
	{
		div = div + sin(n_start);
		temp = n_start / div;
		y = y + temp;
		n_start += 1;
	}
	cout << y << endl;

	return 0;
}
```

### Задание «Ряды» - 3
```C++
#include <iostream>
#include <windows.h>
#include <math.h>
using namespace std;

int main()
{
	setlocale(LC_ALL, "Russian");

	double n, n_start = 1, div = 0, y = 1, temp = 0, factorial = 1;
	cout << "Введите n: ";
	cin >> n;
	
	while (n_start <= n)
	{
		div = div + sin(2 * n_start);
		for (double i = 1; i <= n_start; i++)
		{
			factorial = factorial * i;
		}
		temp = factorial / div;
		y = y * temp;
		n_start += 1;
		factorial = 1;
	}
	
	cout << y << endl;

	return 0;
}
```

### Задание «Файлы» - 13
```C++
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");

    int n, record_num;

    cout << "Введите количество чисел: ";
    cin >> n;

    int* numbers = new int[n];

    // Запись чисел в файл
    ofstream recordFile;
    recordFile.open("numbers.txt");
    for (int i = 1; i <= n; i++) {
        cout << "Введите число " << i << ": ";
        cin >> record_num;
        recordFile << record_num << endl;
    }
    recordFile.close();

    // Ввод чисел в массив из файла
    ifstream readFile;
    readFile.open("numbers.txt");
    string line;
    for (int j = 0; j < n; j++) {
        if (!getline(readFile, line)) {
            cout << "Ошибка чтения строки" << endl;
            return 1;
        }
        double number = stod(line);
        numbers[j] = number;
    }
    readFile.close();

    // Поиск максимального числа
    int maxNumber = numbers[0];
    for (int i = 1; i < n; i++) {
        if (numbers[i] > maxNumber) {
            maxNumber = numbers[i];
        }
    }

    // Поиск минимального числа
    int minNumber = numbers[0];
    for (int i = 1; i < n; i++) {
        if (numbers[i] < minNumber) {
            minNumber = numbers[i];
        }
    }

    int numQuantity = 0;
    int numQuantity2 = 0;
    int maxQuantity = 0;

    // Поиск максимального количества
    for (int target = minNumber; target <= maxNumber; target++) {
        for (int i = 0; i < n; i++) {
            if (numbers[i] == target) {
                numQuantity += 1;
            }
        }

        if (numQuantity > maxQuantity) {
            maxQuantity = numQuantity;
        }

        numQuantity = 0;
    }

    // Ввод чисел в файл
    ofstream sortedFile;
    sortedFile.open("sorted_numbers.txt");

    for (int target = minNumber; target <= maxNumber; target++) {
        for (int i = 0; i < n; i++) {
            if (target == numbers[i]) {
                numQuantity2 += 1;
            }
        }

        if (numQuantity2 == maxQuantity) {
            for (int i = 1; i <= maxQuantity; i++) {
                sortedFile << target << endl;
            }
        }
        numQuantity2 = 0;
    }
    sortedFile.close();

    // Вывод
    cout << endl;
    cout << "Исходные числа:" << endl;
    char readLine[30];
    ifstream out1("numbers.txt");
    while (out1.getline(readLine, 30)) {
        for (int i = 0; i < strlen(readLine); i++) {
            cout << readLine[i];
        }
        cout << endl;
    }
    out1.close();

    cout << endl;
    cout << "После обработки:" << endl;
    char readLine2[30];
    ifstream out2("sorted_numbers.txt");
    while (out2.getline(readLine2, 30)) {
        for (int i = 0; i < strlen(readLine2); i++) {
            cout << readLine2[i];
        }
```
