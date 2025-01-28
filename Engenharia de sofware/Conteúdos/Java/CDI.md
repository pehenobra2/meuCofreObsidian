## 1. O que é o CDI (Context and Dependency Injection)?

**CDI (Context and Dependency Injection)** é uma especificação do [[Java EE]] (agora Jakarta EE) que fornece **injeção de dependências e gerenciamento de ciclo de vida de objetos**. Ele substitui e melhora o antigo conceito de **Managed beans** (`@ManagedBean`), oferecendo mais flexibilidade e integração com outras tecnologias [[Java EE]], como [[JSF]], [[JPA]] E EJB.

- **Principais Benefícios do CDI**:
	- Permite a injeção de dependências de forma declarativa.
	- Gerencia o ciclo de vida dos objetos automaticamente.
	- Oferece suporte a escopos contextuais, como `@RequestScoped`, `@SessionScoped`, `@ApplicationScoped`, etc.
	- Integração nativa com **[[JSF]], [[JPA]], e EJB**.

## 2. Diferença entre CDI e @ManagedBean

Antes do CDI, o JSF usava `@ManagedBean`, mas essa abordagem tem limitações, como falta de suporte avançado a injeção de dependência e ciclos de vida mais complexos.

- **Comparação**

| **Recurso**        | **`@ManagedBean`(Antigo)** | **`@Named` (CDI)** |
| ------------------ | -------------------------- | ------------------ |
| Definição de Beans | `@ManagedBean`             | `@Named`           |
| Suporte a Injeção  | Limitado                   | Completo           |
| Escopos Avançados  | Limitado                   | Completo           |
| Integrado ao JSF   | Sim                        | Sim                |
👉**CDI é a abordagem recomendada nas versões modernas do Jakarta EE.

---

## 3. Exemplo de Uso do CDI no JSF

### 3.1 Criando um Bean CDI

Substituímos `@ManagedBean` por `@Named` e adicionamos `@RequestScope` (ou outro escopo desejado).
```java
import jakarta.enterprise.context.RequestScoped;
import jakarta.inject.Named;

@Named
@RequestScoped
public class UsuarioBean {
    private String nome;
    private String senha;

    public String getNome() { return nome; }
    public void setNome(String nome) { this.nome = nome; }

    public String getSenha() { return senha; }
    public void setSenha(String senha) { this.senha = senha; }

    public String login() {
        if ("admin".equals(nome) && "1234".equals(senha)) {
            return "home.xhtml?faces-redirect=true";
        }
        return null;
    }
}
```
**Explicação**:
- `@Named`: Permite acessar esse bean no JSF (substitui `@ManagedBean`).
- `@RequestScoped`: O bean vive apenas durante a requisição HTTP.
- Método `login()`: Faz uma navegação condicional para `home.xhtml`.

### 3.2 Injetando Dependência com CDI

Com o CDI, podemos usar `@Inject` para injetar um serviço dentro de outro bean.

**Exemplo: Criando um serviço de autenticação e injetando no `UsuarioBean`**.

**Classe de Serviço**
```java
import jakarta.enterprise.context.ApplicationScoped;

@ApplicationScoped
public class AutenticacaoService {
    public boolean autenticar(String usuario, String senha) {
        return "admin".equals(usuario) && "1234".equals(senha);
    }
}
```
**Explicação**:
- `@ApplicationScoped`: Esse serviço é único para toda a aplicação.

**Injetando no `UsuarioBean`
```java
import jakarta.enterprise.context.RequestScoped;
import jakarta.inject.Inject;
import jakarta.inject.Named;

@Named
@RequestScoped
public class UsuarioBean {
    private String nome;
    private String senha;

    @Inject
    private AutenticacaoService authService;

    public String login() {
        if (authService.autenticar(nome, senha)) {
            return "home.xhtml?faces-redirect=true";
        }
        return null;
    }

    // Getters e Setters
}
```
**Explicação**:
- `@Inject`: Faz a injeção automática do serviço `AutenticacaoService`.
- O método `login()` chama o serviço injetado.

---

## 4. Escopos Disponíveis no CDI

O CDI oferece diferentes escopos de bean, dependendo de quanto tempo queremos que o objeto permaneça ativo.

| Escopo              | Anotação              | Duração                                         |
| ------------------- | --------------------- | ----------------------------------------------- |
| Requisição          | `@RequestScoped`      | Uma única requisição HTTP                       |
| Sessão              | `@SessionScoped`      | Dura enquanto a sessão do usuário estiver ativa |
| Aplicação           | `@ApplicationScoped`  | Dura durante toda a aplicação                   |
| Dependente (Padrão) | `@Dependent`          | Sem escopo próprio, depende de outro objeto     |
| Conversacional      | `@ConversationScoped` | Dura enquanto a conversação estiver ativa       |
👉**No JSF, o mais comum é usar `@RequestScoped` para Beans de UI e `@ApplicationScoped` para serviços compartilhados**.

---

## 5. Configuração do CDI no Projeto

Para usar o CDI, é necessário um arquivo chamado `beans.xml`, mesmo que ele esteja vazio.

### 5.1 Crie o arquivo em `WEB-INF/beans.xml`:
📌 **src/main/webapp/WEB-INF/beans.xml**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="https://jakarta.ee/xml/ns/jakartaee"
       version="4.0">
</beans>
```
✅**Esse arquivo ativa CDI no projeto.**

---
