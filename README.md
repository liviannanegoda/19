 # ***Итоговая контрольная работа*** #
 ___
 ## **Задача** ##
*Написать программу, которая из имеющегося массива строк формирует новый массив из строк, длина которых меньше, либо равна 3 символам. Первоначальный массив можно ввести с клавиатуры, либо задать на старте выполнения алгоритма. При решении не рекомендуется пользоваться коллекциями, лучше обойтись исключительно массивами.* 

## **Решение** ##

### Для решения задачи были созданы функции: ###
* FillArray для заполнения массива
* PrintArray для печати массива
* CountStringSymbols для подсчета количества элементов в массиве, длина которых меньше либо равна 3 символам
* GenerateNewArray для создания нового массива, состоящего из строк, длина которых меньше либо равна 3 символам 

## **Алгоритм решения** ##

* Создаем массив;
  * наполняем массив строками (ввод в консоли);
  * производим подсчета количества элементов в массиве, длина которых меньше либо равна 3 символа;
* Cоздаем новый массив размером, равным количеству подсчитанных элементов;
  * заполняем новый массив элементами, длина которых меньше либо равна 3 символа;
  * выводим на печать исходный массив и и новый массив.
```C#
string[] workArray = FillArray();
string[] resultArray = GenerateNewArray(workArray);
string firstArray = PrintArray(workArray);
string secondArray = PrintArray(resultArray);
Console.WriteLine(firstArray + " -> " + secondArray);

string[] FillArray()
{
    Console.WriteLine("Введите данные через пробел, по окончании ввода нажмите Enter: ");
    string? enterSymbols = Console.ReadLine();
    if (enterSymbols == null) { enterSymbols = ""; };
    char[] separators = new char[] { ',', ' ' };
    string[] workArray = enterSymbols.Split(separators, StringSplitOptions.RemoveEmptyEntries);
    return workArray;
}

string PrintArray(string[] workArray)
{
    string stringArray = "[";
    for (int i = 0; i < workArray.Length; i++)
    {
        if (i == workArray.Length - 1)
        {
            stringArray += $"\"{workArray[i]}\"";
            break;
        }
        stringArray += ($"\"{workArray[i]}\", ");
    }
    stringArray += "]";
    return stringArray;
}

int CountStringSymbols(string[] workArray)
{
    int counter = 0;
    foreach (string item in workArray)
    {
        if (item.Length <= 3)
        {
            counter++;
        }
    }
    return counter;
}

string[] GenerateNewArray(string[] workArray)
{
    int resultArrayLength = CountStringSymbols(workArray);
    string[] resultArray = new string[resultArrayLength];
    int i = 0;
    foreach (string item in workArray)
    {
        if (item.Length <= 3)
        {
            resultArray[i] = item;
            i++;
        }
    }
    return resultArray;
}
```

