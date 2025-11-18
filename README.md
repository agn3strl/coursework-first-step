# Макет программы курсового проекта
```C
#define _CRT_SECURE_NO_DEPRECATE
#include <stdio.h>
#include <locale.h>
#include <math.h>

enum sphere {
	SOFTWARE,
	HARDWARE,
	CLOUD,
	CYBERSECURITY
};
typedef enum sphere Sphere;

enum rate {
	LOW,
	MIDDLE,
	HIGH
};
typedef enum rate Rate;

struct itcompany {
	char name[100];
	char country[100];
	Sphere sphere;
	int year_of_foundation;
	int number_of_employees;
	int market_cap;
	Rate rate;
};
typedef struct itcompany IT;

const char* spherestring(Sphere sphere);
const char* ratestring(Rate rate);
void inputcompany(IT* A);
void printcompany(const IT* A);
void printallcompanies(const IT companies[], int count);

int main()
{
	system("chcp 1251");
    IT companies[10]; 
    int count = 0; 
    int choice;
    printf("_____IT-КОМПАНИИ_____\n");
    do {
        printf("\n_____Меню_____\n");
        printf("1 - Добавить новую запись\n");
        printf("2 - Просмотреть все записи\n");
        printf("3 - Поиск по диапазону размера репозитория\n");
        printf("4 - Отсортировать данные\n");
        printf("5 - Сохранить данные в файл\n");
        printf("6 - Загрузить данные из файла\n");
        printf("7 - Выход\n");
        printf("Выберите действие:\n");
        scanf("%d", &choice);

        switch (choice) {
        case 1:
            if (count < 10) {
                inputcompany(&companies[count]);
                count += 1;
                printf("Компания успешно добавлена!\n");
            }
            else {
                printf("Достигнут максимум компаний (10)!\n");
            }
            break;

        case 2:
            printallcompanies(companies, count);
            break;

        case 3:
            printf("В разработке");
            break;

        case 4:
            printf("В разработке");
            break;

        case 5:
            printf("В разработке");
            break;

        case 6:
            printf("В разработке");
            break;

        case 7:
            printf("Выход из программы.\n");
            break;
        }

    } while (choice != 7);
    return 0;
}

const char* spherestring(Sphere sphere) 
{
	switch (sphere) {
	case SOFTWARE: return "Разработка ПО";
	case HARDWARE: return "Аппаратное обеспечение";
	case CLOUD: return "Облачные технологии";
	case CYBERSECURITY: return "Кибербезопасность";
	}
}

const char* ratestring(Rate rate)
{
	switch (rate) {
	case LOW: return "Низкий";
	case MIDDLE: return "Средний";
	case HIGH: return "Высокий";
	}
}

void inputcompany(IT* A) {
    printf("_____Ввод данных о компании_____\n");
    printf("Название компании:\n");
    scanf("%s", A->name);
    printf("Страна:\n");
    scanf(" %[^\n]", A->country);
    printf("Сфера деятельности (0 - Разработка ПО, 1 - Аппаратное обеспечение, 2 - Облачные технологии, 3 - Кибербезопасность):\n");
    int sphere;
    scanf("%d", &sphere);
    A->sphere = (Sphere)sphere;
    printf("Год основания:\n");
    scanf("%d", &A->year_of_foundation);
    printf("Количество сотрудников:\n");
    scanf("%d", &A->number_of_employees);
    printf("Рыночная капитализация (млн $):\n");
    scanf("%d", &A->market_cap);
    printf("Рейтинг работодателя (0 - Низкий, 1 - Средний, 2 - Высокий): ");
    int rate;
    scanf("%d", &rate);
    A->rate = (Rate)rate;
}

void printcompany(const IT* A) 
{
    printf("-----Информация о компании-----\n");
    printf("Название: %s\n", A->name);
    printf("Страна: %s\n", A->country);
    printf("Сфера деятельности: %s\n", spherestring(A->sphere));
    printf("Год основания: %d\n", A->year_of_foundation);
    printf("Количество сотрудников: %d\n", A->number_of_employees);
    printf("Рыночная капитализация: %d млн $\n", A->market_cap);
    printf("Рейтинг работодателя: %s\n", ratestring(A->rate));
    printf("----------------------------------------\n");
}

void printallcompanies(const IT companies[], int count) 
{
    if (count == 0) {
        printf("\nНет данных о компаниях.\n");
        return;
    }

    printf("\n_____Все компании_____\n");
    for (int i = 0; i < count; i++) {
        printf("\nКомпания №%d:\n", i + 1);
        printcompany(&companies[i]);
    }
}


```
