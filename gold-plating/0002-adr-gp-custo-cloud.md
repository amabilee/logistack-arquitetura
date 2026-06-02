# ADR-GP-0001 – Estratégia de Otimização de Custos em Nuvem

## Status

Aceito

## Contexto

A arquitetura do LogiTrack foi projetada para operar em ambiente cloud utilizando microsserviços, mensageria e escalabilidade horizontal.

Embora essa abordagem ofereça benefícios significativos de disponibilidade e elasticidade, ela também pode aumentar os custos operacionais à medida que a plataforma cresce.

Foi identificada a necessidade de incorporar práticas arquiteturais voltadas para eficiência financeira da infraestrutura.

---

## Alternativas Consideradas

### Alternativa 1 – Infraestrutura Superdimensionada

Manter recursos permanentemente disponíveis para suportar picos de carga.

#### Vantagens

* Simplicidade operacional.
* Disponibilidade imediata.

#### Desvantagens

* Alto custo.
* Recursos frequentemente ociosos.

---

### Alternativa 2 – Escalabilidade Manual

Aumentar recursos conforme necessidade operacional.

#### Vantagens

* Controle direto dos custos.

#### Desvantagens

* Processo lento.
* Dependência operacional.
* Risco de indisponibilidade.

---

### Alternativa 3 – Escalabilidade Automática e Consumo Sob Demanda

Utilizar mecanismos automáticos de escalabilidade e cobrança baseada em uso.

#### Vantagens

* Melhor eficiência financeira.
* Elasticidade.
* Redução de desperdício.

#### Desvantagens

* Maior complexidade de monitoramento.
* Dependência dos recursos da plataforma cloud.

---

## Decisão

Adotar uma estratégia de otimização de custos baseada em:

* Auto Scaling;
* Containers gerenciados;
* Escalabilidade independente por microsserviço;
* Processamento assíncrono;
* Monitoramento contínuo de consumo.

---

## Justificativa

A abordagem permite alinhar crescimento operacional e consumo de recursos computacionais.

Dessa forma, a infraestrutura cresce apenas quando necessário, reduzindo desperdícios e aumentando a eficiência financeira da solução.

---

## Consequências

### Positivas

* Menor custo operacional.
* Melhor utilização de recursos.
* Crescimento sustentável.
* Maior previsibilidade financeira.

### Negativas

* Dependência maior da plataforma cloud.
* Necessidade de monitoramento contínuo.
* Complexidade adicional de configuração.

---

## Referências

AWS Well-Architected Framework – Cost Optimization Pillar.

Richards, Mark; Ford, Neal. Fundamentals of Software Architecture.

Microsoft Azure Architecture Center – Cost Optimization.
