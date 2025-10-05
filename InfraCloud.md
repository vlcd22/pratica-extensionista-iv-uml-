### 4. Escolha de Infraestrutura na Cloud

Para a infraestrutura de nuvem do projeto "TaskMaster", a plataforma escolhida é a **Amazon Web Services (AWS)**. Abaixo, detalhamos a estrutura de ativação de usuários, a justificativa para a escolha da AWS e uma análise comparativa com outras plataformas de nuvem.

#### **Análise Comparativa: AWS vs. Microsoft Azure vs. Google Cloud (GCP)**

| Critério | Amazon Web Services (AWS) | Microsoft Azure | Google Cloud Platform (GCP) |
| :--- | :--- | :--- | :--- |
| **Market Share / Maturidade** | Líder de mercado, com a maior fatia e o serviço mais antigo (desde 2006). Altamente maduro e confiável. | Segundo maior player, com forte crescimento. Excelente para empresas que já utilizam o ecossistema Microsoft. | Terceiro maior, mas com tecnologia de ponta, especialmente em containers (Kubernetes), Big Data e Machine Learning. |
| **Gama de Serviços** | A mais ampla e profunda gama de serviços, cobrindo praticamente qualquer caso de uso imaginável. | Vasta gama de serviços, com integração nativa e profunda com produtos Microsoft (Windows Server, Office 365, .NET). | Foco em serviços de alta tecnologia e inovação. Plataforma de escolha para muitas startups de tecnologia. |
| **Documentação e Comunidade** | A mais extensa documentação e a maior comunidade online. É muito fácil encontrar tutoriais, cursos e respostas no Stack Overflow. | Documentação excelente e em crescimento. Forte suporte empresarial. | Documentação de alta qualidade, mas a comunidade online é menor em comparação com a AWS. |
| **Nível Gratuito (Free Tier)** | Oferece um nível gratuito generoso por 12 meses, incluindo os serviços essenciais (EC2, S3, RDS), ideal para projetos de estudantes. | Também oferece um nível gratuito robusto, com créditos para usar nos primeiros meses e serviços sempre gratuitos. | Considerado por muitos o mais generoso para serviços de computação e containers, com um nível gratuito "para sempre". |

#### **Motivo da Escolha da AWS (Por que a AWS?)**

A escolha da AWS como plataforma de nuvem para este projeto foi baseada em uma combinação de fatores estratégicos, técnicos e práticos:

1.  **Liderança de Mercado e Confiabilidade:** Sendo a plataforma mais antiga e líder de mercado, a AWS oferece uma estabilidade e confiabilidade comprovadas. Adotar a AWS também é uma habilidade valiosa e requisitada no mercado de trabalho.
2.  **Ecossistema de Serviços Completo:** Como demonstrado nos diagramas de implantação e DevOps, a AWS possui todos os serviços necessários para construir nossa arquitetura de ponta a ponta de forma nativa.
3.  **Documentação e Comunidade Imbatíveis:** Para um projeto acadêmico, a curva de aprendizado é um fator crucial. A vasta quantidade de documentação oficial, tutoriais e respostas em fóruns torna a resolução de problemas na AWS muito mais rápida.
4.  **Custo-Benefício e Nível Gratuito:** O nível gratuito da AWS nos permite hospedar e operar a aplicação durante a fase de desenvolvimento e apresentação sem incorrer em custos.

#### **Ativação e Estrutura de Usuário na Infraestrutura**

A gestão de acesso à infraestrutura e dos usuários da aplicação são dois pontos críticos. Na AWS, a estrutura seria a seguinte:

**1. Estrutura de Acesso da Equipe de Desenvolvimento:**

O acesso dos desenvolvedores à plataforma AWS será gerenciado pelo **AWS IAM (Identity and Access Management)**, seguindo o princípio do menor privilégio.
* **Conta Raiz (Root):** A conta principal será protegida com MFA e não será usada para atividades do dia a dia.
* **Usuários IAM:** Cada membro da equipe terá seu próprio usuário IAM com credenciais individuais.
* **Grupos e Permissões:** Serão criados grupos (ex: "Desenvolvedores") com permissões específicas para cada função.

**2. Estrutura de Usuários da Aplicação ("TaskMaster"):**

Para gerenciar os usuários finais da nossa aplicação, usaremos o **Amazon Cognito**.
* **Amazon Cognito** é um serviço que cuida de todo o ciclo de vida do usuário: cadastro, login, recuperação de senha, etc.
* **Vantagens:** Ao usar o Cognito, delegamos a complexidade da segurança e gerenciamento de identidades para um serviço robusto e escalável da AWS.
