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





