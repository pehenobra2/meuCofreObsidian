## 1. O que é❓

JDBC (Java Database Connectivity) é uma API do Java que permite a comunicação entre aplicações Java e bancos de dados relacionais. Ele fornece um conjunto de calsses e interfaces para conectar-se a um banco de dados, executar consultas [[SQL]] e manipular dados.

---

## 2. Principais Componentes do JDBC 🧩

1. **Driver JDBC**: Permite a comunicação entre o Java e o banco de dados específico. Existem diferentes tipos de drivers JDBC, como JDBC-ODBC Bridge, drivers nativos e drivers puramente Java.
2. **Connection**: Representa a conexão com o banco de dados.
3. **Statement**: Interface para executar comandos [[SQL]].
4. **ResultSet**: Representa o conjunto de resultados retornado por uma consulta [[SQL]].

---

## 3. Exemplo Simples de Uso do JDBC 🖥️

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

public class JDBCExample {
    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost:3306/meuBanco"; // URL do banco de dados
        String user = "usuario";
        String password = "senha";

        try {
            // Conectar ao banco
            Connection conn = DriverManager.getConnection(url, user, password);
            Statement stmt = conn.createStatement();
            
            // Executar consulta
            ResultSet rs = stmt.executeQuery("SELECT * FROM clientes");
            
            // Processar resultados
            while (rs.next()) {
                System.out.println("ID: " + rs.getInt("id") + ", Nome: " + rs.getString("nome"));
            }

            // Fechar conexões
            rs.close();
            stmt.close();
            conn.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```
Esse código conecta-se a um banco MySQL, executa uma consulta e imprime os resultados.