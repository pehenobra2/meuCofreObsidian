JavaServer Faces (JSF) é um framework Java para construção de interfaces web baseadas em componentes. Ele facilita a criação de aplicações [[Java EE]] ao fornecer um modelo baseado em componentes para a UI, gerenciado pelo próprio framework.

---

## 1. Como o JSF funciona? ⚙️

O JSF segue o padrão **MVC (Model - View - Controller)**, onde:
- **View**: Define a interface gráfica usando arquivos ``.xhtml``.
- **Controller**: São os Managed Beans **(`@ManagedBean` ou [[CDI]] `@Named`)** que processam ações do usuário.
- **Model**: Representa os dados da aplicação, geralmente mapeados com [[JPA]] (`@Entity`).

### 1.1. Ciclo de vida de uma Requisição JSF
O JSF gerencia o ciclo de vida da interface de usuário, incluindo:
1. **Recebimento da Requisição**: O usuário acessa a aplicação.
2. **Construção da Árvore de componentes**: O JSF processa os componentes da interface.
3. **Processamento de Eventos**: Interpreta inputs do usuário e interage com o backend.
4. **Renderização da Resposta**: Retorna a página para o usuário

---

## 2. Estrutura de um Projeto JSF 📂

Um projeto JSF geralmente segue esta estrutura:

```
meu-projeto/
│── src/main/java/
│   ├── com.exemplo.controle/   # Beans Gerenciados (Controladores)
│   │   ├── UsuarioBean.java
│   ├── com.exemplo.modelo/     # Modelos de Dados (Entidades)
│   │   ├── Usuario.java
│   ├── com.exemplo.service/    # Serviços CDI
│   │   ├── AutenticacaoService.java
│── src/main/webapp/
│   ├── WEB-INF/
│   │   ├── faces-config.xml    # Configuração JSF
│   │   ├── beans.xml           # Ativa o CDI no projeto
│   ├── index.xhtml             # Página Inicial
│   ├── login.xhtml             # Tela de Login
│── pom.xml                     # Dependências Maven
│── server.xml                  # Configuração do servidor
```

---

## 3. Exemplo de código

### 3.1 Página XHTML

O arquivo `index.xhtml` define a interface da aplicação:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml"
      xmlns:h="http://java.sun.com/jsf/html">
<head>
    <title>Login</title>
</head>
<body>
    <h:form>
        <h:panelGrid columns="2">
            <h:outputLabel for="username" value="Usuário:" />
            <h:inputText id="username" value="#{usuarioBean.nome}" />

            <h:outputLabel for="password" value="Senha:" />
            <h:inputSecret id="password" value="#{usuarioBean.senha}" />

            <h:commandButton value="Entrar" action="#{usuarioBean.login}" />
        </h:panelGrid>
    </h:form>
</body>
</html>
```
**Explicação:**
- `h:form`: Cria um formulário JSF.
- `h:inputText`: Campo de entrada ligado ao **Managed Bean**.
- `h:commandButton`: Botão que chama o método `login()` do `UsuárioBean`.

### 3.2 Managed Bean (Controller) com [[CDI]]

Criamos o `UsuarioBean.java` para processar a lógica de login:
```java
import jakarta.inject.Named;
import jakarta.enterprise.context.RequestScoped;
import jakarta.inject.Inject;
import jakarta.faces.context.FacesContext;
import java.io.IOException;

@Named
@RequestScoped
public class UsuarioBean {
    private String nome;
    private String senha;

    @Inject
    private AutenticacaoService authService;

    public String getNome() { return nome; }
    public void setNome(String nome) { this.nome = nome; }

    public String getSenha() { return senha; }
    public void setSenha(String senha) { this.senha = senha; }

    public void login() {
        if (authService.autenticar(nome, senha)) {
            try {
                FacesContext.getCurrentInstance().getExternalContext().redirect("home.xhtml");
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```
**Explicação**:
- `@Named`: Indica que este bean pode ser acessado via EL (`#{usuarioBean}` o XHTML).
- `@RequestScoped`: Define o escopo do bean.
- `@Inject`: Injeção de dependência do **AutenticacaoService**.

### 3.3 Serviço de Autenticação com [[CDI]]

```java
import jakarta.enterprise.context.ApplicationScoped;

@ApplicationScoped
public class AutenticacaoService {
    public boolean autenticar(String usuario, String senha) {
        return "admin".equals(usuario) && "1234".equals(senha);
    }
}
```

### 3.4 Arquivo de configuração (`faces-config.xml`)

Embora opcional no JSF 2.X, este arquivo pode configurar regras de navegação:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<faces-config xmlns="http://java.sun.com/xml/ns/javaee"
              version="2.0">
    <navigation-rule>
        <from-view-id>/index.xhtml</from-view-id>
        <navigation-case>
            <from-outcome>home</from-outcome>
            <to-view-id>/home.xhtml</to-view-id>
        </navigation-case>
    </navigation-rule>
</faces-config>
```

---
