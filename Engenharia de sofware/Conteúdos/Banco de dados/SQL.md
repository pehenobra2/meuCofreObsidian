## 1. Intrução ao SQL

### 1.1. O que é SQL?

- SQL é a linguagem usada para manipular bancos de dados relacionais.
- Funciona em diferentes sistemas de bancos de dados, como [[Oracle]], MySQL, SQL Server e PostgresSQL.

### 1.2. Estrutura do SQL

- **DDL (Data Definition Language)**: Comandos que definem a estrutura do banco de dados.
	- `CREATE`, `ALTER`, `DROP`
- **DML (Data Manipulation Language)**: Comandos que manipulam os dados do banco.
	- `INSERT`, `UPDATE`, `DELETE`
- **DQL (Data Query Language)**: Comandos usados para consultar os dados.
	- `SELECT`
- **DCL (Data Control Language)**: Comandos para controle de permissões.
	- `GRANT`, `REVOKE`
- **TCL (Transaction Control Language)**: Comandos que controlam transações.
	- `COMMIT`, `ROLLBACK`

---

## 2. Criando e Gerenciando Tabelas

### 2.1. Criando um Banco de Dados e Usuário
 
```sql
CREATE USER meu_usuario IDENTIFIED BY senha;
GRANT CONNECT, RESOURCE TO meu_usuario;
```

### 2.2. Criando uma Tabela

```sql
CREATE TABLE clientes (
    id_cliente NUMBER PRIMARY KEY,
    nome VARCHAR2(100),
    email VARCHAR2(100) UNIQUE,
    data_nascimento DATE
);
```

### 2.3. Alterando e Excluindo Tabelas

```sql
ALTER TABLE clientes ADD telefone VARCHAR2(15);
DROP TABLE clientes;
```

--- 

## 3. Manipulação de Dados (DML)

### 3.1. Inserindo Dados

```sql
INSERT INTO clientes (id_cliente, nome, email, data_nascimento) 
VALUES (1, 'João Silva', 'joao@email.com', TO_DATE('1990-05-15', 'YYYY-MM-DD'));
```

### 3.2. Atualizando Dados

```sql
UPDATE clientes SET email = 'joao.silva@email.com' WHERE id_cliente = 1;
```

### 3.3. Deletando Dados

```sql
DELETE FROM clientes WHERE id_cliente = 1;
```

---

## 4. Consultando com SELECT (DQL)

### 4.1. Seleção Simples

```sql
SELECT * FROM clientes;
SELECT nome, email FROM clientes;
```

### 4.2. Filtros com `WHERE`

```sql
SELECT * FROM clientes WHERE nome = 'Maria';
SELECT * FROM clientes WHERE data_nascimento > TO_DATE('2000-01-01', 'YYYY-MM-DD');
```

### 4.3. Ordenação com `ORDER BY`

```sql
SELECT * FROM clientes ORDER BY nome ASC;
```

### 4.4. Limitar resultados com `ROWNUM`

```sql
SELECT * FROM clientes WHERE ROWNUM <= 5;
```

---

## 5. Funções Agregadas e Agrupamento

### 5.1. Funções Agregadas

As funções agregadas são utilizadas para calcular valores estatísticos a partir dos dados de uma tabela.

- `COUNT`: Conta o número de registros.
- `AVG`: Calcula a média dos valores de uma coluna numérica.
- `MAX`: Retorna o maior valor de uma coluna.
- `MIN`: Retorna o menor valor de uma coluna.

```sql
SELECT COUNT(*) FROM clientes; -- Conta o número total de registros na tabela
SELECT AVG(salario) FROM funcionarios; -- Calcula a média dos salários
SELECT MAX(salario), MIN(salario) FROM funcionarios; -- Retorna o maior e o menor salário
```

### 5.2. Agrupamento com `GROUP BY`

- `GROUP BY`: Permite agrupar os dados com base em uma ou mais colunas e aplicar funções agregadas.

