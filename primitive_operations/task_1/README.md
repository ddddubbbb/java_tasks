# Задача
Менеджер отдал вам на доработку приложение для компании по прокату самокатов.
Заказчик просит, чтобы приложение умело рассчитывать цену аренды в моменты повышенного спроса
и вело учёт арендованных и возвращённых самокатов. Данные о количестве доступных и выданных самокатов будет
вводить администратор проката. Вам необходимо дописать код строго в соответствии с техническим заданием:
* Настройте считывание с клавиатуры значений переменных `availableScooters` и `scootersInUse`.
* Реализуйте возможность вводить команды бесконечно. Не забудьте предусмотреть её завершение.
* Внутри класса `Scooter` реализуйте методы `rentScooter()`, `returnScooter()` и `getPrice()`:
* Метод `getPrice()` должен вычислять текущую стоимость аренды `currentPrice`. Для этого к числу арендованных скутеров `scootersInUse` надо прибавить 1, результат разделить на число доступных скутеров `availableScooters`. Полученное частное умножить на добавочную стоимость `additionalPrice` и прибавить к цене по умолчанию `defaultPrice`.
* Метод `rentScooter()` должен обрабатывать выдачу самоката и сообщать администратору текущую цену его аренды. Чтобы это сделать, нужно модифицировать формулу `currentPrice` — перед проведением расчётов увеличить на единицу значение переменной `scootersInUse`, а после их окончания уменьшить на единицу значение переменной `availableScooters`.
* Вычисления в методах `getPrice()` и `rentScooter()` необходимо провести одной строкой. Перед выполнением арифметических выражений в обоих методах нужно проверить наличие доступных самокатов.
* Метод `returnScooter()` должен учитывать возврат самоката: уменьшать на единицу число арендованных самокатов и увеличивать на единицу число доступных самокатов. При приёме нужно не забыть проверить, есть ли вообще несданные самокаты.
* Внутри класса `Practice` создайте объект класса `Scooter` и вызовите методы `rentScooter()`, `returnScooter()` и `getPrice()` в соответствии с меню доступных команд.

#### Класс Scooter
```java
public class Scooter {
    int availableScooters;
    int scootersInUse;
    int defaultPrice = 29; // Цена аренды по умолчанию
    int additionalPrice = 5; // Добавочная стоимость при повышенном спросе

    Scooter(int inputAvailableScooters, int inputScootersInUse) {
        availableScooters = inputAvailableScooters;
        scootersInUse = inputScootersInUse;
    }

    void getPrice() {
        ... { // Проверьте, есть ли доступные самокаты
            System.out.println("Нет доступных самокатов.");
        } else {
            int currentPrice = ... // Посчитайте текущую стоимость проката
            System.out.println("Текущая стоимость проката: " + currentPrice + " тг/мин");
        }
    }

    void rentScooter() {
        if (...) { // Проверьте, есть ли доступные самокаты
            System.out.println("Доступных самокатов не осталось.");
        } else {
            int currentPrice = ... /* Посчитайте текущую стоимость проката,
            увеличьте число арендованных самокатов и уменьшите число доступных */
            System.out.println("Выдайте самокат по цене " + currentPrice + " тг/мин");
            System.out.println("Самокатов в аренде: " + scootersInUse);
            System.out.println("Самокатов доступно: " + availableScooters);
        }
    }

    void returnScooter() {
        ... { // Проверьте, есть ли самокаты в аренде
            System.out.println("Все самокаты уже возвращены.");
        } else {
            ... // Уменьшите число арендованных самокатов и увеличьте число доступных
            System.out.println("Самокат принят.");
            System.out.println("Самокатов в аренде: " + scootersInUse);
            System.out.println("Самокатов доступно: " + availableScooters);
        }
    }
}
```

#### main
```java
import java.util.Scanner;

public class Practice {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.println("Сколько самокатов доступно для аренды?");
        int availableScooters = ...; // Считайте количество доступных самокатов с клавиатуры

        System.out.println("Сколько самокатов арендовано?");
        int scootersInUse = ...; // Считайте число арендованных самокатов с клавиатуры

        Scooter scooter = ...; // Создайте новый объект класса Scooter

        System.out.println("Что вы хотите сделать?");
        System.out.println("1 -- Узнать текущую стоимость проката");
        System.out.println("2 -- Выдать самокат");
        System.out.println("3 -- Принять самокат");
        System.out.println("4 -- Завершить работу");

        ... { // реализуйте непрерывный ввод команд
            System.out.println("Введите команду:");
            int command = ... // Считайте команду с клавиатуры

            if (command == 1) {
                ... // Вызовите нужный метод класса Scooter
            } else if (command == 2) {
                ... // Вызовите нужный метод класса Scooter
            } else if (command == 3) {
                ... // Вызовите нужный метод класса Scooter
            } else if (command == 4) {
                System.out.println("Сеанс работы завершён!");
                ... // Завершите ввод команд и работу программы 
            } else {
                System.out.println("Введён неверный код команды.");
            }
        }
    }
}
```