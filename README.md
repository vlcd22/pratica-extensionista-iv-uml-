# Prática Extencionista IV - Entrega 1
## Proposta de Arquitetura de Software para o Projeto "TaskMaster"

Este repositório contém a documentação e os artefatos de arquitetura de software para a primeira entrega da disciplina de Prática Extencionista IV. Toda a documentação e diagramas estão consolidados neste único arquivo.

### Integrantes do Grupo

* [Vicenzo Henrique Peruzzo]
* [Vinicius Dalpasquale]

---

### 1. Diagrama de Pacotes (Arquitetura da Aplicação)

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

### 2. Diagrama de Arquitetura de Implantação

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

---

### 3. Diagrama de Arquitetura DevOps

graph LR
    subgraph "Desenvolvimento"
        Dev[<i class="fa fa-laptop"></i> Desenvolvedor] -- "git push" --> Git[<i class="fa fa-github"></i> GitHub Repo]
    end

    subgraph "CI/CD Pipeline (GitHub Actions)"
        Git -- "Trigger" --> Build[1. Build & Test]
        Build -- "Success" --> Package[2. Package App<br>(Docker Image)]
        Package -- "Success" --> Push[3. Push to ECR<br>(AWS Container Registry)]
        Push -- "Success" --> Deploy[4. Deploy to AWS<br>(Update EC2 Service)]
    end

    subgraph "Produção (AWS)"
        Deploy --> Infra[Infraestrutura AWS<br>EC2, RDS, S3]
    end
