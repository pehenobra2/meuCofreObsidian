## 1. O que é❓

O Oracle Database é um dos sistemas de gerenciamento de banco de dados (SGBD) mais robustos e populares do mundo, usado por grandes empresas para armazenar, processar e gerenciar grandes volumes de dados de forma segura e eficiente. Ele é um [[Tipos de Banco de Dados#Banco de dados Relacional|banco de dados relacional]] e suporta SQL para manipulação de dados.

---

## 2. Por que usar o Oracle DataBase ✅

1. **Escalabilidade**: Suporta desde pequenos bancos até ambientes corporativos de grande porte.
2. **Alta disponibilidade**: Recursos como Real Application Clusters (RAC) e Data Guard garantem redundância e recuperação rápida.
3. **Segurança Avançada**: Controle de acesso rigoroso, criptografia e auditoria detalhada.
4. **Performance Otimizada**: Indexação avançada, particionamento de tabelas e caching eficiente.
5. **Suporte a Transações**: Garante consistência e integridade dos dados com [[ACID]] ([[ACID#1. Atomicidade|Atomicidade]], [[ACID#2. Consistência|Consistência]], [[ACID#3. Isolamento|Isolamento]] e [[ACID#4. Durabilidade|Durabilidade]]).
6. **Compatibilidade Muilti-Cloud**: Pode ser executado localmente (on-premises) ou na nuvem da Oracle, AWS, Azure e etc.

---

## 3. Como usar o Oracle Database 🏦

### 3.1. Instalação do Oracle Database

Baixar e instalar o Oracle Database no site oficial da Oracle. Algumas versões disponíveis:

- **Oracle Database Express Edition (XE)**: Versão gratuita e leve para testes e aprendizado.
- **Oracle Standard/Enterprise**: Para uso comercial e grandes volumes de dados.

### 3.2. Acessando o Banco de Dados

Depois de instalado, você pode interagir com o Oracle Database por meio de:

- SQL * PLUS: Ferramenta de linha de comando para executar consultas SQL.
- SQL Developer: Interface gráfica da Oracle para gerenciar bancos de dados.
- Toad for Oracle: Ferramenta de terceiros usada para administrar bancos Oracle.

### 3.3. Criando um Banco de Dados

Ao instalar, o Oracle já vem com um banco de dados padrão, mas você pode criar um novo assim:
```sql
CREATE DATABASE meu_banco;
```

### 3.4. Criando uma Tabela e Inserindo Dados

```sql
CREATE TABLE clientes (
    id NUMBER PRIMARY KEY,
    nome VARCHAR2(100),
    email VARCHAR2(100) UNIQUE
);

INSERT INTO clientes (id, nome, email) VALUES (1, 'João Silva', 'joao@email.com');
```

### 3.5. Consultando Dados

```sql
SELECT * FROM clientes WHERE nome = 'João Silva';
```

### 3.6. Atualizando e Excluindo Dados

```sql
UPDATE clientes SET email = 'novo@email.com' WHERE id = 1;
DELETE FROM clientes WHERE id = 1;
```

---

## 4. Conceitos Importantes no Oracle ✨

- **Tablespace**: Particionam o armazenamento dos dados para otimização de performance.
- **PL/SQL** : Linguagem procedural da Oracle que permite criar funções, procedures e triggers.
- **Índices**: Melhoram a velocidade das consultas SQL.
- **Partitioning**: Divide grandes tabelas em partes menores para melhorar a performance.
- **Views**: Consultas armazenadas que funcionam como tabelas virtuais.
- **Triggers**: Automação de ações no banco de dados quando ocorre um evento específico.

---

## 5. Oracle vs Outros Bancos de Dados 🆚

| Características    | Oracle Database | Mysql      | PostgreSQL  | SQL Server   |
| ------------------ | --------------- | ---------- | ----------- | ------------ |
| Licença            | Proprietária    | Open-souce | Open-source | Proprietária |
| Suporte a PL/SQL   | Sim             | Não        | Sim         | Não          |
| Escalabilidade     | Alta            | Média      | Alta        | Alta         |
| Desempenho         | Alto            | Bom        | Alto        | Alto         |
| Segurança avançada | Sim             | Básica     | Avançada    | Avançada     |

---