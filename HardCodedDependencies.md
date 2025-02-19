Descrição do Problema

Com base na metodologia SOLID o código HardCodedDependencies viola a Inversão de Dependência. 
O código possui um limite de utilização, não podendo adicionar novas funções sem que precise alterar o código todo, limitando assim a reutilização do mesmo.

Local do problema

A classe `HardCodedDependencies` depende diretamente da implementação da classe `Report`
A classe `Report` tem múltipla função, tanto na geração do relatórios como na apresentação


Melhoria 

Para corrigir precisa criar uma interface e movera  responsabilidade de gerenciamento

````
public class HardCodedDependencies {
    public static void main(String[] args) {

        ReportGenerator report = new PDFReport(); // Injeção de dependência
        ReportService service = new ReportService(report);
        service.generateReport();
    }
}

interface ReportGenerator {

    void generateReport();
}

class PDFReport implements ReportGenerator {

    @Override
    public void generateReport() {

        System.out.println("Generating PDF");

    }
}

class ReportService {

    private final ReportGenerator reportGenerator;

    public ReportService(ReportGenerator reportGenerator) {

        this.reportGenerator = reportGenerator;

    }

    public void generateReport() {

        reportGenerator.generateReport();

    }
}
