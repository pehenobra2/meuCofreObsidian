
Jakarta EE (Java Platform, Enterprise Edition) é uma plataforma para o desenvolvimento de aplicações empresariais em Java, oferecendo um conjunto de especificações que auxiliam na criação de sistemas distribuídos, escaláveis e seguros.

---

## 1. Principais Componentes e Características ✨

### 1.1 APIs e Especificações 

- **Servlets**: Processamento de requisições HTTP e geração de respostas para aplicações web.
- **EJB (Enterprise JavaBeans)**: Componentes para lógica de negócios, com suporte a transações e segurança.
- **[[JPA]] (Java Persistence API)**: Integração com banco de dados relacionais, mapeando objetos Java para tabelas de banco de dados.
- **JMS (Java Message Service)**: Comunicação assíncrona entre sistemas através de mensagens.
- **JAX-RS (Java API for RESTful Web Services)**: Facilita a criação de serviços web baseados em REST.

### 1.2 Containers e Servidores de Aplicação

- Servidores que implementam a especificação Java EE, gerenciando o ciclo de vida das aplicações.
	- Exemplos: **WildFly, GlassFish, Payara.**

---

## 2. Arquitetura Típica de Aplicações Java EE 🏗️

### 2.1 Camadas Principais

- **Camada de Apresentação**: Servlets ou JSP para gerar a interface do usuário.
- **Camada de Negócio**: EJBs, que contêm a lógica empresarial.
- **Camada de Persistência**: [[JPA]], que interage com o banco de dados.
- **Camada de Integração**: API para integração com os outros sistemas (ex: JMS ou JCA).

---

## 3. Principais recursos do Java EE⚡

### 3.1 Controle de Transações

- Transações distribuídas e locais, com gerenciamento simplificado.

### 3.2 Segurança

- Suporte a autenticação, autorização e criptografia.
- Integração com sistemas externos de segurança.

---

## 4. Vantagens do Java EE 🔺

- **Portabilidade**: Pode ser executado em qualquer servidor que implemente a especificação Java EE.
- **Escalabilidade**: Ideal para sistemas de alta demanda, como aplicações corporativas.
- **Desempenho**: Otimizado para desempenho em grandes volumes de dados e usuários simultâneos.
- **Segurança**: Oferece mecanismos de segurança integrados para proteger as aplicações.

---

## 5. Evolução de Java EE para Jakarta EE 🆙

Em 2017, Java EE passou a ser gerido pela Eclipse Foundation e foi renomeado para Jakarta EE. Por isso, a plataforma foi renomeada para **Jakarta EE**.

### 5.1 Impacto da Mudança

- **Pacotes de nomes**: Uma das maiores mudanças visíveis para os desenvolvedores foi a migração de todos os pacotes de código da plataforma, que antes usavam o prefixo `javax`, para o prefixo `jakarta`. Por exemplo, a API de Persistência passou a ser chamada de Jakarta Persistence ao invés de Java Persistence API (JPA).
- **Continuidade**: Apesar da mudança de nome e da governança, as especificações de Jakarta EE mantiveram compatibilidade com o que já era implementado no Java EE, garantindo que as aplicações existentes continuassem a funcionar com as versões mais recentes da plataforma, embora seja necessário ajustar alguns detalhes do código, como a troca de pacotes.

---
