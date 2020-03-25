# Массивы
Массив – это структура данных, хранящая набор значений одного типа. Доступ к элементам
массива осуществляется по индексу, индексация элементов начинаяется с нуля. [Подробнее](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays).

## Типы массивов
* [Одномерные](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/arrays/single-dimensional-arrays): new int[4];

| 0 | 1 | 2 | 3 | 4 |
| - | - | - | - | - |
| [0] -23 | [1] 0 | [2] 15 | [3] 0 | [4] 2|


• [Многомерные](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/arrays/multidimensional-arrays): new int[3,3], new int[2,4,5,6..n];
| |0 | 1 | 2|
|-|-|-|-|
0| [0, 0] 50| [0, 1] -24| [0, 2] 0
1| [1, 0] 82| [1, 1] 4| [1, 2] 0
2| [2, 0] 0| [2, 1] 0| [2, 2] 0



• [Рваные](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/arrays/jagged-arrays): new object[3][]
 |0 | 1 | 2
-|-|-|-
0| [0, 0] 50| [0, 1] -24
1| [1, 0] 82| [1, 1] 4| [1, 2] 0
2| [2, 0] 0


## Инициализация массивов
    int[] numbers = new int[3];
    numbers[0] = 10;
    numbers[2] = 82;
    numbers[1] = -4;
    int[] moreNumbers = new int[] { 1, 3, -29 };
    int[] otherNumbers = new[] { 5, 7, 8, 0, 0, 0, 0, 0 };
    string[] words = new[] { "foo", "bar" };
    char[] letters = new[] { 'a', 'b', 'l' };
    
## Распространенные ошибки при работе с массивами
### Попытка хранить данные различных типов
    int[] array = new int[1];
    array[0] = “some words”; 
- ошибка. Объявлен массив с элементами int, а пытаемся
присвоить ячейке string.
## Попытка обращения к элементу за границами массива
    int[] array = new int[5];
    array[5] = 10; 
 - ошибка. Длина массива 5, но индексация начинается с нуля, так что максимальный индекс – 4.

## Циклы
Циклы – это конструкции, которые используются для многократного выполнения кода, поэтому
отлично подходят для таких операций, как обход массивов:

* [for](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/for) – для повторения кода заданное количество раз
    
        for (int i = 0; i < words.Length; i++)
        {
            Console.WriteLine(words[i]);
        }

* [foreach](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) – для перебора коллекций

        foreach (string word in words)
        {
            Console.WriteLine(word);
        }

* [while](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/while), [do/while](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/do) – для повторения кода, пока выполняется заданное условие

        int counter = 0;
        while (counter < words.Length - 1)
        {
            Console.WriteLine(words[counter]);
            counter++;
        }

## Генерация псевдослучайных чисел
Генерировать псевдослучайные числа можно с помощью метода [Next](https://docs.microsoft.com/en-us/dotnet/api/system.random.next?view=netframework-4.8) класса [Random](https://docs.microsoft.com/en-us/dotnet/api/system.random?view=netframework-4.8). Обратите
внимание, что несколько объектов класса Random [могут возвращать](https://docs.microsoft.com/en-us/dotnet/api/system.random?view=netframework-4.8#Multiple) одинаковые
последовательности чисел, поэтому рекомендуется использовать только один объект.

