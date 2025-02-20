Descrição do Problema

Com base na metodologia SOLID o código TightCouplingViolation viola o Princípio da Inversão de Dependência.
Visto que a classe `Car` está fortemente acoplada a implementação concreta `Engine`

Local do problema

A Classe lasse `Car` depende diretamente da classe `Engine` 


Melhoria 

Para corrigir será necessário criar uma abstração de interface para `Engine` e fazer `Car` depender dessa interface 

````
public class DependencyInversionAlternative {
    public static void main(String[] args) {
        Car car = new Car();
        
        // Podemos injetar qualquer motor sem modificar a classe Car
        Engine petrolEngine = EngineFactory.createEngine("petrol");
        car.setEngine(petrolEngine);
        car.start();
        
        Engine electricEngine = EngineFactory.createEngine("electric");
        car.setEngine(electricEngine);
        car.start();
    }
}

interface Engine {
    void start();
}

class PetrolEngine implements Engine {

    @Override
    public void start() {
        System.out.println("Petrol Engine started");
    }
}

class ElectricEngine implements Engine {
    @Override
    public void start() {

        System.out.println("Electric Engine started");

    }
}

class Car {
    private Engine engine;

    public void setEngine(Engine engine) {

        this.engine = engine;

    }


    public void start() {

        if (engine == null) {

            System.out.println("No engine installed");

        } else {

            engine.start();
            System.out.println("Car is running");

        }
    }
}

class EngineFactory {

    public static Engine createEngine(String type) {

        return switch (type.toLowerCase()) {

            case "petrol" -> new PetrolEngine();
            case "electric" -> new ElectricEngine();

            default -> throw new IllegalArgumentException("Unknown engine type");

        };
    }
}
`
