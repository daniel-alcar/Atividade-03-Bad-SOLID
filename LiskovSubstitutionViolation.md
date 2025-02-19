Descrição do Problema

Com base na metodologia SOLID o código LiskovSubstitutionViolation  viola o Princípio da Substituição de Liskov.
Nesse Princípio a subclasse não deve ser substituível por sua classe base sem alterar o comportamento esperado 
Como Ostrich estende Bird, é aguardado que ele possa voar, mas ela lança exceções causando erro
Local do problema

No código a subclasse `Ostrich` não pode ser usado corretamente no lugar da superclasse `Bird`


Melhoria 

Para corrigirserá necessário remodelar a hierarquia da classes, onde apenas os pássaros irão poder voar tenham o médoto fly()

````

public class Main {
    public static void main(String[] args) {

        Bird sparrow = new Sparrow();
        sparrow.eat();

        Flyable flyingBird = new Sparrow();
        flyingBird.fly();

        Bird ostrich = new Ostrich();
        ostrich.eat();
    }
}

abstract class Bird {
    public void eat() {

        System.out.println("eating");

    }
}

interface Flyable {

    void fly();

}

class Sparrow extends Bird implements Flyable {

    @Override
    public void fly() {

        System.out.println("Sparrow is flying");

    }
}

class Ostrich extends Bird {
}
