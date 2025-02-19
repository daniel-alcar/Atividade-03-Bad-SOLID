Descrição do Problema

Com base na metodologia SOLID o código OpenClosedViolation viola o Princípio do Aberto-Fechado.
Esse princípio estabelece que a classe deve estar aberta (public) para extensão, mas fechada(private) para modificação.
Como Ostrich estende Bird, é aguardado que ele possa voar, mas ela lança exceções causando erro.

Local do problema

No código a classe `DiscountCalculator` só é modificada quando um novo tipo de cliente é adicionado, isso quebra a logicado  OCP.


Melhoria 

Para corrigir será necessário usar o polimorfismo com a interface para definir o comportamento extensível sem a necessidade de modificar o código existente.

````

public class Main {

    public static void main(String[] args) {

        DiscountCalculator calculator = new DiscountCalculator();

        DiscountStrategy vipDiscount = new VIPDiscount();
        System.out.println("VIP Discount: " + calculator.calculateDiscount(vipDiscount, 200));

        DiscountStrategy regularDiscount = new RegularDiscount();
        System.out.println("Regular Discount: " + calculator.calculateDiscount(regularDiscount, 200));
    }
}

interface DiscountStrategy {

    double applyDiscount(double amount);

}

class RegularDiscount implements DiscountStrategy {

    @Override
    public double applyDiscount(double amount) {

        return amount * 0.1;

    }
}

class VIPDiscount implements DiscountStrategy {

    @Override
    public double applyDiscount(double amount) {

        return amount * 0.2;

    }
}

class DiscountCalculator {

    public double calculateDiscount(DiscountStrategy strategy, double amount) {

        return strategy.applyDiscount(amount);

    }
}
