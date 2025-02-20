Descrição do Problema

Com base na metodologia SOLID o código ViolationOfEncapsulation viola o Princípio da Encapsulação.
A encapsulação é responsável por proteger os atributos de uma classe contra modificações indevidas

Local do problema

Os atributos públicos `name` e `age` podem ser alterados em qualquer local


Melhoria 

Para corrigir será necessário tornar os atributos `public` como `private` e criar métodos `get` e `set` para controlar como os atributos podem ser alterados pelo usuário

````
public class EncapsulationAlternative {

    public static void main(String[] args) {

        Person person = new Person("John Doe", 30);
        System.out.println(person);

    }
}

class Person {

    private String name;
    private int age;

    public Person(String name, int age) {

        setName(name);
        setAge(age);

    }

    public void setName(String name) {

        if (name == null || name.trim().isEmpty()) {

            throw new IllegalArgumentException("Name cannot be empty.");

        }

        this.name = name;

    }

    public String getName() {

        return name;

    }

    public void setAge(int age) {

        if (age < 0) {

            throw new IllegalArgumentException("Age cannot be negative");

        }

        this.age = age;

    }

    public int getAge() {

        return age;

    }

    @Override
    public String toString() {

        return name + " is " + age + " years old";

    }
}
