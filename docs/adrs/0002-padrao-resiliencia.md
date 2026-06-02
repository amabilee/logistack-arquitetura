# ADR 0002 – Estratégia de Resiliência com API Gateway e Circuit Breaker

## Status

Aceito

## Contexto

O LogiTrack depende de integrações externas para cálculo de rotas e geolocalização, além de comunicação entre múltiplos microsserviços.

Falhas temporárias em serviços externos ou internos não podem comprometer completamente a operação logística, pois isso impactaria diretamente o cumprimento de SLAs e a eficiência operacional.

A arquitetura deve ser capaz de tolerar falhas parciais e continuar operando mesmo diante da indisponibilidade temporária de componentes específicos.

## Alternativas Consideradas

### Alternativa 1 – Fail Fast

#### Vantagens

* Implementação simples.
* Menor complexidade arquitetural.

#### Desvantagens

* Baixa tolerância a falhas.
* Propagação rápida de indisponibilidade.

### Alternativa 2 – Retry Simples

#### Vantagens

* Fácil implementação.
* Recuperação automática de falhas transitórias.

#### Desvantagens

* Pode amplificar sobrecargas.
* Não evita falhas em cascata.

### Alternativa 3 – Circuit Breaker + Retry + Fallback

#### Vantagens

* Evita sobrecarga em serviços indisponíveis.
* Reduz falhas em cascata.
* Permite continuidade operacional.

#### Desvantagens

* Maior complexidade.
* Necessidade de monitoramento adicional.

## Decisão

Adotar os seguintes padrões de resiliência:

* API Gateway;
* Circuit Breaker;
* Retry com Exponential Backoff;
* Fallback;
* Dead Letter Queue (DLQ).

## Justificativa

O padrão Circuit Breaker impede que serviços continuem enviando requisições para dependências indisponíveis.

Quando uma integração externa apresentar falhas consecutivas, o circuito será aberto e respostas alternativas serão fornecidas através de mecanismos de fallback.

Para comunicação assíncrona, mensagens que excederem o limite de tentativas serão direcionadas para Dead Letter Queues para posterior análise e reprocessamento.

## Trade-offs

### Benefícios

* Maior disponibilidade.
* Redução de falhas em cascata.
* Melhor experiência do usuário.
* Recuperação controlada de erros.

### Custos

* Complexidade adicional.
* Maior esforço de observabilidade.
* Necessidade de monitoramento dos circuitos.

## Consequências

Mesmo em cenários de indisponibilidade parcial, o sistema continuará fornecendo funcionalidades essenciais, preservando a continuidade operacional da plataforma.

## Referências

* Nygard, Michael. Release It!
* Richards, Mark; Ford, Neal. Fundamentals of Software Architecture.
* AWS Well-Architected Framework.
