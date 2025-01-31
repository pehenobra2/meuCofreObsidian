
Os bancos de dados são essenciais para armazenar, organizar e gerenciar informações. Dependendo do tipo de aplicação e das necessidades do sistema, diferentes modelos de bancos de dados são utilizados. 

---

## 1. Banco de Dados Relacional

- Baseado no modelo relacional, onde os dados são armazenados em tabelas com linhas e colunas.
- Usa SQL para manipulação de dados.
- Garante integridade e consistência através das regras [[ACID]].

### 1.1. Exemplos

- MySQL
- PostgreSQL
- Oracle Database
- Microsoft SQL Server

### 1.2. Quando usar?

- Sistemas financeiros
- ERPs e CRMs corporativos
- Aplicações que exigem alta consistência

---

## 2. Banco de Dados NoSQL (Não relacional)

- Projetado para escalabilidade e flexibilidade, ideal para grandes volumes de dados.
- Não utiliza SQL tradicional e pode armazenar dados de diferentes formas.

### 2.1. Principais categorias de NoSQL:

- **Document-based**: Armazena dados no formato JSON ou BSON.
	- Exemplo: MongoDB
		- Key-value: Usa chaves únicas para acessar valores associados.
	- Exemplo: Redis
		- Column-Family: Dados organizados em colunas flexíveis, otimizando consultas massivas.
	- Exemplo: Apache Cassandra
		- Graph-Based: Modela dados como grafos, com nós e conexões entre eles.
	- Exemplo: Neo4j

### 2.2. Quando usar?

- Aplicações que exigem alta escalabilidade.
- Big Data e análises avançadas.
- Redes sociais e sistemas de recomendação.

---

## 3. Banco de Dados Hierárquico

- Os dados são organizados em uma estrutura de árvore, com registros "pai" e "filho".
- Muito utilizado em sistemas legados e grandes corporações.
- Exemplo: IBM Information Management System (IMS).

### 3.1. Quando usar?

- Aplicações que exigem navegação estruturada.
- Sistemas bancários antigos.

---

## 4. Banco de dados em Rede

- Expansão do modelo hierárquico, onde cada registro pode ter múltiplos relacionamentos.
- Usado antes do surgimento dos bancos relacionais modernos.
- Exemplo: Integrated Data Store (IDS)
### 4.1. Quando usar?

- Sistemas complexos com relacionamento múltiplos.

---

## 5. Banco de Dados em memória (IMDB - In-Memory Database)

- Os dados são armazenados na RAM, permitindo acesso extremamente rápido.
- Muito usado em sistemas que exigem baixa latência.
- Exemplos:
	- Redis
	- SAP HAHA

### 5.1. Quando usar?

- Sistemas de trading e bolsa de valores.
- Cache de dados para acelerar aplicações

---

## 6. Banco de Dados Distribuído

- Os dados são armazenados em vários servidores distribuídos geograficamente.
- Garante alta disponibilidade e escalabilidade.
- Exemplos: 
	- Google Spanner
	- Amazon DynamoDB

### 6.1. Quando usar?

- Sistemas globais
- Aplicações que precisam de alta redundância e tolerância a falhas

---

## 7. Conclusão

Cada tipo de banco de dados tem suas vantagens e desvantagens. A escolha ideal depende do tipo de aplicação e dos requisitos do sistema.

- **Relacional**: Quando a consistência e integridade são essenciais.
- **Não relacional**: Para aplicações que exigem escalabilidade e flexibilidade.
- **Em memória**: Quando a velocidade é prioridade.
- **Distribuído**: Para grandes volumes de dados espalhados pelo mundo.

---


