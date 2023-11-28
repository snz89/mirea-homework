## Другие задания
### Задание «Монахи»
```C++
#include <iostream>
using namespace std;

int main()
{
    setlocale(LC_ALL, "Russian");

    int students[600][3];  // Массив учеников и их учителей
    int teachers[600];     // Массив учителей для каждого ученика
    int teachers_2[2][3];  // Массив для хранения учителей двух учеников
    int choice, student1, student2;
    int common_teacher = 0;

    cin >> choice;

    // Исходные данные
    students[31][0] = 41; students[31][1] = 42; students[31][2] = 43;
    students[24][0] = 31; students[24][1] = 32; students[24][2] = 0;
    students[23][0] = 33; students[23][1] = 34; students[23][2] = 0;
    students[12][0] = 24; students[12][1] = 25; students[12][2] = 0;
    students[10][0] = 21; students[10][1] = 22; students[10][2] = 23;
    students[0][0] = 11; students[0][1] = 12; students[0][2] = 13;

    for (int i = 0; i < 600; i++) {
        teachers[i] = -1;
    }
    for (int student = 0; student < 600; student++) {
        for (int i = 0; i < 600; i++) {
            for (int j = 0; j <= 2; j++) {
                if (students[i][j] == student + 1) {
                    teachers[student] = i + 1;
                }
            }
        }
    }

    if (choice == 1) {
        cin >> student1;
        if (student1 < 1 || student1 > 600) {
            cout << "Введен неверный номер";
            return 0;
        }
        if (teachers[student1 - 1] == -1) {
            cout << "Не ученик" << endl;
            return 0;
        }
        else {
            common_teacher = teachers[student1 - 1];
            cout << "Ученик, его учителя " << common_teacher;
            while (common_teacher != 1) {
                common_teacher = teachers[common_teacher - 1];
                if (common_teacher == -1 || common_teacher == 1) {
                    return 0;
                }
                else {
                    cout << ", " << common_teacher;
                }
            }
        }
    }

    if (choice == 2) {
        cin >> student1;
        cin >> student2;
        if (student1 < 1 || student1 > 600 || student2 < 1 || student2 > 600) {
            cout << "Введен неверный номер";
            return 0;
        }
        if (teachers[student1 - 1] == -1) {
            cout << student1 << " - не ученик" << endl;
        }
        if (teachers[student2 - 1] == -1) {
            cout << student2 << " - не ученик" << endl;
        }
        else {
            common_teacher = student1;
            for (int i = 0; i < 3; i++) {
                teachers_2[0][i] = teachers[common_teacher - 1];
                common_teacher = teachers[common_teacher - 1];
            }
            common_teacher = student2;
            for (int i = 0; i < 3; i++) {
                teachers_2[1][i] = teachers[common_teacher - 1];
                common_teacher = teachers[common_teacher - 1];
            }
            for (int i = 0; i < 3; i++) {
                for (int j = 0; j < 3; j++) {
                    if (teachers_2[0][i] == teachers_2[1][j]) {
                        cout << student1 << " и " << student2 << " оба ученики, и их общий учитель " << teachers_2[0][i];
                    }
                }
            }
        }
    }
    return 0;
}
```

### Башня
```C++
#include <iostream>
using namespace std;


void towers(int n, int from, int to, int temp, int& count)
{
    if (n != 0) {
        towers(n - 1, from, temp, to, count);
        towers(n - 1, temp, to, from, count);
        count++;
    }
}

int main()
{
    setlocale(LC_ALL, "Russian");

    int n = 3;
    int count = 0;
    int from = 1, temp = 2, to = 3;

    cout << "Введите n: ";
    cin >> n;

    towers(n, from, temp, to, count);
    cout << "Число перестановок: " << count;

    return 0;
}
```

### Быки и коровы
```C++
#include <iostream>
#include <string>
#include <random>
using namespace std;

void number_enter(string& my_number, bool s) {
    if (s == 0) {
        cout << "Введите число, состоящее из 4 цифр: ";
    }
    else {
        cout << "Введите другое число: ";
    }
    cin >> my_number;

    if (size(my_number) != 4) { // Проверка на длину числа
        cout << "Вы ввели число не из 4 цифр" << endl;
        number_enter(my_number, 0);
    }
}

void removeDuplicates(int array[], int& n) {
    if (n <= 1) {
        return;
    }

    int index = 0;

    for (int i = 1; i < n; ++i) {
        if (array[i] != array[index]) {
            array[i + index] = array[i];
        }
    }

    n = index + 1;
}

void minuses(string computer_number, string my_number, int& minus) {
    for (int i = 0; i < 4; ++i) {
        if (computer_number[i] != my_number[i]) {
            if (my_number.find(computer_number[i]) != string::npos) {
                minus++;
            }
        }
    }
}

void pluses(string computer_number, string my_number, int& plus) { // Поиск плюсов
    for (int i = 0; i < 4; i++) {
        if (computer_number[i] == my_number[i]) {
            plus++;
        }
    }
}

void computer_number_generator(string& computer_number) {
    // Генератор случайного числа
    random_device rd;
    mt19937 gen(rd());
    uniform_int_distribution<int> distribution(1000, 9999);
    int random_number = distribution(gen);
    string h = to_string(random_number);
    int count = 0;

    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            if (i != j && int(h[i]) == int(h[j])) {
                count += 1;
            }
        }
    }

    if (count > 0) {
        computer_number_generator(computer_number);
    }
    else {
        computer_number = h;
    }
}

int main()
{
    setlocale(LC_ALL, "Russian");

    int count = 1; // Количество попыток, за которое выиграли
    int plus = 0; // Кол-во плюсов
    int minus = 0; // Кол-во минусов
    string computer_number; // Не должно содержать одинаковых чисел, добавить генератор чисел
    string my_number;

    computer_number_generator(computer_number);
    cout << computer_number << endl;

    number_enter(my_number, 0);
    cout << endl;

    while (plus < 4) {
        plus = 0;
        minus = 0;

        pluses(computer_number, my_number, plus);
        minuses(computer_number, my_number, minus);

        if (plus == 4) {
            cout << "Вы выиграли за " << count << " попыток!";
            return 0;
        }

        cout << "----- Попытка №" << count << " -----" << endl;
        cout << "Кол-во плюсов: " << plus << endl;
        cout << "Кол-во минусов: " << minus << endl;
        count++;

        number_enter(my_number, 1);
        cout << endl;
    }
}
```

### Шарики
```C++
// Шарики
#include <iostream>
using namespace std;

int* balls;
int n;
int perm_count = 0;

void swap(int a, int b)
{
    int temp = balls[a];
    balls[a] = balls[b];
    balls[b] = temp;
}

void generate(int k)
{
    if (k == n)
    {
        for (int i = 0; i < n; i++)
        {
            if (balls[i] == i + 1)
            {
                perm_count++;
                break;
            }
        }
    }
    else
    {
        for (int j = k; j < n; j++)
        {
            swap(k, j);
            generate(k + 1);
            swap(k, j);
        }
    }
}

int main()
{
    setlocale(LC_ALL, "Russian");
    cout << "Введите количество шариков (n): ";
    cin >> n;
    balls = new int[n];
    for (int i = 0; i < n; i++)
        balls[i] = i + 1;
    generate(0);

    cout << "Количество перестановок: " << perm_count << endl;
    delete[] balls;
}
```
