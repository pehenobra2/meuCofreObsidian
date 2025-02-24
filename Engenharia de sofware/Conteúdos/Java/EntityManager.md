## 1. O que é o EntityManager no [[JPA]]❓

O `EntityManager` é a interface principal do **[[JPA|JPA (Java Persistence API)]]** usada para gerenciar as operações do banco de dados, como **inserir**, **atualizar**, **deletar** e **buscar** entidades, em resumo fazer o CRUD.

Ele funciona como uma **ponte** entre o Java e o banco de dados, permitindo interações usando objetos Java ao invés de SQL puro.

---

## 2. Principais Responsabilidades do EntityManager 🎯

1. Gerenciar o ciclo de vida das entidades (persistência, remoção, atualização).
2. Executar consultas JPQL (Java Persistence Query Lenguage) para buscar dados.
3. Gerenciar transações (iniciar, confirmar e desfazer transações).

---

## 3. Como criar um EntityManager 🔨

O `EntityManager` precisa ser criado a partir de um **EntityManagerFactory**, que por sua vez usa o arquivo `persistence.xml` para configurar a conexão com o banco.

### 3.1 Exemplo de criação do EntityManager
```java
import jakarta.persistence.EntityManager;
import jakarta.persistence.EntityManagerFactory;
import jakarta.persistence.Persistence;

public class JPAUtil {
    private static final EntityManagerFactory emf = Persistence.createEntityManagerFactory("meuPU");

    public static EntityManager getEntityManager() {
        return emf.createEntityManager();
    }
}
```
**Explicação**:
- `Persistence.createEntityManagerFactory("meuPU")` ▶️ Cria a fábrica de `EntityManager` com a configuração do `persistence.xml`.
- `getEntityManager()` ▶️ Retorna um novo `EntityManager` pronto para ser usado.

---

## 4. Principais Operações do EntityManager 🔥

Agora, vamos ver como usamos o `EntityManager` para **salvar**, **buscar**, **atualizar** e **deletar** dados no banco.

### 4.1 Inserindo Dados no banco (`persist`)
```java
EntityManager em = JPAUtil.getEntityManager();
Usuario usuario = new Usuario("João", "joao@email.com");

em.getTransaction().begin(); // Inicia transação
em.persist(usuario); // Insere no banco
em.getTransaction().commit(); // Confirma a transação

em.close(); // Fecha o EntityManager

```
**Explicação**:
1. Criamos um novo usuário (`Usuario` é uma entidade [[JPA]]).
2. `em.getTrasactional().begin()` ▶️ inicia a transação.
3. `em.persist(usuario)` ▶️ Adiciona o objeto ao banco.
4. `em.getTransactional().commit()` ▶️ Salva as alterações.
5. `em.close()` ▶️ Fecha o EntityManager.

### 4.2 Buscando dados (`find` e `createQuery`)
```java
EntityManager em = JPAUtil.getEntityManager();

Usuario usuario = em.find(Usuario.class, 1L); // Busca pelo ID
//1L siginifica "Long", 1 significa int e o l indica que o valor deve ser tratado como um long.
System.out.println(usuario.getNome());

em.close();
```
**Explicação**:
- `find(Usuario.class, 1L)` ▶️ Busca um usuário pelo ID. 
- `1L` ▶️ Indica um long

#### 4.2.1 Consulta avançada com JPQL:
```java
List<Usuario> usuarios = em.createQuery("SELECT u FROM Usuario u", Usuario.class).getResultList();
for (Usuario u : usuarios) {
    System.out.println(u.getNome());
}
```
**Explicação**:
- `createQuery("SELECT u FROM Usuario u")` ▶️ Retorna todos os usuários do banco.

### 4.3 Atualizando um registro (`merge`)
```java
EntityManager em = JPAUtil.getEntityManager();

em.getTransaction().begin();
Usuario usuario = em.find(Usuario.class, 1L);
usuario.setEmail("novoemail@email.com"); // Alteração em memória
em.merge(usuario); // Atualiza no banco
em.getTransaction().commit();

em.close();
```
**Explicação**:
- `find(Usuario.class, 1L)` ▶️ Busca o usuário pelo ID.
- `usuario.setEmail()` ▶️ Altera os dados.
- `merge(usuario)` ▶️ Atualizando no banco.

### 4.4 Removendo um registro (`remove`)
```java
EntityManager em = JPAUtil.getEntityManager();

em.getTransaction().begin();
Usuario usuario = em.find(Usuario.class, 1L);
em.remove(usuario); // Remove o usuário
em.getTransaction().commit();

em.close();
```
**Explicação**:
- `find(Usuario.class 1L)` ▶️ Busca o usuário pelo ID.
- `remove(usuario)` ▶️ Remove do banco.

---

## 5. Importante: Sempre fechar o EntityManager! ⚠️

O **EntityManager não deve ser usado como [[Design Patterns#1. Singleton |singleton]]**. Sempre abra e feche ele corretamente para evitar problemas de conexão:

### 5.1 Jeito correto
```java
EntityManager em = JPAUtil.getEntityManager();
try {
    em.getTransaction().begin();
    // Operações no banco
    em.getTransaction().commit();
} catch (Exception e) {
    em.getTransaction().rollback();
    e.printStackTrace();
} finally {
    em.close();
}
```
**Explicação**:
- `try` ▶️ Executa operações.
- `catch` ▶️ Se der errado, faz `rollback()`.
- `finally` ▶️ Sempre fecha o `EntityManager`.

---

## 6. Resumo Final 🏁

- **EntityManager** gerencia as operações no banco de dados.
- Ele permite **inserir, buscar, atualizar e excluir** registros.
- Sempre precisa estar **dentro de uma transação** (`begin()` e `commit()`).
- **Não esqueça de fechar (`em.close()`) após o uso!**