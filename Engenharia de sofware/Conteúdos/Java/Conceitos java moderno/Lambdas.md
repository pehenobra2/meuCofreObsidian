
As **expressões lambda** foram introduzidas no **Java 8** para permitir a programação funcional no Java. Elas fornecem uma maneira **concisa e expressiva** de passar comportamentos como argumentos para métodos, eliminando a necessidade de classes anônimas verbosas.


## O que são Expressões Lambdas?

Uma expressão lambda é uma função anônima, ou seja, uma função sem nome que pode ser definida diretamente dentro de um método.

**Sintaxe Geral de uma expressão lambda**:
```java
(parametros) -> { corpo_da_função }
```

- Parâmetros: Valores de entrada da função.
- `->` : Indica que estamos declarando uma expressão lambda.
- Corpo: O código executado pela função.

**Variação na sintaxe**:
```java
// Sem parâmetros
() -> System.out.println("Hello, Lambda!");

// Um parâmetro (parênteses opcionais)
x -> x * 2;

// Múltiplos parâmetros
(x, y) -> x + y;

// Corpo com múltiplas linhas (uso obrigatório de chaves)
(x, y) -> { 
    int resultado = x + y;
    return resultado;
};
```

---

### 1. Usando Lambda com `Function`

A interface funcional `Function<T, R>` recebe um valor e retorna outro.
```java
import java.util.function.Function;

public class ExemploLambda {
    public static void main(String[] args) {
        // Lambda que dobra um número
        Function<Integer, Integer> dobrar = x -> x * 2;
        
        System.out.println(dobrar.apply(5)); // 10
    }
}
```
**Explicação**:
- `Function<Integer, Integer>` → Recebe um `Integer` e retorna um `Integer`.
- `x -> x * 2` → Multiplica `x` por 2.
- `dobrar.apply(5)` → Aplica a função ao número `5`.

___

## 2. Lambdas com Interfaces Funcionais Padrão do Java

O pacote `java.util.function` já inclui diversas interfaces funcionais que podemos usar com lambdas:

| Interface             | Parâmetros | Retorno   | Exemplo de Uso               | Descrição                                                                                                         |
| --------------------- | ---------- | --------- | ---------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| `Supplier<T>`         | Nenhum     | `T`       | `() -> "Olá"`                | Fornece um valor sem receber nenhum parâmetro. Útil para **fábricas de objetos** ou **valores dinâmicos**.        |
| `Consumer<T>`         | `T`        | `void`    | `x -> System.out.println(x)` | Executa uma operação sobre um dado sem retornar nada. Normalmente usado para **logs** ou **ações sobre objetos**. |
| `Function<T, R>`      | `T`        | `R`       | `x -> x * 2`                 | Converte um tipo de dado em outro. Muito usada para **transformações e mapeamentos** em **Streams**.              |
| `Predicate<T>`        | `T`        | `boolean` | `x -> x > 10`                | Avalia uma condição e retorna **true** ou **false**. Usado em **filtros e validações**.                           |
| `BiFunction<T, U, R>` | `T, U`     | `R`       | `(x, y) -> x + y`            | Aceita dois argumentos e retorna um resultado. Útil para **operações matemáticas** ou **combinações de dados**.   |

---

## 3. Ordenação de Listas com Lambdas

As expressões lambda são ideais para ordenar coleções de forma simples e elegante.
```java
import java.util.Arrays;
import java.util.List;

public class ExemploOrdenacao {
    public static void main(String[] args) {
        List<String> nomes = Arrays.asList("Carlos", "Ana", "Bruno");

        // Ordena em ordem alfabética (ignora maiúsculas/minúsculas)
        nomes.sort((a, b) -> a.compareToIgnoreCase(b));

        System.out.println(nomes); // [Ana, Bruno, Carlos]
    }
}
```
**Explicação**:
- `.sort((a, b) -> a.compareToIgnoreCase(b))` → Compara duas Strings sem diferenciar maiúsculas de minúsculas.

**Forma Alternativa (Method Reference):
```java
nomes.sort(String::compareToIgnoreCase);
```

---

## 4. Uso de Lambdas com [[Streams API]]

As expressões lambda se combinam muito bem com a Streams API, permitindo manipular coleções de forma funcional.

**Filtrando elementos em uma lista**
```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class ExemploFiltro {
    public static void main(String[] args) {
        List<String> nomes = Arrays.asList("Ana", "Bruno", "Carlos", "Beatriz");

        // Filtra nomes que começam com "B"
        List<String> nomesComB = nomes.stream()
            .filter(nome -> nome.startsWith("B"))
            .collect(Collectors.toList());

        System.out.println(nomesComB); // [Bruno, Beatriz]
    }
}
```
**Explicação**:
- `.filter(nome -> nome.startsWith("B"))` → Mantém apenas nomes que começam com "B".

---

## 5. Lambda com `Runnable` - Criando Threads

Lambdas também simplificam o uso da interface `Runnable`, usada para criar **threads**.
```java
public class ExemploThread {
    public static void main(String[] args) {
        // Criando uma thread usando Lambda
        Thread thread = new Thread(() -> {
            for (int i = 0; i < 5; i++) {
                System.out.println("Executando thread... " + i);
            }
        });

        thread.start();
    }
}
```
**Explicação**:
- `new Thread(() -> {...}).start();` cria e executa uma thread sem precisar de uma classe anônima.

---

## 6. Método `forEach()` com Lambda

O `forEach()` pode ser usado em listas para iterar de maneira funcional.
```Java
import java.util.List;

public class ExemploForEach {
    public static void main(String[] args) {
        List<String> nomes = List.of("Ana", "Bruno", "Carlos");

        // Percorre a lista e imprime cada nome
        nomes.forEach(nome -> System.out.println("Nome: " + nome));
    }
}
```
Saída:
```
Nome: Ana  
Nome: Bruno  
Nome: Carlos 
```


