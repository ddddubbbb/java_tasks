# Задача

Вам нужно снять наличные в банкомате, но он сломался и выводит только консоль с недописанным кодом. 
По счастливой случайности — на Java. Допишите код — реализуйте методы в классе `BankAccount`. 
Чтобы установить и считать значение суммы денег на счёте `moneyAmount`, вам понадобятся get- и set-методы. 
Чтобы снять деньги со счёта и обнулить его — метод `withdrawAll()`, который должен обнулять счёт и печатать 
количество выданных денег в формате: _Со счёта снято 10000 тг_. 
Все методы должны иметь самый широкий уровень доступа. В результате запуска программы в консоли должно появиться:
```
Количество денег на счету - 10000 тг. (сумма может быть любой)
Со счёта снято 10000 тг.
Количество денег на счету - 0 тг.
```

```java
public class Main {
    public static void main(String[] args) {
        BankAccount bankAccount = new BankAccount();
        bankAccount.setMoneyAmount(10000); // передайте в банкомат сумму на счету
        System.out.println("Количество денег на счету - " + bankAccount.getMoneyAmount() + " тг.");
        bankAccount.withdrawAll(); // вызовите метод вывода средств
        System.out.println("Количество денег на счету - " + bankAccount.getMoneyAmount() + " тг.");
    }
}

class BankAccount {
    private long moneyAmount;

    // допишите код методов
    // используйте параметр newMoneyAmount для установки нового значения

    public long getMoneyAmount() {
        return moneyAmount;
    }

    public void setMoneyAmount(long moneyAmount) {
        this.moneyAmount = moneyAmount;
    }

    public void withdrawAll(){
        System.out.println("Со счёта снято " + moneyAmount + " тг.");
        moneyAmount = 0;
    }
}
```