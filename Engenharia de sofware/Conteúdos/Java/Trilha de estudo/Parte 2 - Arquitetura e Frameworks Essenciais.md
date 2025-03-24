
**Objetivo: Aprender a desenvolver aplicações escaláveis com Java e Spring**

## Conteúdos:

- [ ] Spring boot - Fundamentos, Dependency Injection, Beans.
- [ ] JPA/Hibernate - Estratégias de mapeamento, Lazy vs Eager Loading
- [ ] API REST e GraphQL - Construção, versionamento, boas práticas.
- [ ] Mensageria - RabbitMQ, Kafka, Event-driven architecture.
- [ ] Autenticação & Segurança - Spring Security, JWT, OAuth2.

## Prática: Melhorando o Projeto MinhasFinanças com Arquitetura Escalável

Para aplicar os conceitos avançados de escalabilidade com **Spring Boot**, a melhor abordagem é expandir o **MinhasFinanças**, tornando-o mais robusto e pronto para um grande volume de usuários. Aqui estão algumas melhorias que irão cobrir todos os conteúdos desta fase:

✅ **🔹 Modularização e Escalabilidade com Spring Boot**

- Refatorar a aplicação para uma **arquitetura em módulos** (ex: módulo de transações, módulo de relatórios, etc.).
- Criar serviços desacoplados, aplicando **Dependency Injection** corretamente.

✅ **🔹 Persistência Otimizada com JPA/Hibernate**

- Melhorar o **Lazy vs. Eager Loading** para evitar problemas de performance.
- Implementar **consultas otimizadas com Criteria API** e **Named Queries**.

✅ **🔹 API REST e GraphQL**

- Melhorar a API REST do projeto, aplicando **versionamento e paginização**.
- Criar um endpoint **GraphQL** para consultas mais flexíveis dos usuários.

✅ **🔹 Mensageria e Event-driven Architecture**

- Integrar **Kafka ou RabbitMQ** para processar transações financeiras de forma assíncrona.
- Implementar um sistema de **notificações financeiras** (ex: quando o saldo estiver abaixo de um limite).

✅ **🔹 Segurança e Autenticação Avançada**

- Implementar **OAuth2 e JWT** para controle de acesso seguro.
- Criar um sistema de **autorização baseada em roles** (Admin, Usuário Padrão, etc.).


🚀 Criar um módulo que gera **relatórios financeiros detalhados** usando **Spring Batch** para processar grandes volumes de dados.  
🚀 Exibir esses relatórios no frontend com **gráficos interativos** em React Native.