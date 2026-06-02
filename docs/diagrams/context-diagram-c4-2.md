## Diagrama de Containers (C4 – Nível 2)

```mermaid
flowchart LR

    %% Usuários
    Gestor["Gestor Logístico"]
    Operacao["Equipe de Operação"]
    Motorista["Motorista"]

    %% Frontends
    Web["Web App
    React"]

    Mobile["App Mobile
    Flutter"]

    %% Backend
    Gateway["API Gateway
    Node.js / Express"]

    Route["Route Service
    Python"]

    Tracking["Tracking Service
    Node.js"]

    Notification["Notification Service
    Node.js"]

    Rabbit["RabbitMQ
    Message Broker"]

    Database[("PostgreSQL")]

    Cache[("Redis Cache")]

    %% Sistemas Externos
    Maps["APIs de Mapas
    Google Maps / OSM"]

    ERP["Sistema ERP"]

    Estoque["Sistema de Estoque"]

    Comunicacao["Serviço de Notificações Externo"]

    GPS["Serviço GPS / Telemetria"]

    %% Usuários
    Gestor -->|"HTTPS"| Web
    Operacao -->|"HTTPS"| Web
    Motorista -->|"HTTPS"| Mobile

    %% Frontend
    Web -->|"REST"| Gateway
    Mobile -->|"REST"| Gateway

    %% Gateway
    Gateway -->|"REST"| Route
    Gateway -->|"REST"| Tracking
    Gateway -->|"REST"| Notification

    %% Banco
    Gateway --> Database

    Route --> Database
    Tracking --> Database

    %% Cache
    Gateway --> Cache
    Route --> Cache

    %% Eventos
    Route -->|"Publica eventos"| Rabbit
    Tracking -->|"Publica eventos"| Rabbit
    Rabbit -->|"Consome eventos"| Notification

    %% Integrações
    Route -->|"Consulta rotas"| Maps

    Gateway -->|"Pedidos"| ERP
    Gateway -->|"Estoque"| Estoque

    Notification -->|"SMS / Email / Push"| Comunicacao

    GPS -->|"Localização"| Tracking
```