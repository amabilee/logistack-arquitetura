# ADR 0001 – Estratégia de Nuvem e Escalabilidade

## Status

Aceito

## Contexto

O LogiTrack é uma plataforma de logística inteligente responsável pelo monitoramento de veículos, otimização dinâmica de rotas e processamento contínuo de eventos de localização em tempo real.

Os requisitos não funcionais priorizados para o sistema incluem:

* Alta escalabilidade;
* Alta disponibilidade;
* Resiliência;
* Performance em tempo real;
* Facilidade de manutenção.

O crescimento da operação logística implica aumento contínuo na quantidade de veículos monitorados, eventos processados e requisições simultâneas. Dessa forma, a arquitetura deve suportar expansão sob demanda sem necessidade de reestruturações significativas.

## Alternativas Consideradas

### Alternativa 1 – Infraestrutura como Serviço (IaaS)

Exemplo:

* AWS EC2
* Azure Virtual Machines

#### Vantagens

* Controle total sobre servidores.
* Flexibilidade de configuração.

#### Desvantagens

* Maior esforço operacional.
* Necessidade de gerenciamento manual de escalabilidade.
* Maior responsabilidade sobre segurança e atualização de infraestrutura.

### Alternativa 2 – Serverless

Exemplo:

* AWS Lambda
* Azure Functions

#### Vantagens

* Escalabilidade automática.
* Baixo custo para cargas esporádicas.
* Menor gerenciamento de infraestrutura.

#### Desvantagens

* Possibilidade de cold start.
* Maior complexidade para workloads persistentes.
* Menor aderência a serviços de longa execução.

### Alternativa 3 – Plataforma como Serviço (PaaS)

Exemplo:

* AWS ECS Fargate
* Azure Container Apps

#### Vantagens

* Escalabilidade automática.
* Menor esforço operacional.
* Facilidade de implantação.
* Adequado para arquiteturas baseadas em microsserviços.

#### Desvantagens

* Menor controle sobre infraestrutura.
* Dependência maior dos serviços do provedor.

## Decisão

Adotar uma estratégia baseada em Plataforma como Serviço (PaaS) utilizando AWS ECS Fargate para hospedagem dos microsserviços.

A arquitetura utilizará:

* AWS ECS Fargate para execução dos containers;
* PostgreSQL gerenciado para persistência;
* RabbitMQ para comunicação assíncrona;
* Application Load Balancer para distribuição de carga;
* CloudWatch para monitoramento e observabilidade.

## Justificativa

A abordagem PaaS oferece o melhor equilíbrio entre escalabilidade, custo operacional e simplicidade de gerenciamento.

A utilização de containers permite escalar individualmente os microsserviços mais demandados, como rastreamento e otimização de rotas, sem impactar os demais componentes do sistema.

Essa estratégia está alinhada aos atributos de qualidade priorizados para o projeto, especialmente escalabilidade, disponibilidade e manutenibilidade.

## Trade-offs

### Benefícios

* Escalabilidade horizontal simplificada.
* Redução do esforço operacional.
* Melhor utilização de recursos computacionais.
* Maior velocidade de implantação.

### Custos

* Menor controle sobre infraestrutura.
* Dependência do ecossistema do provedor de nuvem.
* Possível aumento de custos em cenários de utilização contínua e elevada.

## Consequências

A arquitetura passa a suportar crescimento progressivo da operação logística sem necessidade de reprojetar componentes críticos, mantendo desempenho e disponibilidade adequados para processamento em tempo real.

## Referências

* Richards, Mark; Ford, Neal. Fundamentals of Software Architecture.
* AWS Well-Architected Framework.
* Pressman, Roger. Engenharia de Software.
