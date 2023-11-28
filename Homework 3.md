## Домашняя работа 3
### Задача 3.1 «Заем»
```C++
#include <iostream>
using namespace std;

int main()
{
    setlocale(LC_ALL, "Russian");

    // Объявляем переменные для суммы займа (S), процентной ставки (p), срока (n) и ежемесячного платежа (m)
    float S, p, n, m;

    // Вводим сумму займа
    cout << "Введите S" << endl;
    cin >> S;

    // Вводим процентную ставку
    cout << "Введите p" << endl;
    cin >> p;

    // Вводим срок в месяцах
    cout << "Введите n" << endl;
    cin >> n;

    // Преобразуем процентную ставку в десятичную форму
    float r = p / 100;

    // Вычисляем ежемесячный платеж по формуле аннуитетного платежа
    m = (S * r * pow(1 + r, n)) / (12 * (pow(1 + r, n) - 1));

    // Выводим ежемесячный платеж
    cout << "m = " << m << endl;
    return 0;
}
```

## Задача 3.2 «Ссуда»
```C++
#include <iostream>
using namespace std;

int main()
{
	setlocale(LC_ALL, "Russian");
	double S, m, n;
	cout << "Введите S" << endl;
	cin >> S;
	cout << "Введите m" << endl;
	cin >> m;
	cout << "Введите n" << endl;
	cin >> n;
	for (double p = 0; p <= 100; p += 0.01)
	{
		double r = p / 100;
		double m1 = (S * r * pow(1 + r, n)) / (12 * (pow(1 + r, n) - 1));
		if (abs(m - m1) <= 0.05)
		{
			cout << "Процент = " << p << endl;
		}
	}
}
```

### Задача 3.3 «Копирование файла»
```C++
#include <iostream>
#include <windows.h>
#include <fstream>
using namespace std;

int main()
{
	SetConsoleCP(1251);
	SetConsoleOutputCP(1251);

	ofstream file;
	file.open("test.txt");
	file << "123ABH67JF9";
	file.close();

	char buf[50];
	fstream check;
	check.open("test.txt");
	check.getline(buf, 50);
	check.close();
	cout << buf << endl;

	return 0;
}
```

### Задача 3.4 «Фильтр»
```C++
#include <iostream>
#include <windows.h>
#include <fstream>
using namespace std;

int main()
{
	SetConsoleCP(1251);
	SetConsoleOutputCP(1251);

	char buf[50];
	fstream check;
	check.open("test.txt");
	check.getline(buf, 50);
	check.close();
	for (int i = 0; i <= 50; i++)
	{
		if ((int(buf[i]) >= 48) & (int(buf[i]) <= 57))
		{
			cout << buf[i];
		}
	}
	return 0;
}
```

## Задача 3.5 «Сортировка букв» - пузырьковая сортировка
```C++
#include <iostream>
#include <windows.h>
#include <fstream>
#include <string>
#include <algorithm>
using namespace std;

int main()
{
	SetConsoleCP(1251);
	SetConsoleOutputCP(1251);

	ofstream file;
	file.open("test.txt");
	file << "ZGQFJKBHUUGDUKJGFDLOYTYDVABCFDJG";
	file.close();

	char buf[30];
	string d;
	fstream check;
	check.open("test.txt");
	check.getline(buf, 30);
	check.close();
	cout << buf << endl;
	for (int i = 0; i < 29; i++)
	{
		for (int j = 0; j < 29 - i; j++)
		{
			if (buf[j] > buf[j + 1])
			{
				char temp = buf[j];
				buf[j] = buf[j + 1];
				buf[j + 1] = temp;
			}
		}
	}
	string buf2;
	for (int i = 0; i < 30; i++)
	{
		buf2.push_back(buf[i]);
	}
	cout << buf2 << endl;
	return 0;
}
```

## Задача 3.5 «Сортировка букв» - сортировка с помощью двоичного дерева
```C++
#include <iostream>
#include <windows.h>
#include <fstream>
#include <string>
#include <algorithm>
using namespace std;

struct TreeNode {
    char data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(char val) : data(val), left(nullptr), right(nullptr) {}
};

TreeNode* insert(TreeNode* root, char data) {
    if (root == nullptr) {
        return new TreeNode(data);
    }

    if (data < root->data) {
        root->left = insert(root->left, data);
    }
    else {
        root->right = insert(root->right, data);
    }

    return root;
}

void inOrderTraversal(TreeNode* root, string& result) {
    if (root != nullptr) {
        inOrderTraversal(root->left, result);
        result.push_back(root->data);
        inOrderTraversal(root->right, result);
    }
}

int main() {
    SetConsoleCP(1251);
    SetConsoleOutputCP(1251);

    ofstream file;
    file.open("test.txt");
    file << "ZGQFJKBHUUGDUKJGFDLOYTYDVABCFDJG";
    file.close();

    char buf[30];
    string d;
    fstream check;
    check.open("test.txt");
    check.getline(buf, 30);
    check.close();
    cout << buf << endl;

    TreeNode* root = nullptr;
    for (int i = 0; i < 30; i++) {
        root = insert(root, buf[i]);
    }

    string buf2;
    inOrderTraversal(root, buf2);

    cout << buf2 << endl;

    return 0;
}
```
