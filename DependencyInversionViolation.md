Descrição do Problema

Com base na metodologia SOLID o código DependencyInversionViolation.java apresenta inconsistência, onde viola a ideia de Inversão de Dependência. 
A Inversão de Dependência declara que módulos de alto nível não devem depender de módulos de baixo nível, onde ambos devem depender de abstrações.
Já as abstrações não devem depender de detalhes. Já Detalhes devem depender de abstrações.

Local do problema

A classe Switch depende diretamente da implementação concreta de LighBuld, criando um alto acoplamento entre as classes.

Melhoria 

Para corrigir se deve adicionar uma abstração que represente um dispositivo que pode ser ligado ou desligado, dessa forma a classe Switch passa a depender da abstração ao invés de uma implementação concreta 


`public class DependencyInversionSolution {
    public static void main(String[] args) {
      
        Device bulb = new LightBulb();
      
        Switch lightSwitch = new Switch(bulb);

        lightSwitch.turnOn();
      
        lightSwitch.turnOff();
      
    }
}

interface Device {
  
    void turnOn();
    void turnOff();
  
}

class LightBulb implements Device {
  
    @Override
    public void turnOn() {
      
        System.out.println("LightBulb is ON");
      
    }

    @Override
    public void turnOff() {
      
        System.out.println("LightBulb is  OFF");
      
    }
}

class Switch {
  
    private Device device;

    public Switch(Device device) {
      
        this.device = device;
      
    }

    public void turnOn() {
      
        device.turnOn();
      
    }

    public void turnOff() {
      
        device.turnOff();
      
    }
}`
