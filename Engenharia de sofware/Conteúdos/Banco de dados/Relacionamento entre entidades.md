Os relacionamentos entre entidades são definidos através de anotações que especificam como as entidades estão associadas entre si. Existem 4 tipos principais de relacionamento entre entidades:
### 1. **Um para um**

Um relacionamento **"Um para um"** significa que uma entidade está relacionada a apenas uma instância de outra entidade. 

#### 1.1 Exemplo

Uma entidade `Pessoa` pode ter um único passaporte, e um passaporte pertence a uma única pessoa.
```java
@Entity
public class Pessoa {
    @Id
    private Long id;
    
    private String nome;
    
    @OneToOne
    private Passaporte passaporte;
    
    // Getters e Setters
}

@Entity
public class Passaporte {
    @Id
    private Long id;
    
    private String numero;
    
    @OneToOne(mappedBy = "passaporte")
    private Pessoa pessoa;
    
    // Getters e Setters
}
```
**Explicação**:
- A anotação `@OneToOne` estabelece um relacionamento um para um entre `Pessoa` e `Passaporte`.
- No lado de `Passaporte`, usamos `mappedBy` para definir que o lado proprietário do relacionamento é a classe `Pessoa`.

---

### 2. **Um para muitos**

Um relacionamento **"Um para muitos"** significa que uma instância de uma entidade pode estar associada a múltiplas instâncias de outra entidade.

#### 2.1 Exemplo

Uma categoria pode ter múltiplos produtos, mas um produto pertence a apenas uma categoria.
```java
@Entity
public class Categoria {
    @Id
    private Long id;
    
    private String nome;
    
    @OneToMany(mappedBy = "categoria")
    private List<Produto> produtos;
    
    // Getters e Setters
}

@Entity
public class Produto {
    @Id
    private Long id;
    
    private String nome;
    
    @ManyToOne
    @JoinColumn(name = "categoria_id")
    private Categoria categoria;
    
    // Getters e Setters
}
```
**Exemplo**:
- A anotação `@OneToMany` estabelece que uma `Categoria` pode ter vários `Produto`.
- O lado não proprietário (`Produto`) possui uma referência para o lado proprietário (`Categoria`) com a anotação `@ManyToOne`.
- `mappedBy` define que o relacionamento é mapeado pelo atributo `categoria` da classe `Produto`.
- `@JoinColumn` é usado no lado `Produto` para especificar a coluna que estabelece o vínculo entre as tabelas (a chave estrangeira).

---

### 3. **Muitos para um**

O relacionamento **"Muitos para um"** é o oposto do **"Um para muitos"**. Ele define que múltiplas instâncias de uma entidade podem estar associadas a uma instância de outra entidade.

#### 3.1 Exemplo

Vários produtos podem pertencer a uma categoria.
```java
@Entity
public class Produto {
    @Id
    private Long id;
    
    private String nome;
    
    @ManyToOne
    @JoinColumn(name = "categoria_id")
    private Categoria categoria;
    
    // Getters e Setters
}
```
**Explicação**:
- `@ManyToOne` define que muitos `Produto` podem ter uma `Categoria`.
- A anotação `@JoimColumn` define a coluna de chave estrangeira no banco de dados, que vincula `Produto` à `Categoria`.

---

### 4. **Muitos para muitos** 

Um relacionamento **"Muitos para muitos"** define que múltiplas instâncias de uma entidade podem estar associadas a múltiplas instâncias de outra entidade.

#### 4.1 Exemplo

Estudantes podem estar matriculados em várias matérias, e matérias podem ter vários estudantes.
```java
@Entity
public class Estudante {
    @Id
    private Long id;
    
    private String nome;
    
    @ManyToMany
    @JoinTable(
        name = "estudante_materia", 
        joinColumns = @JoinColumn(name = "estudante_id"), 
        inverseJoinColumns = @JoinColumn(name = "materia_id")
    )
    private List<Materia> materias;
    
    // Getters e Setters
}

@Entity
public class Materia {
    @Id
    private Long id;
    
    private String nome;
    
    @ManyToMany(mappedBy = "cursos")
    private List<Estudante> estudantes;
    
    // Getters e Setters
}
```
**Explicação**:
- `@ManyToMany` define o relacionamento muitos para muitos entre `Estudante` e `Materia`.
- A anotação `@JoinTable` define a tabela de junção que mantém as relações entre as duas entidades. Ela especifica as colunas de chave estrangeira (`estudante_id` e `materia_id`).
- `mappedBy` é usado no lado da `Materia` para indicar que o mapeamento do relacionamento é feito através da entidade `Estudante`.


### 5. Considerações Importantes

1. Chaves estrangeiras e tabelas de junção
	1. `@OneToMany` e `@ManyToOne` geralmente envolvem uma chave estrangeira no lado do `MANY`.
	2. `@ManyToMany` envolve uma tabela de junção, que armazena as chaves estrangeiras de ambas as entidades.
2. Cascading
	1. O cascading pode ser configurado para realizar operações em cascata (como persistir, remover) em entidades relacionadas.
	2. Exemplo: `@OneToMany(cascade = CascadeType.ALL)` faz com que, ao persistir a `Categoria`, os produtos associados também sejam persistidos.
3. Relacionamento Unidrecional vs Bidirecional
	1. Unidirecional é quando a relação é referenciada apenas de um lado.
	2. Bidirecional é quando a relação é referenciada dos dois lados, o que permite navegar entre as entidades em ambas as direções.