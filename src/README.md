# LogiTrack - Código Fonte

## Objetivo

Esta pasta contém os componentes responsáveis pela implementação da plataforma LogiTrack.

---

## Arquitetura da Aplicação

A aplicação segue uma arquitetura baseada em microsserviços e comunicação orientada a eventos.

Principais serviços:

* API Gateway
* Route Service
* Tracking Service
* Notification Service

---

## Tecnologias

### Backend

* Java / Spring Boot
* Spring Cloud Gateway
* RabbitMQ
* PostgreSQL

### Infraestrutura

* Docker
* Docker Compose

---

## Comunicação

### Síncrona

* REST API
* HTTP/HTTPS

### Assíncrona

* RabbitMQ
* Eventos de domínio

Exemplos:

* NovaLocalizacaoRecebida
* RotaAtualizada
* EntregaConcluida

---

## Persistência

Banco de dados relacional PostgreSQL.

---

## Execução Local

```bash
docker compose up
```

---

## Observabilidade

Planejado para utilização de:

* CloudWatch
* Logs centralizados
* Métricas
* Monitoramento de filas

---

## Segurança

* HTTPS
* JWT
* Controle de acesso baseado em papéis

---

## Estrutura

```text
src/
├── gateway/
├── route-service/
├── tracking-service/
├── notification-service/
└── shared/
```
