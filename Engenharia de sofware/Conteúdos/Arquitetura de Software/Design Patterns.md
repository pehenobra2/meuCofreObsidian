
## 1. Singleton

O **Singleton** é um padrão de projeto de design que garante que uma classe tenha **somente uma instância** durante a execução do programa e fornece um ponto de acesso global para essa instância.

### 1.1 Características principais 🔥
- **Uma única instância**: A classe cria e mantém uma única instância.
- **Acesso global**: A instância é acessada através de um método estático.
- **Controle de criação**: O objeto é criado apenas quando necessário.

### 1.2 Exemplo de implementação simples
```java
public class Singleton {
    private static Singleton instancia;

    private Singleton() {}

    public static Singleton getInstance() {
        if (instancia == null) {
            instancia = new Singleton();
        }
        return instancia;
    }
}
```

### 1.3 Quando usar?
- **Gerenciamento de recursos compartilhados**, como conexões de banco de dados.
- **Configurações globais** no sistema.

### 1.4 Vantagens 🔺
- Eficiência no uso de recursos.
- Controle centralizado da instância.

### 1.5 Desvantagens 🔻
- Difícil de testar e substituir.
- Pode ser problemático em ambientes multithread (requer controle de concorrência).

---

## 2. Factory

O **Factory** é um padrão de design que define uma interface para criar objetos, mas permite que as subclasses decidam qual classe instanciar. Esse padrão ajuda a delegar a criação de objetos para métodos específicos, o que promove o desacoplamento.

### 2.1 Características principais 🔥

- **Criação centralizada**: A criação de objetos é centralizada em uma fábrica.
- **Desacoplamento**: O código cliente não precisa saber como os objetos são criados, apenas que a fábrica retorna um tipo de objeto.
- **Subclasses especializadas**: A fábrica pode ser estendida para criar diferentes tipos de objetos

### 2.2 Exemplos de implementação simples
```java
public interface Produto {
    void exibir();
}

public class ProdutoA implements Produto {
    public void exibir() {
        System.out.println("Produto A");
    }
}

public class ProdutoB implements Produto {
    public void exibir() {
        System.out.println("Produto B");
    }
}

public abstract class Fabrica {
    public abstract Produto criarProduto();
}

public class FabricaA extends Fabrica {
    public Produto criarProduto() {
        return new ProdutoA();
    }
}

public class FabricaB extends Fabrica {
    public Produto criarProduto() {
        return new ProdutoB();
    }
}
```

## 2.3 Quando usar?
- Quando a criação de objetos é complexa ou envolve várias etapas
- Quando o sistema precisa ser flexível para adicionar novos tipos de objetos sem alterar o código existente

## 2.4 Vantagens 🔺

- Desacoplamento entre criação e uso de objetos
- Facilidade para adicionar novos tipos de objetos

## 2.5 Desvantagens 🔻

- Pode aumentar a complexidade do código
- Mais classes podem ser necessárias para implementar fábricas diferentes

---

## 3. Method

O **Method** (ou Strategy) é um padrão de design comportamental que define uma família de algoritmos, encapsula cada um deles e os torna intercambiáveis. O algoritmo pode ser alterado sem afetar os clientes que utilizam o padrão.

## 3.1 Características principais 🔥

## 3.2 Exemplo de implementação simples

## 3.3 Quando usar?

## 3.4 Vantagens 🔺

## 3.5 Desvantagens 🔻

---

## 4. Observer

## 3.1 Características principais 🔥

## 3.2 Exemplo de implementação simples

## 3.3 Quando usar?

## 3.4 Vantagens 🔺

## 3.5 Desvantagens 🔻

---

## 5. Prototype

## 3.1 Características principais 🔥

## 3.2 Exemplo de implementação simples

## 3.3 Quando usar?

## 3.4 Vantagens 🔺

## 3.5 Desvantagens 🔻

---

## 6. Adapter

## 3.1 Características principais 🔥

## 3.2 Exemplo de implementação simples

## 3.3 Quando usar?

## 3.4 Vantagens 🔺

## 3.5 Desvantagens 🔻

---

## 7. Composite

## 3.1 Características principais 🔥

## 3.2 Exemplo de implementação simples

## 3.3 Quando usar?

## 3.4 Vantagens 🔺

## 3.5 Desvantagens 🔻

---

## 8. Decorator

## 3.1 Características principais 🔥

## 3.2 Exemplo de implementação simples

## 3.3 Quando usar?

## 3.4 Vantagens 🔺

## 3.5 Desvantagens 🔻


