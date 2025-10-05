# Prática Extencionista IV - Entrega 1
## Proposta de Arquitetura de Software para o Projeto "TaskMaster"

Este repositório contém a documentação e os artefatos de arquitetura de software para a primeira entrega da disciplina de Prática Extencionista IV.

### Integrantes do Grupo

[Vicenzo Henrique Peruzzo]
[Vinicius Dalpasquale] 

---

### 1. Estrutura do Repositório

O repositório está organizado da seguinte forma:

-   `README.md`: Este arquivo, que serve como a documentação central do projeto.
-   `/diagrams`: Uma pasta contendo os artefatos visuais da arquitetura.
    -   `1_diagrama_pacotes.md`: Código-fonte e explicação do Diagrama de Pacotes (Arquitetura da Aplicação).
    -   `2_diagrama_implantacao.md`: Código-fonte e explicação do Diagrama de Implantação.
    -   `3_diagrama_devops.md`: Código-fonte e explicação do Diagrama de Arquitetura DevOps.

---

### 2. Diagrama de Pacotes (Arquitetura da Aplicação)

O Diagrama de Pacotes abaixo descreve a arquitetura lógica da nossa aplicação, o "TaskMaster", um sistema de gestão de tarefas. A arquitetura foi modelada utilizando uma abordagem de camadas para separar as responsabilidades e promover baixo acoplamento e alta coesão.

```mermaid
graph TD
    subgraph "Arquitetura TaskMaster"
        WebApp -- "<<usa>>" --> Api
        Api -- "<<usa>>" --> Core
        Core -- "<<usa>>" --> Infrastructure
        Core -- "<<usa>>" --> Shared
        Infrastructure -- "<<usa>>" --> Shared
    end

    style WebApp fill:#cde4ff,stroke:#333,stroke-width:2px
    style Api fill:#cde4ff,stroke:#333,stroke-width:2px
    style Core fill:#baffc9,stroke:#333,stroke-width:2px
    style Infrastructure fill:#ffdfba,stroke:#333,stroke-width:2px
    style Shared fill:#f9f7d9,stroke:#333,stroke-width:2px

    ### 3. Diagrama de Arquitetura de Implantação

Este diagrama ilustra como os componentes de software serão distribuídos na infraestrutura em nuvem na AWS.

```mermaid
graph TD
    subgraph "Internet"
        Usuario[<i class="fa fa-user"></i> Usuário]
    end

    subgraph "AWS Cloud"
        LB[AWS Load Balancer]

        subgraph "Auto Scaling Group"
            EC2_1[EC2 Instance 1<br>Servidor API]
            EC2_2[EC2 Instance 2<br>Servidor API]
        end

        subgraph "Frontend Hosting"
             S3[S3 Bucket<br>WebApp (React)]
        end

        RDS[<i class="fa fa-database"></i> AWS RDS<br>(PostgreSQL)]
    end

    Usuario --> S3
    Usuario --> LB
    LB --> EC2_1
    LB --> EC2_2
    EC2_1 --> RDS
    EC2_2 --> RDS
