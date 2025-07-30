## 1. Programação Orientada a Objetos

A POO é um paradigma baseado em objetos (Entidades que combinam dados e comportamentos). Em Java, os pilares são:

1. Encapsulamento - Protege os atributos, usando `private`, e expõe acesso controlado via `getters`/`setter`.
2. Herança - Uma classe herda atributos e métodos de uma classe pai (`extends`).
3. Polimorfismo - Um objeto pode ser tratado como do tipo da sua superclasse ou interface.
4. Abstração - Define apenas o essencial (interfaces e classes abstratas).

### 1.1. Exemplo

``` Java
abstract class Animal {
    protected String nome;

    public Animal(String nome) {
        this.nome = nome;
    }

    public abstract void emitirSom();
}

class Cachorro extends Animal {
    public Cachorro(String nome) {
        super(nome);
    }

    @Override
    public void emitirSom() {
        System.out.println(nome + " faz: Au Au!");
    }
}

class Gato extends Animal {
    public Gato(String nome) {
        super(nome);
    }

    @Override
    public void emitirSom() {
        System.out.println(nome + " faz: Miau!");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a1 = new Cachorro("Rex");
        Animal a2 = new Gato("Mimi");

        a1.emitirSom(); // Rex faz: Au Au!
        a2.emitirSom(); // Mimi faz: Miau!
    }
}
```

👉Polimorfismo em ação: `Animal` pode referenciar um `Cachorro` ou `Gato`.

---

## 2. Collections Framework

O Collections Framework é um conjunto de interfaces e classes para trabalhar com coleções de objetos.

- List -> Permite elementos duplicados, mantém ordem (`ArrayList`, `LinkedList`).
- Set -> Não permite duplicados (`HashSet`, `TreeSet`).
- Map -> Armazena pares chave-valor (`HashMap`, `TreeMap`).

### 2.1. Exemplos

``` Java
import java.util.*;

public class CollectionsDemo {
    public static void main(String[] args) {
        // Lista ordenada
        List<String> nomes = new ArrayList<>();
        nomes.add("Pedro");
        nomes.add("Ana");
        nomes.add("Pedro"); // permite duplicado
        System.out.println(nomes); // [Pedro, Ana, Pedro]

        // Conjunto sem duplicatas
        Set<String> conjunto = new HashSet<>(nomes);
        System.out.println(conjunto); // [Pedro, Ana]

        // Mapa chave-valor
        Map<Integer, String> mapa = new HashMap<>();
        mapa.put(1, "Java");
        mapa.put(2, "Python");
        mapa.put(3, "Go");

        System.out.println(mapa.get(2)); // Python
        mapa.forEach((k,v) -> System.out.println(k + ": " + v));
    }
}
```

---

## 3. Streams API

Streams foram introduzidos no Java 8 para trabalhar com coleções de forma funcional (filtros, mapeamentos, reduções).

### 3.1. Exemplos:

``` Java
import java.util.*;

public class StreamsDemo {
    public static void main(String[] args) {
        List<Integer> numeros = Arrays.asList(1,2,3,4,5,6);

        // Filtrar pares e somar
        int somaPares = numeros.stream()
            .filter(n -> n % 2 == 0)
            .mapToInt(Integer::intValue)
            .sum();

        System.out.println("Soma dos pares: " + somaPares);

        // Transformar para string e ordenar
        List<String> resultado = numeros.stream()
            .map(n -> "Num:" + n)
            .sorted()
            .toList();

        System.out.println(resultado);
    }
}
```

👉 Operações intermediárias (`filter`, `map`, `sorted`) retornam um novo stream.

👉 Operações terminais (`sum`, `collect`, `forEach`) finalizam o processamento.

---

## 4. Lambdas

Uma lambda é uma forma curta de escrever funções anônimas.

Antes do Java 8:

```Java
Runnable r = new Runnable() {
    @Override
    public void run() {
        System.out.println("Executando...");
    }
};
```

Com lambda:
```Java
Runnable r = () -> System.out.println("Executando...");
```

Combinando com Streams:
```Java
List<String> nomes = Arrays.asList("Ana", "João", "Maria");
nomes.forEach(nome -> System.out.println(nome.toUpperCase()));
```

---

## 5. Tratamento de Exceções

Java possui checked e unchecked exceptions.

- Checked -> Obrigam `try/catch` ou `throws` (`IOException`).
- Unchecked -> Erros de programação (`NullPointerException`, `IndexOutOfBoundsException`).

### 5.1. Exemplo:

```Java
public class ExcecoesDemo {
    public static void main(String[] args) {
        try {
            int resultado = dividir(10, 0);
            System.out.println(resultado);
        } catch (ArithmeticException e) {
            System.err.println("Erro: divisão por zero!");
        } finally {
            System.out.println("Sempre executa.");
        }
    }

    public static int dividir(int a, int b) {
        return a / b;
    }
}
```

---

