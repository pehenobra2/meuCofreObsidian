## 1. O que é JPA? 
O **JPA** (Java Persistence API) é uma **especificação** que define como gerenciar dados relacionais em uma JAVA, utilizando o conceito de entidades que são mapeadas para tabelas em um banco de dados. Ele permite que você trabalhe com objetos **JAVA** em vez de escrever [[SQL]] diretamente, usando **ORM (Object-Relational Mapping)**.

---

## 2. Objetivos principais do JPA 🎯

1. Mapear objetos JAVA para tabelas em um banco de dados.
2. Fazer operações de persistência (salvar, atualizar, excluir e buscar) sem precisar de [[SQL]] manual.
3. Abstrair a interação com o banco de dados, tornando o código mais fácil de manter e portável.

---

## 3. Principais Componentes do JPA ⚙️

### 3.1 Entidade (Entity)

Uma classe JAVA mapeada para uma tabela no banco de dados. Exemplo de entidade:
```java
import jakarta.persistence.Entity;
import jakarta.persistence.Id;
import jakarta.persistence.Column;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;

@Entity
public class Usuario {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    @Column(name = "nome")
    private String nome;
    
    @Column(name = "email")
    private String email;

    // Getters e Setters
}
```
**Explicação**:
- `@Entity` marca a classe como entidade JPA, que será mapeada para uma tabela no banco.
- `@Id` indica o campo que será usado como chave primária.
- `@GeneratedValue` controla como o valor da chave primária será gerado.
- `@Column` mapeia um atributo de classe para uma coluna no banco.
- `@OneToMany`, `@ManyToOne`, `@OneToOne`, `@ManyToMany` definem [[Relacionamento entre entidades|relacionamentos entre entidades]]
- A classe `Usuario` é uma entidade, e cada instância dessa classe é uma linha na tabela `usuario` do banco de dados.
- `@GeneratedValue(strategy = GenerationType.IDENTITY)` define que o valor da chave primária `id` será gerado automaticamente pelo banco (geralmente como um autoincremento).

### 3.2 [[EntityManager]]

Interface principal do JPA usada para realizar operações de persistência. Exemplo:
```java
EntityManager em = entityManagerFactory.createEntityManager();
em.getTransaction().begin();
em.persist(usuario);
em.getTransaction().commit();
```

### 3.3 EntityManagerFactory

Fábrica responsável por criar instâncias de `EntityManager`. Ele é criado uma vez por aplicação e deve ser reutilizado para criar os `EntityManagers` necessários. O `EntityManagerFactory` geralmente é obtido a partir de um arquivo de configuração chamado `persistence.xml`.
- `EntityManagerFactory` geralmente é criado uma única vez usado ao longo da aplicação.
**Exemplo de criação de EntityManagerFactory**:
```java
EntityManagerFactory emf = Persistence.createEntityManagerFactory("meuPU");
EntityManager em = emf.createEntityManager();
```
**Explicação**:
- `Persistence.createEntityManagerFactory("meuPU")` ▶️ Cria a fábrica a partir da configuração definida no `persistence.xml`.

### 3.4 Consulta JPQL

[[JPA]] usa JPQL (Java Persistence Query Language), uma linguagem de consulta semelhante ao SQL, mas orientada a objetos. Exemplo:
```java
List<Usuario> usuarios = em.createQuery("SELECT u FROM Usuario u", Usuario.class).setParameter("nome", "João").getResultList();
```
**Explicação**:
- `createQuery("SELECT u FROM Usuario u")` ▶️ Cria uma consulta JPQL que seleciona da entidade `Usuario`.
- `setParameter("nome", "João")` ▶️ Define um parâmetro para o nome do usuário.

### 3.5 Transações

O JPA exige que as operações de persistência sejam realizadas dentro de uma **transação**. Transações são necessárias para garantir a [[ACID#1. O que é❓#1. Atomicidade|atomicidade]], ou seja, se ocorrer um erro, a transação pode ser revertida e os dados do banco ficam consistentes.

- Principais métodos para gerenciar transações:
	- `begin()` ▶️ Inicia a transação.
	- `commit()` ▶️ Confirma a transação.
	- `rollback()` ▶️ Reverte a transação em caso de erro.

**Exemplo de transação**:
```java
EntityManager em = emf.createEntityManager();
em.getTransaction().begin();

Usuario usuario = new Usuario();
usuario.setNome("Maria");
em.persist(usuario);

em.getTransaction().commit();
em.close();
```

---

## 4. Ciclo de vida das Entidades no JPA 🔃

As entidades no JPA podem estar em diferentes estados no seu ciclo de vida:

| Estado    | O que significa?                                                                  |
| --------- | --------------------------------------------------------------------------------- |
| Transient | O objeto existe, mas não está no banco.                                           |
| Managed   | O objeto está no banco e sendo gerenciado pelo `EntityManager`.                   |
| Detached  | O objeto foi desconectado do `EntityManager`, mas ainda existe no banco de dados. |
| Removed   | O objeto foi marcado para remoção no banco de dados.                              |

---

## 5. Principais operações do JPA 

1. **Persistir (Inserir)** :
```java
em.persist(usuario); //Insere o objeto no banco
```
2. **Buscar**:
```java
Usuario usuario = em.find(Usuario.class, 1L); // Busca pelo ID
```
3. **Atualizar (Merge)**:
```java
em.merge(usuario); // Atualiza a entidade no banco
```
4. **Remover**:
```java
em.remove(usuario); // Remove o objeto do banco
```

---

## 6. Vantagens do JPA 🔺

1. **Abstração de SQL**: Não é necessário escrever SQL diretamente, tornando o código mais limpo.
2. **Portabilidade**: Funciona com qualquer banco de dados que suporte JPA, facilitando mudanças de DB.
3. **Facilidade de manutenção**: O código é mais fácil de manter com o uso de objetos Java, ao invés de manipular SQL diretamente.

---

## 7. Desvantagens do JPA 🔻

1. **Curva de aprendizado**: Pode ser mais complexo, especialmente quando se lida com consultas mais avançadas.
2. **Desempenho**: O uso de JPA pode ser mais lento em algumas situações comparado ao SQL puro.

---

