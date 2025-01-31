JavaServer Faces (JSF) é um framework Java para construção de interfaces web baseadas em componentes. Ele facilita a criação de aplicações [[Java EE]] ao fornecer um modelo baseado em componentes para a UI, gerenciado pelo próprio framework.

---

## 1. Como o JSF funciona? ⚙️

O JSF segue o padrão **MVC (Model - View - Controller)**, onde:
- **View**: Define a interface gráfica usando arquivos ``.xhtml``.
- **Controller**: São os Managed Beans **(`@ManagedBean` ou [[CDI]] `@Named`)** que processam ações do usuário.
- **Model**: Representa os dados da aplicação, geralmente mapeados com [[JPA]] (`@Entity`).

### 1.1. Ciclo de vida de uma Requisição JSF

O JSF gerencia automaticamente o ciclo de vida da requisições HTTP, garantindo que os componentes da interface sejam processados corretamente. Esse ciclo é composto pelas seguintes fases:
1. **Recebimento da Requisição**: O usuário acessa a página JSF.
2. **Restaurar View**: O framework cria ou restaura a árvore de componentes da interface do usuário.
3. **Aplicar Valores da Requisição**: Os dados do formulário enviado pelo cliente são carregados nos componentes.
4. **Processar Validações**: O JSF executa conversão de tipos, validaçãode dados e aplica regras de negócio.
5. **Atualizar Dados do Modelo**: Com CDI, os valores dos componentes são injetados diretamente nos beans anotados com `@Named` e escopo apropriado (`@RequestScoped`, `@ViewScoped`, etc). Isso garante separação de responsabilidades e reutilização de componentes.
6. **Invocar Aplicações**: O JSF processa a lógica do negócio chamando serviços CDI, que são injetados automaticamente usando `@Inject`. Os beans de serviço são definidos com escopos como `ApplicationScoped` ou `@Dependent`, garantindo modularidade e reutilização.
7. **Renderizar Resposta**: O framework gera o HTML correspondente à interface e o envia ao navegador.
8. **Resposta**: O cliente recebe e exibe a página renderizada.

---

## 2. Escopos de CDI no JSF 

No contexto do JSF, os beans podem ser definidos com diferentes escopos, dependendo da necessidade da aplicação:

- **@ResquestScoped**: O bean vive durante uma única requisição HTTP.
- **@ViewScope**: Mantém o estado enquanto o usuário estiver na mesma página.
- **@SessionScoped**: Dura enquanto a sessão do usuário estiver ativa.
- **@ApplicationScoped**: Compartilhando por toda a aplicação.
- **@Dependent**: Criado e destruído junto como bean que injeta.

---

## 3. Estrutura de um Projeto JSF 📂

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

## 4. Exemplo de código 🖥️

### 4.1. Página XHTML

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

### 4.2. Bean Gerenciado com [[CDI]] (Controller)

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
	            FacesContext
		            .getCurrentInstance()
		            .getExternalContext()
		            .redirect("home.xhtml");
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

### 4.3. Serviço de Autenticação com [[CDI]]

```java
import jakarta.enterprise.context.ApplicationScoped;

@ApplicationScoped
public class AutenticacaoService {
    public boolean autenticar(String usuario, String senha) {
        return "admin".equals(usuario) && "1234".equals(senha);
    }
}
```

### 4.4. Arquivo de configuração (`faces-config.xml`)

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
