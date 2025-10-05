### 2. Diagrama de Arquitetura de Implantação (Versão Simplificada)

Este diagrama ilustra a arquitetura de implantação na nuvem AWS de forma simplificada para garantir a renderização correta.

```mermaid
graph TD
    Usuario[Usuario na Internet] --> Frontend[WebApp no S3]
    Usuario --> LoadBalancer[Load Balancer]

    subgraph "Infraestrutura AWS"
        LoadBalancer --> Servidor1[Servidor API 1]
        LoadBalancer --> Servidor2[Servidor API 2]
        Servidor1 --> BancoDeDados[Banco de Dados RDS]
        Servidor2 --> BancoDeDados[Banco de Dados RDS]
    end
