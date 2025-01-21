**Atomicidade** significa uma transação que deve ter **TUDO OU NADA**:
- **Se tudo der certo** ▶️ As mudanças são confirmadas (`COMMIT`).
- **Se algo der errado** ▶️ As mudanças são desfeitas (`ROLLBACK`). 
Isso impede que o banco de dados fique em um estado inconsistente, protegendo os dados contra falhas inesperadas.