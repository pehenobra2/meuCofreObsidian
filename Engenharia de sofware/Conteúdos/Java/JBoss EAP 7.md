
O **JBoss EAP 7** (Enterprise Application Platform) é um servidor de aplicações [[Java EE]] desenvolvido pela **Red hat**. Ele é baseado no projeto de código aberto **WildFly** e oferece uma plataforma robusta para desenvolvimento, implantação e gerenciamento de aplicações empresariais.

---

## 1. Principais Características ✨

### 1.1 Suporte a [[Java EE]] 7 ☕

O JBoss EAP 7 é compatível com [[Java EE]] 7, permitindo o desenvolvimento de aplicações modernas e escaláveis.

### 1.2 Alta Performance ⚡

- Inicialização rápida e baixo consumo de memória.
- Melhorias no gerenciamento de conexões e execução assíncrona.

### 1.3 Arquitetura Modular 📐

- Baseado no sistema JBoss Modules, que carrega apenas os módulos necessários, otimizando o desempenho.

### 1.4 Integração com [[CDI]], [[JSF]] e [[PrimeFaces]] 🔗

- Suporte nativo para [[CDI]], [[JSF]] e frameworks como [[PrimeFaces]], tornando o desenvolvimento web mais ágil.

## 1.5 Suporte a Cloud e Microservices ☁️

- Integração com Docker, Kubernetes e OpenShift.
- Suporte para arquiteturas baseadas em microservices.

---

## 2. Exemplo de Estrutura de Projeto 📂

Abaixo está um exemplo de estrutura de um projeto [[Java EE]] rodando no JBoss EAP 7:
```
meu-projeto/
│── src/main/java/
│   ├── com.exemplo.controle/   # Beans Gerenciados (CDI)
│   │   ├── UsuarioBean.java
│   ├── com.exemplo.modelo/     # Modelos de Dados (Entidades JPA)
│   │   ├── Usuario.java
│   ├── com.exemplo.service/    # Serviços e Regras de Negócio
│   │   ├── UsuarioService.java
│── src/main/webapp/
│   ├── WEB-INF/
│   │   ├── beans.xml           # Ativa CDI
│   │   ├── faces-config.xml    # Configuração JSF
│   ├── index.xhtml             # Página Inicial
│── pom.xml                     # Dependências Maven
│── standalone.xml              # Configuração do Servidor JBoss
```

---

## 3. Implantação no JBoss EAP 7 🛠️

Para rodar sua aplicação no JBoss EAP, siga os passos:
1. Baixar o JBoss EAP 7 no site da Red hat.
2. Iniciar o servidor com:
```sh
./standalone.sh
```
3. Fazer o deploy da aplicação:
	1. Copiar o `.war` para a pasta `standalone/deployments/`
	2. Ou usar o CLI:
```sh
jboss-cli.sh --connect
deploy meu-projeto.war
```

---
