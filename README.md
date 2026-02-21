# Mini Projeto "O Arquiteto Decisor" (v4)

**Aluno:** Amábile Honorato Zucchetti\
**Matrícula:** 2310438\
**Link Repositório GitHub (Scaffolding):** `https://github.com/amabilee/logistack-arquitetura`

---

## CICLO 1: Visão e Requisitos (Fase 1)
*Preencher e entregar no AVA ao final do Ciclo 1.*

### 1.1 Resumo do Cenário de Negócio
O LogiTrack é um sistema voltado para a modernização das operações de uma empresa de logística, com foco na otimização de rotas e no gerenciamento eficiente de entregas. O problema central é a dificuldade em lidar com grandes volumes de dados geolocalizados e mudanças em tempo real, como trânsito, atrasos e falhas de comunicação. A arquitetura visa suportar o processamento contínuo dessas informações para melhorar a tomada de decisão operacional. Os principais usuários do sistema são gestores logísticos, motoristas da frota e equipes de operação. O sistema também integra serviços externos de mapas e sistemas internos de estoque. O objetivo de negócio é reduzir custos operacionais, aumentar a eficiência das entregas e melhorar a previsibilidade de chegada, garantindo alta performance, escalabilidade e resiliência da solução.

### 1.2 Atributos de Qualidade (RNFs) Priorizados

1.  **Performance:** A performance é um requisito essencial para o LogiTrack, pois o sistema precisa processar dados de localização e recalcular rotas em tempo real. Caso as respostas sejam lentas, decisões operacionais importantes podem ser tomadas com base em informações desatualizadas. Do ponto de vista técnico, é necessário garantir baixa latência no processamento e na comunicação entre os serviços envolvidos.
2.  **Escalabilidade:** A escalabilidade é importante para permitir que o sistema suporte o aumento do número de veículos, entregas e usuários sem perda significativa de desempenho. Como a empresa de logística pode crescer ao longo do tempo, a arquitetura deve permitir a expansão dos recursos de forma gradual, principalmente no processamento de dados geolocalizados.
3.  **Resiliência:** A resiliência é um requisito prioritário devido à dependência de serviços externos, como APIs de mapas, e à instabilidade de redes de comunicação. O sistema deve continuar operando mesmo quando ocorrerem falhas parciais, evitando a interrupção total das operações logísticas. Arquiteturalmente, isso exige mecanismos de tolerância a falhas e recuperação automática.
4.  **Confiabilidade:** A confiabilidade garante que as informações fornecidas pelo sistema, como status das entregas e previsões de chegada, sejam corretas e consistentes. Dados incorretos podem causar atrasos, retrabalho e decisões equivocadas por parte dos gestores. Portanto, o sistema deve garantir integridade e consistência das informações processadas.
5.  **Manutenibilidade:** A manutenibilidade é relevante para facilitar futuras evoluções do sistema, como melhorias nos algoritmos de otimização de rotas ou integração com novos serviços. Uma arquitetura bem estruturada e modular reduz o impacto de mudanças e facilita a correção de falhas, o que é importante para a manutenção contínua da solução.

### 1.3 Diagrama de Contexto (C4 Nível 1)
[Insira aqui a imagem do seu Diagrama de Contexto (C4 Nível 1). Este diagrama deve mostrar o sistema como uma caixa preta e suas interações com usuários e outros sistemas externos. **Recomendado: Salvar o diagrama em `/diagrams` no GitHub e referenciar o link da imagem aqui.**]

### 1.4 Classificação da Estratégia
-   **Classificação:** [Conservadora / Balanceada / Ousada]
-   **Justificativa:** [Explique em 5 linhas o porquê desta escolha em relação ao risco, inovação e maturidade tecnológica. Referencie o Capítulo 1 do Pressman sobre a natureza do software, se pertinente].

---

## CICLO 2: Blueprint e Decisões (Fase 2)
*Preencher e entregar no AVA ao final do Ciclo 2.*

