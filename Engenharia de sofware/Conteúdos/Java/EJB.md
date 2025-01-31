## 1. O que é❓

O Enterprise JavaBeans (EJB) é um framework da plataforma [[Java EE]] que facilita o desenvolvimento de aplicações corporativas robustas, escaláveis e seguras. Ele permite a criação de componentes distribuídos, transacionais e reutilizáveis para aplicações empresariais.

---

## 2. Principais Características do EJB 3.0 ✨

- **Simplicidade**: Uso reduzido de XML, configuração via anotações.
- **POJOs (Plain Old Java Objects)**: [[Bean#4.4. EJBs|Beans]] agora podem ser classes simples sem necessidade de implementar interfaces específicas.
- **Injeção de Dependência**: Facilita a integração e reduz acoplamento.
- **Gerenciamento de Transações**: Suporte nativo a transações distribuídas.
- **Segurança Integrada**: Controle de acesso baseado em anotações.
- **Componentes Distribuídos**: Comunicação via RMI, CORBA e Web Services.

---

## 3. Tipos de EJBs no EJB 3.0 🧩

O EJB 3.0 suporta três tipos principais de Enterprise Beans:

### 3.1. Session Beans

Componentes que encapsulam lógica de negócio.

#### 3.1.1. Stateless Session Beans

Sem estado entre chamadas; ótimo para serviços rápidos.

- Exemplo:
```java
import javax.ejb.Stateless;

@Stateless  
public class CalculadoraEJB {  
    public int somar(int a, int b) {  
        return a + b;  
    }  
}
```

#### 3.1.2. Stateful Session Beans

Mantêm estado entre chamadas; útil para sessões de usuário.

- Exemplo: Carrinho de compras
```java
import javax.ejb.Stateful;
import java.util.ArrayList;
import java.util.List;

@Stateful  // Mantém estado entre chamadas
public class CarrinhoComprasEJB {
    
    private List<String> produtos = new ArrayList<>();

    public void adicionarProduto(String produto) {
        produtos.add(produto);
    }

    public void removerProduto(String produto) {
        produtos.remove(produto);
    }

    public List<String> listarProdutos() {
        return produtos;
    }
}
```
Uso do Stateful Bean em um cliente Java:
```java
import javax.ejb.EJB;

public class Cliente {
    
    @EJB
    private static CarrinhoComprasEJB carrinho;

    public static void main(String[] args) {
        carrinho.adicionarProduto("Notebook");
        carrinho.adicionarProduto("Mouse");

        System.out.println("Produtos no carrinho: " + carrinho.listarProdutos());

        carrinho.removerProduto("Mouse");

        System.out.println("Produtos no carrinho após remoção: " + carrinho.listarProdutos());
    }
}
```
**Explicação**:
- O `@Stateful` mantém os produtos armazenados para cada cliente.
- Se um cliente adiciona produtos, ele mantém esse estado enquanto a sessão estiver ativa.
- Isso evita a necessidade de reter informações no cliente ou no banco de dados a cada chamada.


#### 3.1.3. Singleton Session Beans

Apenas uma instância compartilhada na aplicação.

- Exemplo: Controlador de Acessos.
```java
import javax.ejb.Singleton;

@Singleton  // Apenas uma instância para toda a aplicação
public class ContadorAcessosEJB {
    
    private int contador = 0;

    public void incrementar() {
        contador++;
    }

    public int getContador() {
        return contador;
    }
}
```
Uso do Singleton Bean em um Cliente Java:
```java
import javax.ejb.EJB;

public class Aplicacao {
    
    @EJB
    private static ContadorAcessosEJB contador;

    public static void main(String[] args) {
        contador.incrementar();
        contador.incrementar();

        System.out.println("Número de acessos: " + contador.getContador());
    }
}
```
**Explicação**:
- O `@Singleton` garante que todos os usuários compartilhem a mesma instância.
- O contador será incrementado globalmente sempre que alguém chamar `incrementar()`.
- Ideal para armazenar informações como estatísticas, caches e configurações globais.

### 3.2. Message-Driven Beans (MDBs)

Processam mensagens de forma assíncrona, geralmente integrados com JMS (Java message Service).

- Exemplo:
```java
import javax.ejb.MessageDriven;
import javax.jms.Message;
import javax.jms.MessageListener;

@MessageDriven  
public class ProcessadorMensagens implements MessageListener {  
    public void onMessage(Message message) {  
        System.out.println("Mensagem recebida: " + message);  
    }  
}
```

### 3.3. Entity Beans ([[JPA]] + EJB)

Antes do EJB 3.0, os Entity Beans eram usados para persistência, mas com o EJB 3.0 foi adotado o [[JPA]] para mapear entidades diretamente no banco de dados.

- Exemplo:
```java
import javax.persistence.*;

@Entity  
public class Cliente {  
    @Id  
    @GeneratedValue  
    private Long id;  
    private String nome;  

    // Getters e Setters  
}
```

---

## 4. Injeção de Dependência no EJB 3.0 💉

A injeção de dependência simplifica a obtenção de instâncias de beans sem precisar do JNDI manualmente.

- Exemplo de Injeção de um Session Bean em outro Bean:
```java
import javax.ejb.EJB;
import javax.ejb.Stateless;

@Stateless  
public class ServicoCliente {  

    @EJB  
    private CalculadoraEJB calculadora;  

    public void executar() {  
        int resultado = calculadora.somar(5, 10);  
        System.out.println("Resultado: " + resultado);  
    }  
}
```

---

## 5. Vantagens 🔺

- **Facilidade de Desenvolvimento**: Menos configurações, mais produtividade.
- **Gerenciamento Automático**: Transações, concorrência e segurança são gerenciados pelo contêiner.
- **Suporte a Web Services**: Fácil integração com serviços REST e SOAP.
- **Escalabilidade**: Ideal para aplicações distribuídas e de alta carga.

---
