# Estratégia de Otimização de Custos em Nuvem

## Objetivo

Como evolução arquitetural da plataforma LogiTrack, foi realizada uma análise de estratégias para redução de custos operacionais em ambientes Cloud Native, mantendo os requisitos de desempenho, disponibilidade e escalabilidade definidos para o sistema.

O objetivo é garantir que a arquitetura seja economicamente sustentável à medida que a operação logística cresce.

---

## Problema Identificado

Arquiteturas baseadas em microsserviços podem gerar custos elevados devido à execução contínua de múltiplos containers, armazenamento de dados, transferência de rede e processamento de eventos.

Sem uma estratégia adequada de governança financeira, o crescimento da infraestrutura pode resultar em desperdício de recursos computacionais e aumento significativo das despesas operacionais.

---

## Estratégias Propostas

### Auto Scaling

Os microsserviços serão escalados apenas quando necessário.

Benefícios:

* Redução de recursos ociosos;
* Menor custo computacional;
* Melhor utilização da infraestrutura.

---

### Escalabilidade Independente

Cada serviço será escalado individualmente.

Exemplos:

* Tracking Service pode crescer para 20 instâncias.
* Notification Service pode permanecer com apenas 2 instâncias.

Benefício:

Evita escalabilidade desnecessária de componentes pouco utilizados.

---

### Uso de Containers Gerenciados

A utilização de AWS ECS Fargate elimina a necessidade de manter servidores dedicados.

Benefícios:

* Pagamento baseado em consumo;
* Redução de custos operacionais;
* Menor esforço administrativo.

---

### Processamento Assíncrono

O uso de RabbitMQ reduz a necessidade de processamento síncrono constante.

Benefícios:

* Melhor aproveitamento computacional;
* Distribuição equilibrada da carga;
* Redução de picos de utilização.

---

### Armazenamento Inteligente

Dados históricos poderão ser arquivados periodicamente para camadas de armazenamento mais econômicas.

Benefícios:

* Redução de custos de banco de dados;
* Melhor gerenciamento de retenção de dados.

---

## Benefícios Esperados

* Redução do custo total de propriedade (TCO);
* Melhor eficiência operacional;
* Crescimento sustentável da plataforma;
* Maior previsibilidade financeira.

---

## Impacto Arquitetural

A otimização de custos passa a ser considerada um atributo arquitetural relevante, complementando requisitos de desempenho, escalabilidade e disponibilidade.
