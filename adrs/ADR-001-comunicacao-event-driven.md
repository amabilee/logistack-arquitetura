- **Título:** Estratégia de Comunicação entre Microsserviços baseada em Mensageria (Event-Driven)

- **Contexto:**  
O LogiTrack precisa processar grandes volumes de dados em tempo real, como localização de veículos, eventos de entrega e atualizações de rotas. Esses dados são gerados continuamente e devem ser consumidos por múltiplos serviços (ex: rastreamento, otimização de rotas, notificações) sem comprometer a performance e a disponibilidade do sistema.  
Uma abordagem baseada apenas em comunicação síncrona (REST) geraria forte acoplamento entre serviços, aumento de latência em cadeias de chamadas e maior risco de falhas em cascata, especialmente considerando a dependência de APIs externas e instabilidade de rede (ex: dispositivos móveis dos motoristas).

- **Decisão:**  
Adotar uma **arquitetura orientada a eventos (Event-Driven)** utilizando um **Message Broker (RabbitMQ)** como principal mecanismo de comunicação entre microsserviços.  
Os serviços passam a se comunicar predominantemente de forma **assíncrona**, por meio de publicação e consumo de eventos (ex: `NovaLocalizacaoRecebida`, `RotaAtualizada`, `EntregaConcluida`).  
A comunicação síncrona (REST) será mantida apenas para operações que exigem resposta imediata (ex: requisições do frontend via API Gateway).

- **Justificativa:**  

**1. Performance e Tempo Real (RNF crítico)**  
- *Benefício:* A comunicação assíncrona permite que eventos sejam processados em paralelo, reduzindo o tempo de resposta percebido e evitando bloqueios entre serviços.  
- *Trade-off:* Introduz latência eventual no processamento completo do fluxo (ex: uma atualização pode não refletir instantaneamente em todos os serviços).

**2. Resiliência e Tolerância a Falhas**  
- *Benefício:* O uso de filas desacopla produtores e consumidores. Se um serviço estiver indisponível, as mensagens permanecem na fila para processamento posterior, evitando perda de dados.  
- *Trade-off:* Exige mecanismos adicionais como retry, dead-letter queues e controle de duplicidade de eventos.

**3. Escalabilidade**  
- *Benefício:* Consumidores podem ser escalados horizontalmente conforme o volume de eventos (ex: aumento de veículos enviando localização).  
- *Trade-off:* Requer gerenciamento mais complexo de infraestrutura e monitoramento do broker.

**4. Baixo Acoplamento entre Serviços**  
- *Benefício:* Serviços não precisam conhecer diretamente uns aos outros, apenas os eventos, facilitando evolução e manutenção.  
- *Trade-off:* Maior complexidade na governança de eventos (versionamento, contratos e rastreabilidade).

**5. Consistência de Dados (Impacto negativo controlado)**  
- *Trade-off:* O sistema passa a operar com **consistência eventual**, o que exige cuidados no design (ex: idempotência, ordenação de eventos e reconciliação de estados).  
- *Mitigação:* Uso de identificadores únicos de eventos, armazenamento confiável e processamento idempotente.

- **Conclusão:**  
A adoção de mensageria com arquitetura orientada a eventos foi escolhida por alinhar-se diretamente aos requisitos de **alta performance, escalabilidade e resiliência**, fundamentais para um sistema de logística em tempo real, mesmo ao custo de maior complexidade arquitetural e operacional.