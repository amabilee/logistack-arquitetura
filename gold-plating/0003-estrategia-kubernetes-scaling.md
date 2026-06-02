# Evolução da Estratégia de Escalabilidade com Kubernetes

## Objetivo

Como melhoria arquitetural adicional, foi realizada uma análise da utilização de Kubernetes para ampliar as capacidades de escalabilidade da plataforma LogiTrack.

A proposta complementa a estratégia original baseada em containers e serviços gerenciados em nuvem.

---

## Cenário Inicial

A arquitetura original já previa escalabilidade horizontal através da execução de múltiplas instâncias dos microsserviços.

Entretanto, o crescimento contínuo da operação logística pode gerar picos significativos de carga em componentes específicos, principalmente:

* Tracking Service;
* Route Service;
* Notification Service.

---

## Solução Proposta

Utilização de Kubernetes para gerenciamento dos containers da plataforma.

A estratégia inclui:

* Deploy automatizado;
* Recuperação automática de falhas;
* Balanceamento de carga;
* Autoescalonamento.

---

## Horizontal Pod Autoscaler (HPA)

O Kubernetes pode aumentar ou reduzir automaticamente o número de instâncias de um serviço.

Exemplo:

| Serviço              | Instâncias Mínimas | Instâncias Máximas |
| -------------------- | ------------------ | ------------------ |
| Tracking Service     | 2                  | 20                 |
| Route Service        | 2                  | 10                 |
| Notification Service | 1                  | 10                 |

---

## Escalabilidade Baseada em Eventos

Além do consumo de CPU e memória, o escalonamento pode considerar:

* Quantidade de mensagens no RabbitMQ;
* Taxa de eventos recebidos;
* Número de entregas simultâneas.

---

## Benefícios

### Escalabilidade Dinâmica

Capacidade de adaptação automática às cargas de trabalho.

### Melhor Utilização de Recursos

Redução de desperdício computacional.

### Alta Disponibilidade

Recuperação automática de containers com falha.

### Resiliência

Maior tolerância a falhas operacionais.

---

## Trade-offs

### Benefícios

* Alta elasticidade;
* Recuperação automática;
* Escalabilidade granular.

### Desvantagens

* Maior complexidade operacional;
* Necessidade de monitoramento adicional;
* Curva de aprendizado da plataforma.

---

## Conclusão

A adoção de Kubernetes representa uma evolução arquitetural importante para cenários de crescimento acelerado, fornecendo mecanismos avançados de escalabilidade e disponibilidade compatíveis com aplicações Cloud Native.
