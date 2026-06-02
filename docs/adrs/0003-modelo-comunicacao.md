# ADR 0003 – Comunicação Assíncrona Baseada em Eventos

## Status

Aceito

## Contexto

O LogiTrack processa continuamente eventos de localização, atualizações de rotas e informações operacionais provenientes de veículos distribuídos geograficamente.

Esses eventos precisam ser consumidos por diferentes componentes da arquitetura, incluindo:

* Rastreamento;
* Otimização de rotas;
* Notificações;
* Monitoramento operacional.

Uma abordagem totalmente síncrona aumentaria o acoplamento entre serviços e criaria riscos de indisponibilidade em cascata.

## Alternativas Consideradas

### Alternativa 1 – REST Síncrono

#### Vantagens

* Simplicidade.
* Facilidade de depuração.

#### Desvantagens

* Forte acoplamento.
* Maior latência acumulada.
* Maior risco de falhas em cascata.

### Alternativa 2 – gRPC

#### Vantagens

* Alta performance.
* Comunicação eficiente.

#### Desvantagens

* Maior complexidade operacional.
* Menor familiaridade da equipe.

### Alternativa 3 – Arquitetura Orientada a Eventos

#### Vantagens

* Desacoplamento.
* Escalabilidade.
* Resiliência.
* Processamento assíncrono.

#### Desvantagens

* Consistência eventual.
* Maior complexidade de monitoramento.

## Decisão

Adotar uma arquitetura orientada a eventos utilizando RabbitMQ como Message Broker.

A comunicação entre microsserviços ocorrerá predominantemente através de eventos de domínio.

Exemplos:

* NovaLocalizacaoRecebida;
* RotaAtualizada;
* EntregaConcluida.

Comunicação síncrona REST será mantida apenas para interações imediatas entre clientes e API Gateway.

## Justificativa

A comunicação assíncrona reduz dependências diretas entre serviços e permite que cada componente evolua e escale de forma independente.

O modelo baseado em eventos atende diretamente aos requisitos de:

* Escalabilidade;
* Resiliência;
* Performance;
* Manutenibilidade.

## Trade-offs

### Benefícios

* Baixo acoplamento.
* Processamento paralelo.
* Melhor tolerância a falhas.
* Escalabilidade independente.

### Custos

* Consistência eventual.
* Complexidade de observabilidade.
* Governança de eventos.

## Consequências

A arquitetura passa a operar de forma distribuída e orientada a eventos, aumentando a capacidade de processamento e a tolerância a falhas, ao custo de maior complexidade operacional.

## Referências

* Newman, Sam. Building Microservices.
* Fowler, Martin. Event Driven Architecture.
* Richards, Mark; Ford, Neal. Fundamentals of Software Architecture.
