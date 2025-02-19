Descrição do Problema

Com base na metodologia SOLID o código ImproperExceptionHandling viola o Princípio da Responsabilidade única, e além disso não está tratando as exceções de erro.

Local do problema

A captura da exceção não está diferenciando qual foi o motivo do erro 
A mensagem de erro oferece uma resposta nada satisfatória para o usuário em `Something went wrong!`


Melhoria 

Para corrigir será necessário capturas as exceções importantes e lançar de forma adequada 


````
public class Main {
    public static void main(String[] args) {

        Calculator calculator = new Calculator();

        try {

            System.out.println("Result: " + calculator.divide(10, 0));

        } catch (ArithmeticException e) {

            System.out.println("Error: Division by zero is not allowed.");

        } catch (Exception e) {

            System.out.println("Unexpected error: " + e.getMessage());

        }
    }
}

class Calculator {
    public int divide(int a, int b) {

        if (b == 0) {

            throw new ArithmeticException("Cannot divide by zero.");
        }

        return a / b;

    }
}
`