```sql
SELECT cidade, COUNT(*) FROM clientes GROUP BY cidade;
```
Esse comando retorna a quantidade de clientes por cidade, agrupando os registros e contando quantos clientes existem em cada cidade.

### 5.3. Filtrando Grupos com `HAVING`

- `HAVING`: Diferente do `WHERE`, quer filtra registros individuais, o `HAVING` é usado para filtrar grupos de dados após a agregação.

```sql
SELECT cidade, COUNT(*) FROM clientes GROUP BY cidade HAVING COUNT(*) > 10;
```
Esse comando retorna apenas as cidades que possuem mais de 10 clientes cadastrados.

---

## 6. Junções (Joins) 

Joins são usados para combinar dados de duas ou mais tabelas com base em uma condição de relacionamento. O `INNER JOIN` é o tipo mais comum.

### 6.1. INNER JOIN

Retorna apenas os registros que possuem correspondência nas duas tabelas.
```sql
SELECT clientes.nome, pedidos.valor
FROM clientes
INNER JOIN pedidos ON clientes.id_cliente = pedidos.id_cliente;
```

### 6.2. LEFT JOIN (ou LEFT OUTER JOIN)

Retorna todos os registros da tabela à esquerda e os dados correspondentes da tabela à direita. Se não houver correspondência, os resultados da tabela à direita serão `NULL`.
```sql
SELECT clientes.nome, pedidos.valor
FROM clientes
LEFT JOIN pedidos ON clientes.id_cliente = pedidos.id_cliente;
```

### 6.3. RIGHT JOIN (ou RIGHT OUTER JOIN)

Retorna todos os registros da tabela à direita e os dados correspondentes da tabela à esquerda.
```sql
SELECT clientes.nome, pedidos.valor
FROM clientes
RIGHT JOIN pedidos ON clientes.id_cliente = pedidos.id_cliente;
```

### 6.4. FULL JOIN

Retorna todos os registros quando há uma correspondência em qualquer uma das tabelas.
```sql
SELECT clientes.nome, pedidos.valor
FROM clientes
FULL OUTER JOIN pedidos ON clientes.id_cliente = pedidos.id_cliente;
```

---

## 7. Subqueries

Uma subquery é uma consulta dentro de outra consulta. Elas são usadas para fornecer um valor de pesquisa para a consulta principal.
```sql
SELECT nome 
FROM clientes 
WHERE id_cliente IN (
    SELECT id_cliente 
    FROM pedidos 
    WHERE valor > 1000
);
```
Neste caso, a subquery seleciona os `id_cliente` que possuem pedidos com valor maior que 1000, e a consulta externa retorna os nome desse clientes.

---

## 8. Views

Uma View é uma consulta salva como um objeto no banco de dados, facilitando consultas frequentes.
```sql
CREATE VIEW clientes_ativos AS 
SELECT * FROM clientes WHERE status = 'Ativo';
```
Essa consulta é utilizada para listar apenas os clientes cujo status está marcado como "Ativo".

---

## 9. Procedures

Procedures são blocos de código armazenados que podem ser executados sob demanda.

```sql
CREATE OR REPLACE PROCEDURE atualizar_email (p_id_cliente NUMBER, p_novo_email VARCHAR2) AS
BEGIN
    UPDATE clientes SET email = p_novo_email WHERE id_cliente = p_id_cliente;
END;
```
Essa procedure recebe um ID de cliente e um novo email como parâmetros e atualiza o email do cliente correspondente na tabela.

---

## 10. Trigger

Triggers são blocos de código que são acionados automaticamente em resposta a eventos em uma tabela.

```sql
CREATE OR REPLACE TRIGGER trg_log_insert
AFTER INSERT ON clientes
FOR EACH ROW
BEGIN
    INSERT INTO log_clientes (id_cliente, data_log) 
    VALUES (:NEW.id_cliente, SYSDATE);
END;
```
Esse trigger é acionado automaticamente após a inserção de um novo registro na tabela `clientes`, adicionando um log com o ID do cliente e a data da inserção na tabela `log_clientes`.

---
