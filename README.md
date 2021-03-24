//3 Вариант
Продавец,наименование,количество,цена,дата_продажи.Определить количество товаров, которые проданы менее года назад и вывести сведенья о них.
# -#include <iostream>
using namespace std;
struct Date {
    short day;
    short month;
    short year;
    bool isCorrect();
};
bool Date::isCorrect()
{
    bool result = false;
    if (month > 0 && month <= 12 && year <= 2021)
    {
        switch (month)
        {
        case 1:
        case 3:
        case 5:
        case 7:
        case 8:
        case 10:
        case 12:
        {
            if ((day <= 31) && (day > 0))
                result = true;
            break;
        }
        case 4:
        case 6:
        case 9:
        case 11:
        {
            if ((day <= 30) && (day > 0))
                result = true;
            break;
        }
        case 2:
        {
            if (year % 4 != 0)
            {
                if ((day <= 28) && (day > 0))
                    result = true;
            }
            else
                if (year % 400 == 0)
                {
                    if ((day <= 29) && (day > 0))
                        result = true;
                }
                else
                    if ((year % 100 == 0) && (year % 400 != 0))
                    {
                        if ((day == 28) && (day > 0))
                            result = true;
                    }
                    else
                        if ((year % 4 == 0) && (year % 100 != 0))
                            if ((day <= 29) && (day > 0))
                                result = true;
            break;
        }
        default:
            result = false;
        }
    }
    return result;
}
struct Tovar
{
    char Prodavec[56];
    char NameTovar[56];
    int Quantity;
    int Cost;
    Date DateOfIssue;
};
void task1()
{
    const int N = 2;
    Tovar group[N];
    for (int i = 0; i < N; i++)
    {
        cout << "\nInput Prodavec: ";
        cin.ignore(std::cin.rdbuf()->in_avail());
        cin.getline(group[i].Prodavec, 56);
        
        cout << "\nInput NameTovar: ";
        cin.ignore(std::cin.rdbuf()->in_avail());
        cin.getline(group[i].NameTovar, 56);
        
        cout << "\nInput Quantity: ";
        cin.ignore(std::cin.rdbuf()->in_avail());
        cin >> group[i].Quantity;
        
        cout << "\nInput Cost:";
        cin.ignore(std::cin.rdbuf()->in_avail());
        cin >> group[i].Cost;
        
        do
        {
            cout << "\nInput DateOfIssue: ";
            cin.ignore(std::cin.rdbuf()->in_avail());
            cin >> group[i].DateOfIssue.day >> group[i].DateOfIssue.month >> group[i].DateOfIssue.year;
        } while (!group[i].DateOfIssue.isCorrect());
        cin.ignore(std::cin.rdbuf()->in_avail());
        cin.clear();
    }
    for (int i = 0; i < N; i++)
    {
        
        if (group[i].DateOfIssue.year <= 2020 && group[i].DateOfIssue.month <= 3)
        {
            cout << "\n";
            cout << "Product " <<"'"<< group[i].NameTovar <<"'"<< " is over a year old.";
            cout << "\n";
        }
        else
        {
            cout << "\nNameTovar: " << group[i].NameTovar;
            cout << "\nProdavec: " << group[i].Prodavec;
            cout << "\nDateOfIssue: " << group[i].DateOfIssue.day << "." << group[i].DateOfIssue.month << "." << group[i].DateOfIssue.year;
            cout << "\nQuantity: " << group[i].Quantity;
            cout << "\nCost: " << group[i].Cost << endl;
        }
        
    }

}
int main()
{
    task1();
    return 0;
}
