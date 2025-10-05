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

    WebApp: Camada de apresentação (frontend). Construída em uma tecnologia como React, Angular ou Vue.js, é responsável por toda a interface do usuário. Ela consome os dados da Api.

    Api: A camada de API (backend for frontend). Expõe os endpoints RESTful que a WebApp consome. É responsável por autenticação, autorização e encaminhamento de requisições para a camada Core.

    Core: O coração da aplicação. Contém toda a lógica de negócio, serviços, entidades e regras que definem o que a aplicação faz, independentemente da tecnologia de UI ou banco de dados.

    Infrastructure: Camada de infraestrutura. Contém as implementações concretas de acesso a recursos externos, como o banco de dados (repositórios), envio de e-mails, e integração com outros serviços.

    Shared: Um pacote de utilitários comum, contendo código que pode ser reutilizado por múltiplas camadas, como modelos de dados (DTOs), constantes, e funções auxiliares.
