Descrição do Problema

Com base na metodologia SOLID o código DependencyInversionViolation.java apresenta inconsistência, onde viola a ideia de Inversão de Dependência. 
A Inversão de Dependência declara que módulos de alto nível não devem depender de módulos de baixo nível, onde ambos devem depender de abstrações.
Já as abstrações não devem depender de detalhes. Já Detalhes devem depender de abstrações.

Local do problema

A classe Switch depende diretamente da implementação concreta de LighBuld, criando um alto acoplamento entre as classes.

Melhoria 

Para corrigir se deve adicionar uma abstração que represente um dispositivo que pode ser ligado ou desligado, dessa forma a classe Switch passa a depender da abstração ao invés de uma implementação concreta 
