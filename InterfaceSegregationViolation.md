Descrição do Problema

Com base na metodologia SOLID o código InterfaceSegregationViolation viola o Princípio da Segregação de Interface.
Nesse Princípio a classe não deve ser forçada a implementar um método que não utiliza.

No código se uma impresso  não suporta todas as funcionalidades precisará implementar métodos desnecessários, que resultaram em exceções, ocupando espaço e até mesmo retornando valores vazios.

Local do problema

A interface `Machine`faz com que qualquer outra classe que implemente os métodos `print()`,`scan()` e `fax()` 


Melhoria 

Para corrigir será necessário segregar a classe `Machine` em interfaces menores, e permitir que classes implementem apenas funcionalidades importantes

````
public class InterfaceSegregationSolution {
    public static void main(String[] args) {
        MultiFunctionPrinter multiPrinter = new MultiFunctionPrinter();
        multiPrinter.print();
        multiPrinter.scan();
        multiPrinter.fax();

        SimplePrinter simplePrinter = new SimplePrinter();
        simplePrinter.print();
    }
}

interface Printer {

    void print();

}

interface Scanner {

    void scan();

}

interface Fax {

    void fax();

}

class MultiFunctionPrinter implements Printer, Scanner, Fax {

    public void print() {

        System.out.println("Printing");

    }

    public void scan() {

        System.out.println("Scanning...");
    }

    public void fax() {

        System.out.println("Faxing");
    }
}

class SimplePrinter implements Printer {

    public void print() {

        System.out.println("Printing");

    }
}
