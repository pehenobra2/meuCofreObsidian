## 1. O que é❓

O Hibernate é um framework de mapeamento objeto-relacional (**ORM - Object Relacional Mapping**) para Java. Ele facilita a interação entre aplicações Java e bancos de dados relacionais, permitindo que os desenvolvedores trabalhem com objetos Java em vez de escrever SQL manualmente.

## 2. Principais funções do Hibernate ✨

### 2.1. Mapeamento Objeto-Relacional (ORM)

- Transforma tabelas do banco de dados em classes Java e colunas em atributos.

### 2.2. Gerenciamento de Conexão com Banco de Dados

- Lida com a abertura e fechamento de conexões automaticamente.

### 2.3. Execução de consultas e Manipulação de Dados

- Permite realizar operações **CRUD (Create, Read, Update, Delete)** usando HQL (Hibernate Query Language) ou Criteria API.

### 2.4. Cache de Dados

- Melhora a performance armazenando objetos já consultados para evitar acessos repetidos ao banco.

### 2.5. Suporte a Transações

- Integra-se com o [[JPA]] (Java Persistence API) para gerenciar transações de forma eficiente.

---

## 3. Vantagens do Hibernate 🔺

- **Abstração do SQL**: Não precisa escrever SQL puro, pois o Hibernate gera as queries automaticamente.
- **Independência de Banco de Dados**: Suporta múltiplos bancos como MySQL, PostgreSQL, Oracle, etc, sem mudar o código.
- **Redução de Código Boilerplate**: Diminui o código necessário para interagir com o banco de dados.
- **Cache Interno**: Reduz o número de acessos ao banco, melhorando o desempenho.
- **Facilidade de Manutenção**: Permite que mudanças no banco sejam refletidas facilmente no código Java.

---

## 4. Desvantagens do Hibernate 🔻

- **Overhead de Performance**: O Hibernate adiciona uma camada extra, o que pode torná-lo mais lento que SQL puro em algumas situações.
- **Configuração Inicial Complexa**: Requer a definição de arquivos de configuração (`hibernate.cfg.xml` ou `persistence.xml`).

---

## 5. Exemplo Básico de Uso do Hibernate

### 5.1. Dependência no `pom.xml` (se usar Maven)

```xml
<dependency>
    <groupId>org.hibernate</groupId>
    <artifactId>hibernate-core</artifactId>
    <version>6.0.0</version>
</dependency>
```

### 5.2. Configuração (`persistence.xml`) 

```xml
<?xml version="1.0" encoding="UTF-8"?>
<persistence xmlns="http://xmlns.jcp.org/xml/ns/persistence" version="2.1">
    <persistence-unit name="meuPU">
        <provider>org.hibernate.jpa.HibernatePersistenceProvider</provider>

        <!-- Configuração da conexão com o banco de dados -->
        <properties>
            <property name="jakarta.persistence.jdbc.driver" value="com.mysql.cj.jdbc.Driver"/>
            <property name="jakarta.persistence.jdbc.url" value="jdbc:mysql://localhost:3306/meubanco"/>
            <property name="jakarta.persistence.jdbc.user" value="root"/>
            <property name="jakarta.persistence.jdbc.password" value="senha"/>

            <!-- Dialeto do Hibernate -->
            <property name="hibernate.dialect" value="org.hibernate.dialect.MySQLDialect"/>
            
            <!-- Geração automática do schema do banco -->
            <property name="hibernate.hbm2ddl.auto" value="update"/>
            
            <!-- Mostrar as queries SQL geradas pelo Hibernate -->
            <property name="hibernate.show_sql" value="true"/>
            <property name="hibernate.format_sql" value="true"/>
        </properties>
    </persistence-unit>
</persistence>
```
**Explicação dos campos**:
- `pesistence-unit name="meuPU"`: Define uma unidade de persistência, que pode ser usada para configurar [[EntityManager]].
- `<provider>org.hibernate.jpa.HibernatePersistenceProvider</provider>`: Especifica que o Hibernate será o provedor de persistência.
- `property name="jakarta.persistence.jdbc.driver" value="com.mysql.cj.jdbc.Driver"/>`: Driver [[JDBC]] do banco de dados.
- `property name="jakarta.persistence.jdbc.url" value="jdbc:mysql://localhost:3306/meubanco"/>`: URL de conexão com o banco.
- `<property name="jakarta.persistence.jdbc.user" value="root"/>`: Usuário do banco de dados.
- `<property name="jakarta.persistence.jdbc.password" value="senha"/>`: Senha do banco.
- `<property name="hibernate.dialect" value="org.hibernate.dialect.MySQLDialect"/>`: Define o dialeto SQL para o banco (no caso, MySQL).
- `<property name="hibernate.hbm2ddl.auto" value="update"/>`: Controla a criação/alteração automática do banco.
	- `update`: Atualiza o schema sem apagar os dados.
	- `create`: Apaga e recria o banco a cada execução.
	- `create-drop`: Igual a `create`, mas apaga ao encerrar a sessão.
	- `validade`: Apenas verifica se as tabelas já existem, sem modificar nada.
- `<property name="hibernate.show_sql" value="true"/>`: Exibe as queries SQL no console.
- `<property name="hibernate.format_sql" value="true"/>`: Formata as queries SQL para melhor leitura.

### 5.3. Criando uma Sessão e Salvando um Objeto

```java
import jakarta.persistence.*;

public class Main {
    public static void main(String[] args) {
        EntityManagerFactory emf = Persistence.createEntityManagerFactory("meuPU");
        EntityManager em = emf.createEntityManager();

        em.getTransaction().begin();
        Usuario usuario = new Usuario();
        usuario.setNome("Maria");
        usuario.setEmail("maria@email.com");
        em.persist(usuario);
        em.getTransaction().commit();

        em.close();
        emf.close();
    }
}
```

---