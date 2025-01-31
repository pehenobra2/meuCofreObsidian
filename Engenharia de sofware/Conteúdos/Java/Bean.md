
## 1. O que é um Bean Java❓

Um JavaBean (ou simplismente Bean) é uma classe Java reutilizável que segue um conjunto específico de regras para garantir que possa ser usada de maneira padronizada em aplicações Java.

Os Beans são aplamente utilizados em frameworks como [[Spring]], [[JSF]], [[EJB]], e no próprio [[Java EE|Java EE/Jakarta EE]] para representar objetos de negócio, componentes de UI e configurações de aplicação.

---

## 2. Regras para um Bean📝

Para que uma classe seja considerada um Bean, ela deve serguir estar regras:

1. **Ter um construtor público sem argumentos**
	1. Isso permite que a classe possa ser instanciada dinamicamente.
2. **Ter atributos privados (encapsulamento)**
	1. Os atributos devem ser acessados apenas através dos métodos getters e setters.
3. **Ter métodos getters e setters padrão**
	1. Deve usar a convenção `getNome()` para leitura e `setNome(valor)` para escrita.
4. **Ser serializável**
	1. Implementar `java.io.Serializable` para que possa ser salvo e recuperado do armazenamento (como em sessões de usuário).

---

## 3. Exemplo de um Bean Simples 🖥️

```java
import java.io.Serializable;

public class Usuario implements Serializable {
    private String nome;
    private String email;

    // Construtor padrão obrigatório
    public Usuario() {}

    // Getters e Setters
    public String getNome() {
        return nome;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }
}
```

---

## 4. Tipos de Beans ☕

### 4.1. Beans Tradicionais

- Simples classes Java que seguem as regras mencionadas acima.

### 4.2. Managed Beans ([[JSF]] e [[CDI]])

- Usados para [[JSF]] e [[CDI]] para representar componentes de UI e lógica de negócios.
- Exemplo:
```java
import jakarta.enterprise.context.RequestScoped;
import jakarta.inject.Named;

@Named
@RequestScoped
public class MeuBean {
    private String mensagem = "Olá, mundo!";

    public String getMensagem() {
        return mensagem;
    }

    public void setMensagem(String mensagem) {
        this.mensagem = mensagem;
    }
}
```

### 4.3. [[Spring]] Beans

- Objetos gerenciados pelo [[Spring|Spring Framework]], usados para injeção de dependência.
- Exemplo:
```java
import org.springframework.stereotype.Component;

@Component
public class MeuSpringBean {
    public void executar() {
        System.out.println("Spring Bean em execução!");
    }
}
```

### 4.4. EJBs

- Usados em [[Java EE|Java EE/Jakarta EE]] para lógica de negócios distribuída.
- Exemplo:
```java
import jakarta.ejb.Stateless;

@Stateless
public class MeuEJB {
    public String processar() {
        return "Processamento no EJB concluído!";
    }
}
```

---

## 5. Vantagens de Usar Beans 🔺

- **Encapsulamento**: Protege os dados da classe.
- **Reutilização**: Classes podem ser reutilizadas em várias partes da aplicação.
- **Facilidade de integração**: Muitos frameworks Java suportam Beans.
- **Padrão e convenção**: Mantém o código organizado e padronizado.

---

