Os **Records** foram introduzidos no **Java 14** (como preview) e tornaram-se estáveis no **Java 16**. Eles foram criados para reduzir o **boilerplate** (código repetitivo) de classes simples que armazenam dados, como **DTOs (Data Transfer Objects)**.

## 1. O que são Records?

Os **Records** são uma forma **concisa e imutável** de representar um conjunto de dados.  
Eles automaticamente fornecem:

- Um **construtor compacto**  
- Métodos **getter** para os campos  
- Implementações de **equals(), hashCode() e toString()**

**Exemplo de Record:**
```java
public record Produto(String nome, double preco) {}
```

---

## 2. Comparação: Classe Tradicional vs. Record


**Classe Tradicional (Antes do Java 16)**
```java
public final class Produto {
    private final String nome;
    private final double preco;

    public Produto(String nome, double preco) {
        this.nome = nome;
        this.preco = preco;
    }

    public String getNome() { return nome; }
    public double getPreco() { return preco; }

    @Override public boolean equals(Object o) { ... }
    @Override public int hashCode() { ... }
    @Override public String toString() { ... }
}
```

**Mesma Implementação com Record (Java 16+)**
```java
public record Produto(String nome, double preco) {}
```

---

## 3. Características importantes dos Records

### 3.1. Imutabilidade

Os atributos dos **Records** são **implicitamente finais**, ou seja, não podem ser modificados após a criação.
```java
Produto p = new Produto("Celular", 1500.00);
p.preco = 2000.00; // ❌ ERRO: Não é possível modificar o campo
```

**Isso os torna ideias para DTOs, eventos e objetos de valor.**

### 3.2. Métodos Gerados Automaticamente

Os Records geram automaticamente métodos úteis:
```java
Produto p = new Produto("Celular", 1500.00);
System.out.println(p.nome()); // "Celular"
System.out.println(p.preco()); // 1500.0
System.out.println(p); // Produto[nome=Celular, preco=1500.0]
```

### 3.3. Construtores Personalizados

Os Records permitem definir construtores compactos sem precisar reatribuir os campos.
```java
public record Produto(String nome, double preco) {
    public Produto {
        if (preco < 0) {
            throw new IllegalArgumentException("Preço não pode ser negativo");
        }
    }
}
```

Esse código verifica se o preço é negativo sem precisar da atribuição explícita (`this.preco = preco;`).

### 3.4. Métodos Customizados

Os Records podem ter métodos adicionais para cálculo ou transformação de dados.
```Java
public record Produto(String nome, double preco) {
    public double aplicarDesconto(double percentual) {
        return preco - (preco * percentual / 100);
    }
}
```

```java
Produto p = new Produto("Celular", 1500.00);
System.out.println(p.aplicarDesconto(10)); // 1350.0

```

Apenas os atributos continuam imutáveis, mas métodos adicionais podem ser definidos!

### 3.5. Implementando interfaces

Os Records podem implementar **interfaces**, mas não podem estender classes.
```java
public interface Desconto {
    double aplicarDesconto(double percentual);
}

public record Produto(String nome, double preco) implements Desconto {
    @Override
    public double aplicarDesconto(double percentual) {
        return preco - (preco * percentual / 100);
    }
}
```

Ótima abordagem para objetos de domínio que precisam de comportamento específico!

### 3.6. Herança e Records

Os Records são **implicitamente finais**, então **NÃO podem ser estendidos**.
```java
public record Produto(String nome, double preco) {} 

public class Eletronico extends Produto {} // ❌ ERRO: Records não podem ser estendidos!
```

Se precisar de uma estrutura hierárquica, considere usar [[Sealed Classes|Sealed Classes!]]

### 3.7. Records e JSON (Jackson/Gson)

Os Records funcionam muito bem com bibliotecas de serialização como **Jackson** e **Gson**, facilitando a conversão para JSON.

**Exemplo com Jackson:**
```java
import com.fasterxml.jackson.databind.ObjectMapper;

public class TesteRecordJson {
    public static void main(String[] args) throws Exception {
        ObjectMapper mapper = new ObjectMapper();

        Produto p = new Produto("Celular", 1500.00);
        String json = mapper.writeValueAsString(p);
        System.out.println(json); // {"nome":"Celular","preco":1500.0}

        Produto p2 = mapper.readValue(json, Produto.class);
        System.out.println(p2); // Produto[nome=Celular, preco=1500.0]
    }
}
```

---

