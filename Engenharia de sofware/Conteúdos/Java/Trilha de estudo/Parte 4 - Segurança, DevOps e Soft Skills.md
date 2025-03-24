
**Objetivo: Especializar-se em segurança, automação e se destacar no mercado.**

## Conteúdos: 

- [ ] **Segurança da informação** - OWASP Top 10, injeção de dependência, ataques comuns.
- [ ] **Criptografia & Segurança de APIs** – TLS, OAuth, OpenID, JWT avançado.
- [ ] **DevOps & CI/CD** – Jenkins, GitHub Actions, Docker, Kubernetes.
- [ ] **Soft Skills** – Comunicação, liderança técnica, participação em comunidades.

## Prática: melhorando projeto MinhasFinanças

### **1. Segurança da Informação - Protegendo a Aplicação**

✅ **OWASP Top 10**  
A primeira etapa é garantir que sua aplicação esteja protegida contra os principais **ataques da OWASP Top 10**. A aplicação de práticas como **validação de entrada**, **prevenção contra CSRF** e **controle de erros** é essencial para uma API segura.

- **SQL Injection**: Garantir que está utilizando **JPA/Hibernate** corretamente para evitar vulnerabilidades de SQL injection.
- **Cross-Site Scripting (XSS)**: Validar e higienizar entradas de usuário.
- **Cross-Site Request Forgery (CSRF)**: Habilitar proteção CSRF para APIs REST.
- **Injeção de Dependência**: Usar **Spring Security** e **DI** de forma adequada para garantir que dependências sejam controladas corretamente.

### **2. Criptografia & Segurança de APIs**

✅ **TLS, OAuth2, OpenID, JWT Avançado**  
A segurança das APIs deve ser uma prioridade, especialmente quando lidamos com dados financeiros sensíveis. Vamos focar na **autenticação e criptografia**:

- **OAuth2 & JWT**: Implementar autenticação baseada em **OAuth2** com **JWT** para garantir que apenas usuários autenticados possam acessar dados sensíveis.
- **Criptografia de Dados**: Implementar criptografia para dados sensíveis, como informações bancárias dos usuários, utilizando **AES** para dados em repouso.
- **HTTPS/TLS**: Garantir que todas as comunicações entre o **front-end e o back-end** sejam feitas por meio de **HTTPS**.

### **3. DevOps & CI/CD - Automação do Processo de Deploy**

✅ **GitHub Actions e Kubernetes**  
Implementar um **pipeline CI/CD** automatizado para o **MinhasFinanças** usando **GitHub Actions** e **Kubernetes**.

- **GitHub Actions**: Automatizar o processo de build, testes e deploy com **GitHub Actions** para garantir que o código seja testado e implantado automaticamente a cada alteração.
- **Kubernetes**: Containerizar a aplicação com **Docker** e gerenciar o deploy em **Kubernetes** para garantir escalabilidade e disponibilidade.

