# ADR-GP-0001 – Introdução de Observabilidade Distribuída

## Status

Aceito

## Contexto

A arquitetura do LogiTrack foi concebida utilizando microsserviços e comunicação orientada a eventos.

Embora essa abordagem forneça benefícios relacionados à escalabilidade e resiliência, ela também aumenta significativamente a complexidade operacional.

Durante a análise arquitetural foi identificado que a ausência de mecanismos formais de observabilidade dificultaria:

* Diagnóstico de falhas;
* Monitoramento de desempenho;
* Análise de gargalos;
* Auditoria operacional.

---

## Alternativas Consideradas

### Alternativa 1 – Monitoramento Básico

Utilizar apenas logs locais dos serviços.

#### Vantagens

* Simplicidade.
* Baixo custo inicial.

#### Desvantagens

* Baixa visibilidade.
* Diagnóstico lento.
* Escalabilidade limitada.

---

### Alternativa 2 – Logs Centralizados

Centralização de logs em uma plataforma única.

#### Vantagens

* Melhor rastreabilidade.
* Facilidade de consulta.

#### Desvantagens

* Visibilidade limitada sobre fluxos distribuídos.

---

### Alternativa 3 – Observabilidade Completa

Combinação de:

* Logs;
* Métricas;
* Tracing distribuído.

#### Vantagens

* Visão completa do sistema.
* Diagnóstico rápido.
* Monitoramento proativo.

#### Desvantagens

* Maior complexidade.
* Maior consumo de recursos.

---

## Decisão

Adotar uma estratégia de observabilidade distribuída baseada em três pilares:

### Logs

Registro centralizado de eventos operacionais.

### Métricas

Coleta contínua de indicadores técnicos.

### Tracing Distribuído

Rastreamento de requisições entre microsserviços.

---

## Ferramentas Consideradas

* OpenTelemetry
* Prometheus
* Grafana
* CloudWatch

---

## Justificativa

A observabilidade completa oferece suporte adequado para a operação de sistemas distribuídos modernos.

Essa estratégia reduz o tempo necessário para identificar falhas, aumenta a confiabilidade da plataforma e melhora a capacidade de evolução da arquitetura.

---

## Consequências

### Positivas

* Melhor monitoramento.
* Menor MTTR.
* Diagnóstico mais rápido.
* Operação mais previsível.

### Negativas

* Maior complexidade arquitetural.
* Necessidade de infraestrutura adicional.
* Custos operacionais ligeiramente superiores.

---

## Referências

NEWMAN, Sam. Building Microservices.

NYGARD, Michael. Release It!.

RICHARDS, Mark; FORD, Neal. Fundamentals of Software Architecture.

OpenTelemetry Documentation.

Prometheus Documentation.
