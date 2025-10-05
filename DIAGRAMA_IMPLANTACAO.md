graph TD
    subgraph "Internet"
        Usuario[Usuário]
    end

    subgraph "AWS Cloud"
        LB[AWS Load Balancer]

        subgraph "Auto Scaling Group"
            EC2_1[EC2 Instance 1 - Servidor API]
            EC2_2[EC2 Instance 2 - Servidor API]
        end

        subgraph "Frontend Hosting"
            S3[S3 Bucket - WebApp React]
        end

        RDS[AWS RDS - PostgreSQL]
    end

    Usuario --> S3
    Usuario --> LB
    LB --> EC2_1
    LB --> EC2_2
    EC2_1 --> RDS
    EC2_2 --> RDS
