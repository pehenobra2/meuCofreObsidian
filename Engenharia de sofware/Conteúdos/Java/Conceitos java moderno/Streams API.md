
A **Streams API** foi introduzida no Java 8 para permitir o processamento de coleções de forma **declarativa, paralelizada e eficiente**. Diferente das abordagens tradicionais com `for` ou `while`, as Streams oferecem uma maneira funcional de manipular dados, reduzindo código repetitivo e melhorando a legibilidade.

## 1. O que é uma Stream?

Uma Stream representa uma sequência de elementos que podem ser processados em um pipeline de operações.

**Características**:
- **Imutável** - Não modifica a coleção original.
- **Lazy (Avaliação Preguiçosa)** - As operações só são executadas quando necessário.
- **Paralelizável** - Pode ser executada em múltiplos threads (`parallelStream()`).

### 1.1. Criando uma Stream

Podemos criar uma Stream a partir de diferentes fontes de dados, como listas, arrays, e até arquivos.
```Java
import java.util.List;
import java.util.stream.Stream;

public class ExemploStream {
    public static void main(String[] args) {
        // Criando uma Stream a partir de uma Lista
        List<String> nomes = List.of("Ana", "Bruno", "Carlos");
        Stream<String> stream = nomes.stream(); 

        // Exibindo os elementos da Stream
        stream.forEach(System.out::println);
    }
}
```
Saída:
```
Ana  
Bruno  
Carlos  
```
🚨**Atenção!!! Uma stream só pode ser usada uma única vez. Após a operação `forEach()`, ela não pode ser reutilizada.

---

## 2. Filtrando Dados

O método `filter(Predicate<T>)` permite remover elementos que **não atendem a uma condição
```Java
import java.util.List;
import java.util.stream.Collectors;

public class ExemploFiltro {
    public static void main(String[] args) {
        List<String> nomes = List.of("Ana", "Bruno", "Carlos", "Beatriz");

        // Filtra nomes que começam com "B"
        List<String> nomesComB = nomes.stream()
            .filter(nome -> nome.startsWith("B"))
            .collect(Collectors.toList());

        System.out.println(nomesComB); // [Bruno, Beatriz]
    }
}
```
**Explicação**:
- `.filter(nome-> nome.startsWith("B"))` → Mantém apenas nomes que começam com "B".
- `.collect(Collectors.toList())` → Converte a Stream de volta para uma Lista.

---

## 3. Transformação de Dados

O método `map(Function<T, R>)` **transforma cada elemento da Stream** em outro tipo de dado.
```Java
import java.util.List;
import java.util.stream.Collectors;

public class ExemploMap {
    public static void main(String[] args) {
        List<String> nomes = List.of("Ana", "Bruno", "Carlos");

        // Transforma cada nome no seu tamanho (número de caracteres)
        List<Integer> tamanhos = nomes.stream()
            .map(String::length) // Transforma "Ana" em 3, "Bruno" em 5, etc.
            .collect(Collectors.toList());

        System.out.println(tamanhos); // [3, 5, 6]
    }
}
```
**Explicação**:
- `.map(String:length)` → Converte cada `String` para um `Integer` contendo o número de caracteres.

---

## 4. Reduzindo Dados

O método `reduce()` combina todos os elementos de uma Stream em **um único resultado**.
```Java
import java.util.List;

public class ExemploReduce {
    public static void main(String[] args) {
        List<String> nomes = List.of("Ana", "Bruno", "Carlos");

        // Soma o total de caracteres de todos os nomes
        int somaCaracteres = nomes.stream()
            .map(String::length)  // Transforma os nomes em seus tamanhos [3, 5, 6]
            .reduce(0, Integer::sum); // Soma todos os tamanhos

        System.out.println("Total de caracteres: " + somaCaracteres); // 14
    }
}
```
**Explicação**:
- `.map(String:length)` → Transforma `"Ana", "Bruno", "Carlos"` em `[3, 5, 6]`.
- `.reduce(0, Integer:sum)` → Soma os valores: `3 + 5 + 6 = 14`.

---

## 5. Executando Streams em Paralelo

Para grandes conjuntos de dados, podemos processar elementos **simultaneamente** em múltiplas threads usando `parallelStream()`.
```Java
import java.util.List;

public class ExemploParallel {
    public static void main(String[] args) {
        List<String> nomes = List.of("Ana", "Bruno", "Carlos", "Diego", "Eva");

        // Processamento paralelo
        nomes.parallelStream().forEach(nome -> 
            System.out.println(Thread.currentThread().getName() + " -> " + nome)
        );
    }
}
```
**Explicação**:
- `.parallelStream()` executa as operações da Stream em **múltiplas threads**, acelerando o processamento em coleções grandes.

🚨**Cuidado!! O processamento paralelo pode trazer problemas de concorrência se os elementos não forem independentes**.

---

## 6. Outras Operações Importantes

### 6.1. Ordenação com `Sorted()`

```Java
List<String> nomesOrdenados = nomes.stream()
    .sorted()
    .collect(Collectors.toList());
```
**Ordena os elementos em ordem alfabética.**

### 6.2. Contando elementos com `Count()`

```Java
long total = nomes.stream().count();
```
**Retorna o número total de elementos na Stream.

### 6.3. Encontrando o primeiro elemento com `findFirst()`

```Java
Optional<String> primeiro = nomes.stream().findFirst();
```
**Retorna o primeiro elemento da Stream (se existir).

### 6.4. Verificando condições com `allMatch()`, `anyMatch()` e `noneMatch()`

```Java
boolean todosComA = nomes.stream().allMatch(nome -> nome.startsWith("A"));
boolean algumComB = nomes.stream().anyMatch(nome -> nome.startsWith("B"));
boolean nenhumComZ = nomes.stream().noneMatch(nome -> nome.startsWith("Z"));
```
**Verifica se todos, algum ou nenhum dos elementos atendem a uma condição.**

---