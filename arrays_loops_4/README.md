# Задача 3

Благодаря вам финансовое приложение умеет записывать и выводить траты. Научите его ещё и анализировать их — печатать не все сразу, а только одну — самую крупную. Для этого внесите в код такие изменения:
1. Добавьте в меню ещё одну команду «5 — Показать самую большую сумму расходов за неделю». В тело программы допишите дополнительное ветвление для её обработки.
2. При выполнении новой команды приложение должно найти в массиве расходов за неделю самое большое значение и вывести его на экран. Для этого сначала создайте дополнительную переменную maxExpense со стартовым значением 0. Затем с помощью цикла for сравните maxExpense со всеми элементами массива. Если значение элемента больше, сохраняйте его в переменной maxExpense — так она будет всё время перезаписываться и после завершения цикла в ней окажется нужная вам самая крупная сумма расходов. Напечатайте её в строке «Самая большая сумма расходов на этой неделе составила ... тенге.».
```java
import java.util.Scanner;

public class Practice {
    public static void main(String[] args) {
        double[] expenses = new double[7];

        double rateUSD = 450;
        double rateEUR = 500;
        double rateRUB = 5;

        Scanner scanner = new Scanner(System.in);

        System.out.println("Сколько денег у вас осталось до зарплаты?");
        double moneyBeforeSalary = scanner.nextDouble();

        System.out.println("Сколько дней до зарплаты?");
        int daysBeforeSalary = scanner.nextInt();

        while (true) {
            System.out.println("Что вы хотите сделать?");
            System.out.println("1 — Конвертировать валюту");
            System.out.println("2 — Получить совет");
            System.out.println("3 — Ввести трату");
            System.out.println("4 - Показать траты за неделю");
            // Допишите вывод нового пункта меню
            ...
            System.out.println("0 — Выход");

            int command = scanner.nextInt();

            if (command == 1) {
                System.out.println("Ваши сбережения: " + moneyBeforeSalary + " KZT");
                System.out.println("В какую валюту хотите конвертировать? Доступные варианты: 1 - USD, 2 - EUR, 3 - RUB.");
                int currency = scanner.nextInt();
                if (currency == 1) {
                    System.out.println("Ваши сбережения в долларах: " + moneyBeforeSalary / rateUSD);
                } else if (currency == 2) {
                    System.out.println("Ваши сбережения в евро: " + moneyBeforeSalary / rateEUR);
                } else if (currency == 3) {
                    System.out.println("Ваши сбережения в рублях: " + moneyBeforeSalary / rateRUB);
                } else {
                    System.out.println("Неизвестная валюта");
                }
            } else if (command == 2) {
                if (moneyBeforeSalary < 10000) {
                    System.out.println("Сегодня лучше поесть дома. Экономьте, и вы дотянете до зарплаты!");
                } else if (moneyBeforeSalary < 35000) {
                    if (daysBeforeSalary < 10) {
                        System.out.println("Окей, пора в Макдак!");
                    } else {
                        System.out.println("Сегодня лучше поесть дома. Экономьте, и вы дотянете до зарплаты!");
                    }
                } else if (moneyBeforeSalary < 80000) {
                    if (daysBeforeSalary < 10) {
                        System.out.println("Неплохо! Прикупите долларов и зайдите поужинать в классное место. :)");
                    } else {
                        System.out.println("Окей, пора в Макдак!");
                    }
                } else {
                    if (daysBeforeSalary < 10) {
                        System.out.println("Отлично! Заказывайте крабов!");
                    } else {
                        System.out.println("Неплохо! Прикупите долларов и зайдите поужинать в классное место. :)");
                    }
                }
            } else if (command == 3) {
                System.out.println("За какой день вы хотите ввести трату: 1-ПН, 2-ВТ, 3-СР, 4-ЧТ, 5-ПТ, 6-СБ, 7-ВС?");
                int day = scanner.nextInt();
                System.out.println("Введите размер траты:");
                double expense = scanner.nextDouble();
                moneyBeforeSalary = moneyBeforeSalary - expense;
                expenses[day - 1] = expenses[day - 1] + expense;
                System.out.println("Значение сохранено! Ваш текущий баланс в тенге: " + moneyBeforeSalary);
                if (moneyBeforeSalary < 5000) {
                    System.out.println("На вашем счету осталось совсем немного. Стоит начать экономить!");
                }
            } else if (command == 4) {
                for (int i = 0; i < expenses.length; i++) {
                    System.out.println("День " + (i + 1) + ". Потрачено " + expenses[i] + " тенге");
                }
            } else if (...) { // Добавьте условие в ветвление для обработки новой команды
                /* Объявляем переменную maxExpense для хранения самой большой суммы расходов. 
                   Сначала её значение неизвестно, поэтому равно нулю */
                double maxExpense = 0;
                for (int i = ...; i < ...; ...) { // Проходим циклом по всему массиву трат
                    if (...) { // Сравниваем, больше ли текущий элемент массива значения maxExpense
                        // Если условие верно, то записываем в maxExpense значение текущего элемента массива
                        maxExpense = ...;
                    }
                }
                // Печатаем максимум расходов:
                System.out.println("Самая большая сумма расходов на этой неделе составила " + ... + " тенге.");
            } else if (command == 0) {
                System.out.println("Выход");
                break;
            } else {
                System.out.println("Извините, такой команды пока нет.");
            }
        }
    }
}
```