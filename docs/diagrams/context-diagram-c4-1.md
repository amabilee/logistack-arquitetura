## Diagrama de Contexto (C4 – Nível 1)

```mermaid
flowchart LR

    %% Pessoas
    Gestor["Gestor Logístico"]
    Motorista["Motorista da Frota"]
    Operacao["Equipe de Operação"]

    %% Sistema Principal
    LogiTrack["LogiTrack
    Sistema de otimização de rotas
    e gestão de entregas em tempo real"]

    %% Sistemas Externos
    Mapas["APIs de Mapas e Trânsito"]
    ERP["Sistema ERP"]
    Estoque["Sistema de Estoque / WMS"]
    Comunicacao["Serviço de Notificações"]
    Rastreamento["Serviço de Telemetria / GPS"]
    Clientes["Portal do Cliente"]

    %% Relacionamentos Usuários
    Gestor -->|"Consulta KPIs, acompanha SLAs e analisa previsões"| LogiTrack
    Motorista -->|"Recebe rotas otimizadas e envia status das entregas"| LogiTrack
    Operacao -->|"Monitora eventos operacionais e gerencia incidentes"| LogiTrack

    %% Relacionamentos Sistemas Externos
    LogiTrack -->|"Consulta rotas, distâncias e trânsito"| Mapas
    LogiTrack -->|"Recebe pedidos e atualiza entregas"| ERP
    LogiTrack -->|"Consulta disponibilidade de produtos"| Estoque
    LogiTrack -->|"Dispara notificações e alertas"| Comunicacao
    LogiTrack -->|"Recebe localização dos veículos"| Rastreamento
    LogiTrack -->|"Fornece ETA e status das entregas"| Clientes
```