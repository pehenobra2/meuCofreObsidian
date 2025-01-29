## 1. O que é❓

O conceito ACID garante que as transações no banco de dados sejam confiáveis, mesmo em caso de falhas. Vamos entender cada princípio:
### 1.1. Atomicidade

**Atomicidade** significa uma transação que deve ter **TUDO OU NADA**:
- **Se tudo der certo** ▶️ As mudanças são confirmadas (`COMMIT`).
- **Se algo der errado** ▶️ As mudanças são desfeitas (`ROLLBACK`). 
Isso impede que o banco de dados fique em um estado inconsistente, protegendo os dados contra falhas inesperadas.

**Exemplo**: Transferência bancária
- Débito na conta A
- Crédito na conta B
Se o crédito falhar, o débito é desfeito para evitar inconsistências.

---

### 1.2. Consistência

A consistência garante que o banco de dados passe de um estado válido para outro estado válido, sem quebrar regras de integridade.

- **Todas as restrições e Validações são respeitadas.
- **Se uma violação ocorrer, a transação falha e o banco não sofre alterações**.

**Exemplo**:
Se um campo `idade INT CHECK (idade >= 18)` for violado ao inserir um valor `idade=15`, a transação será automaticamente rejeitada.

---

### 1.3. Isolamento

O isolamento garante que transações concorrentes não interfiram umas nas outras, preservando a integridade dos dados.

Diferentes níveis de isolamento:
1. **Read Uncommitted**: Uma transação pode ver dados ainda não confirmados por outra (⚠️ inseguro).
2. **Read Committed**: Só permite leitura de dados já confirmados (✅ seguro).
3. **Repeatable Read**: Garante que os dados lidos não mudam durante a transação.
4. **Serializable**: O nível mais seguro, evitando qualquer interferência entre transações.

**Exemplo**: 
Dois usuários editando o mesmo pedido de compra simultaneamente. O isolamento impede que um veja os dados parcialmente alterados pelo outro.

---

### 1.4. Durabilidade

A durabilidade assegura que, uma vez confirmada, a transação será armazenada permanentemente, mesmo em caso de falha do sistema (queda de energia, falha no servidor, etc).

- **Os dados são gravados de forma permanente.**
- **Recuperação garantida após falhas**.

**Exemplo**:
Apos um `COMMIT`, mesmo que o servidor reinicie inesperadamente, as informações já gravadas permanecerão intactas.

---