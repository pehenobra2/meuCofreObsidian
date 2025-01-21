
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