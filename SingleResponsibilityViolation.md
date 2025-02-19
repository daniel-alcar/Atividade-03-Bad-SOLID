Descrição do Problema

Com base na metodologia SOLID o código OpenClosedViolation viola o Princípio da Responsabilidade Única.
Esse princípio estabelece que uma classe deve ter apenas um motivo para mudar, ou seja, ela deve ter apenas uma única responsabilidade bem definida.

Local do problema

A Classe `Invoice` tem múltiplas responsabilidades.


Melhoria 

Para corrigir será necessário separar as responsabilidades em classes distintas

````

public class Main {
    public static void main(String[] args) {

        Invoice invoice = new Invoice(1000);
        
        InvoicePrinter printer = new InvoicePrinter();
        printer.print(invoice);
        
        InvoiceRepository repository = new InvoiceRepository();
        repository.save(invoice);
    }
}

class Invoice {

    private double amount;

    public Invoice(double amount) {

        this.amount = amount;

    }

    public double getAmount() {

        return amount;

    }
}

class InvoicePrinter {

    public void print(Invoice invoice) {

        System.out.println("Invoice amount: " + invoice.getAmount());

    }
}

class InvoiceRepository {

    public void save(Invoice invoice) {

        System.out.println("invoice");

    }
}
