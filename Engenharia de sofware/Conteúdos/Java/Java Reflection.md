## 1. O que é?

Refletion é um recurso do Java que permite inspecionar e manipular classes, métodos e atributos em tempo de execução. Com ele, você pode:

- Criar instâncias de classes dinamicamente.
- Acessar atributos e métodos privados.
- Obter informações sobre anotações.
- Chamar métodos sem conhecê-los em tempo de compilação.

---

## 2. Como Refletion funciona no Java?

Refletion opera sobre a metaprogramação, que permite analisar e modificar o código enquanto ele está rodando. Ele funciona por meio da API `java.lang.reflect`.

### 2.1. Obtendo Informações de uma classe

Podemos inspecionar os detalhes de uma classe, como seu nome, métodos, atributos, etc.

``` Java
import java.lang.reflect.*;

class Produto {
    private String nome;
    private double preco;
    
    public Produto(String nome, double preco) {
        this.nome = nome;
        this.preco = preco;
    }

    public void exibir() {
        System.out.println("Produto: " + nome + " - Preço: " + preco);
    }
}

public class ReflexaoExemplo {
    public static void main(String[] args) {
        Class<?> classe = Produto.class; // Obtém a classe
        
        System.out.println("Nome da Classe: " + classe.getName());
        
        System.out.println("\n📌 Métodos:");
        for (Method metodo : classe.getDeclaredMethods()) {
            System.out.println(metodo.getName());
        }

        System.out.println("\n📌 Atributos:");
        for (Field atributo : classe.getDeclaredFields()) {
            System.out.println(atributo.getName());
        }
    }
}
```

Saída:
```
Nome da Classe: Produto

📌 Métodos:
exibir

📌 Atributos:
nome
preco
```

### 2.2. Criando Objetos Dinamicamente

Podemos instanciar objetos sem usar `new`, chamando o construtor via Refletion.
```Java
Constructor<?> construtor = Produto.class.getConstructor(String.class, double.class);
Produto p = (Produto) construtor.newInstance("Celular", 1500.0);
p.exibir();
```

Saída:
```
Produto: Celular - Preço: 1500.0
```

### 2.3. Acessando Atributos Privados

Com Reflection, podemos acessar e modificar atributos privados.

```Java
Produto p = new Produto("Notebook", 3000.0);
Field campoNome = Produto.class.getDeclaredField("nome");
campoNome.setAccessible(true); // Habilita acesso ao atributo privado
campoNome.set(p, "Tablet");

p.exibir();
```

Saída:
```
Produto: Tablet - Preço: 3000.0
```

### 2.4. Chamando Métodos Dinamicamente

Podemos chamar métodos sem saber seus nomes em tempo de compilação.
```Java
Method metodo = Produto.class.getMethod("exibir");
metodo.invoke(p);
```

---

## 3. Como Reflection funciona no Spring?

O Spring usa Reflection intensivamente para fornecer recursos como:

- Injeção de Dependências (`Autowired`)
- Criação de Beans no Spring Context (`@Component`, `Service`)
- Anotações Customizadas (`@Transactional`, `@Cacheable`)
- Proxy Dinâmico (AOP) para interceptação de chamadas

### 3.1. Reflection na injeção de Dependências

Quando você usa:
``` Java
@Service
public class ProdutoService {
    private final ProdutoRepository repository;

    @Autowired
    public ProdutoService(ProdutoRepository repository) {
        this.repository = repository;
    }
}
```

O Spring faz o seguinte por baixo dos panos:
1. Usa Reflection para encontrar classes anotadas com `@Service`.
2. Cria uma instância de `ProdutoService`.
3. Procura o `ProdutosRepository` e injeta dinamicamente no construtor.

### 3.2. Reflection na Serialização (Jackson)

Ao usar DTOs com records e Jackson, como:
```Java
public record ProdutoDTO(String nome, double preco) {}
```

O Jackson usa Reflection para:

- Ler os atributos (`nome`, `preco`) sem precisar de getters/setters.
- Mapear automaticamente JSON 🔁Objeto.

### 3.3. Reflection em AOP (Aspect-Oriented Programming)

Se você usa `Transactional`:
```Java
@Service
public class PedidoService {
    @Transactional
    public void finalizarPedido(Long id) { 
        // código
    }
}
```

O Spring:
1. Cria um proxy da classe `PedidoService` com Reflection.
2. Intercepta chamadas para `finalizarPedido()`.
3. Garante que a transação seja iniciada antes do método e commitada depois.

---