### 2.1 Diagrama de Containers (C4 Nível 2)
[Insira aqui a imagem do seu Diagrama de Containers (C4 Nível 2). Este diagrama deve detalhar a estrutura interna do sistema, mostrando os principais containers (aplicações, bancos de dados, filas, etc.) e suas interações. **Recomendado: Salvar o diagrama em `/diagrams` no GitHub e referenciar o link da imagem aqui.**]

### 2.2 Estilo Arquitetural Escolhido
[Descreva o estilo arquitetural principal que você adotou (ex: Microsserviços, Monolito Modular, Hexagonal, Event-Driven) e justifique sua escolha com pelo menos 3 trade-offs reais (prós e contras) em relação aos RNFs priorizados na Fase 1. Referencie o Capítulo 14 do Pressman sobre estilos arquiteturais, se pertinente].

### 2.3 Architecture Decision Record (ADR) Principal
[Escolha uma decisão arquitetural crucial que você tomou nesta fase (ex: Escolha da Tecnologia de Persistência, Estratégia de Comunicação entre Microsserviços) e documente-a como um ADR. **Recomendado: Criar o arquivo `.md` do ADR em `/adrs` no GitHub e referenciar o link aqui.**]
-   **Título:** [Ex: Escolha da Tecnologia de Persistência]
-   **Contexto:** [O problema ou necessidade técnica que levou a essa decisão. Qual era o cenário?]
-   **Decisão:** [O que foi decidido. Qual tecnologia/abordagem foi escolhida?]
-   **Justificativa:** [Por que esta opção venceu as alternativas? Quais foram os trade-offs considerados? Quais os impactos nos RNFs?]

---

## CICLO 3: Cloud e Resiliência (Fase 3)
*Preencher e entregar no AVA ao final do Ciclo 3.*

### 3.1 Estratégia de Cloud e Implantação
[Descreva como sua arquitetura será implantada em um ambiente de nuvem (ex: AWS, Azure, GCP). Qual o modelo de serviço (IaaS, PaaS, Serverless)? Como o sistema será escalado e monitorado?]

### 3.2 Análise de Fragilidade e Mitigação
-   **Ponto Frágil:** [Identifique a maior fraqueza ou risco da sua arquitetura em um cenário de produção (ex: falha de um serviço crítico, pico de tráfego inesperado, vulnerabilidade de segurança).]
-   **Mitigação:** [Como você minimizaria esse risco? Quais estratégias de resiliência (ex: circuit breaker, retry, fallback, multi-região) seriam aplicadas?]

### 3.3 Parecer Técnico Final
[Resumo executivo (até 10 linhas) defendendo por que sua arquitetura é a melhor escolha para o cliente, considerando os requisitos de negócio, os RNFs e a estratégia de implantação. Qual o valor agregado da sua solução?]

---

## BÔNUS: Evolução Arquitetural (Gamificação)
*Opcional - Preencher apenas se houver melhoria estrutural documentada no GitHub.*

[Descreva brevemente a melhoria arquitetural que você implementou no seu repositório GitHub para fins de bônus de nota. Referencie a nova ADR e o diagrama atualizado (se houver) no GitHub. Ex: Migração de um componente para Serverless, implementação de um padrão de resiliência, otimização de custo em cloud. **Lembre-se: a melhoria deve ser arquitetural, não apenas textual.**]

---

## Referências Bibliográficas
-   **Pressman, R. S.** (2021). *Engenharia de Software: Uma Abordagem Profissional*. McGraw Hill. (Capítulos selecionados conforme o tema da aula).
-   **Richards, M., & Ford, N.** (2020). *Fundamentals of Software Architecture: An Engineering Approach*. O'Reilly Media.
-   **C4 Model for Software Architecture.** (s.d.). Disponível em: [https://c4model.com/](https://c4model.com/)
-   **Architecture Decision Records (ADRs).** (s.d.). Disponível em: [https://adr.github.io/](https://adr.github.io/)