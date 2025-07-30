
## 1. S - Single Responsibility Principle

- Por que existe?
>Se uma classe tem muitas responsabilidades, qualquer mudança em uma delas pode quebrar as outras. Isso gera **acoplamento excessivo**, dificultando manutenção e testes.

- Exemplo ruim (classe com muitas responsabilidades)
```Java
class RelatorioService {
    public void gerarRelatorio() {
        System.out.println("Gerando relatório...");
    }
    public void salvarBanco() {
        System.out.println("Salvando no banco de dados...");
    }
    public void enviarEmail() {
        System.out.println("Enviando email...");
    }
}
```
**Problema**: Essa classe gera, salva e envia. Se mudar a forma de envio, afeta o relatório.

- Exemplo correto
```Java
class GeradorRelatorio {
    public void gerar() {
        System.out.println("Gerando relatório...");
    }
}

class RelatorioRepository {
    public void salvarBanco() {
        System.out.println("Salvando no banco...");
    }
}

class RelatorioEmailSender {
    public void enviarEmail() {
        System.out.println("Enviando email...");
    }
}
```
**Cada classe tem uma única responsabilidade.** 

- Quando usar?
Sempre que perceber que uma classe está fazendo coisas demais.

---

## 2. O - Open/Close Principle

> Classes devem estar abertas para extensão, mas fechadas para modificação.

- Por que existe?
Se você precisar alterar código antigo para adicionar novas funcionalidades, corre risco de quebrar algo. O ideal é extender o comportamento sem tocar no código base.

- Exemplo ruim
```Java
class CalculadoraDesconto {
    public double calcular(String tipoCliente, double valor) {
        if (tipoCliente.equals("VIP")) {
            return valor * 0.9;
        } else if (tipoCliente.equals("REGULAR")) {
            return valor * 0.95;
        }
        return valor;
    }
}
```
Se aparecer um novo tipo de cliente, você terá que modificar a classe.

- Exemplo correto
```Java
interface RegraDesconto {
    double aplicar(double valor);
}

class DescontoVIP implements RegraDesconto {
    public double aplicar(double valor) {
        return valor * 0.9;
    }
}

class DescontoRegular implements RegraDesconto {
    public double aplicar(double valor) {
        return valor * 0.95;
    }
}

class CalculadoraDesconto {
    public double calcular(RegraDesconto regra, double valor) {
        return regra.aplicar(valor);
    }
}
```
Se surgir um novo desconto, você cria outra classe, sem modificar o código existente.

---

## 3. L - Liskov Substitution Principal

> Subtipos devem poder substituir seus tipos base sem alterar o funcionamento esperado.

- Por que existe?
Se você herda de uma classe, o comportamento não deve ser quebrado. Um objeto da subclasse deve ser usável no lugar do objeto da superclasse.

- Exemplo ruim
```Java
class Ave {
    public void voar() {
        System.out.println("Voando...");
    }
}

class Pinguim extends Ave {
    @Override
    public void voar() {
        throw new UnsupportedOperationException("Pinguins não voam!");
    }
}
```
`Pinguim` não pode substituir `Ave` sem quebrar o código.

- Exemplo correto
```Java
interface Ave {
    void emitirSom();
}

interface AveQueVoa extends Ave {
    void voar();
}

class Andorinha implements AveQueVoa {
    public void emitirSom() { System.out.println("Piu piu!"); }
    public void voar() { System.out.println("Voando!"); }
}

class Pinguim implements Ave {
    public void emitirSom() { System.out.println("Glu glu!"); }
}
```
Agora `Pinguim` não é obrigado a voar, respeitando o LSP.

---

## 4. I - Interface Segregation Principle

> Nenhum cliente deve ser forçado a depender de métodos que não fazem sentido para elas.

- Exemplo ruim (Interface gorda)
```Java
interface Funcionario {
    void programar();
    void testar();
    void gerenciar();
}

class Desenvolvedor implements Funcionario {
    public void programar() {}
    public void testar() {}
    public void gerenciar() { 
        throw new UnsupportedOperationException("Não gerencio nada!");
    }
}
```
O desenvolvedor é forçado a implementar `gerenciar()` sem precisar.

- Exemplo correto (interfaces pequenas)
```Java
interface Programador {
    void programar();
}

interface Testador {
    void testar();
}

interface Gerente {
    void gerenciar();
}

class Desenvolvedor implements Programador, Testador {
    public void programar() {}
    public void testar() {}
}
```
Cada classe implementa só o que precisa.

---

## 5. D - Dependency Inversion Principal

> Dependa de abstrações, não de implementações concretas.

- Por que existe?
Se você depende diretamente de classes concretas, trocar a implementações é difícil. Depender de interfaces ou abstrações torna o código mais flexível.

- Exemplo ruim (dependência direta)
```Java
class MySQLDatabase {
    void salvar(String dado) { System.out.println("Salvando no MySQL"); }
}

class UsuarioService {
    private MySQLDatabase db = new MySQLDatabase();
    void cadastrar(String usuario) {
        db.salvar(usuario);
    }
}
```
Se mudar o banco para PostgreSQL, você quebra `UsuarioService`.

- Exemplo correto (inversão de dependência)
```Java
interface Database {
    void salvar(String dado);
}

class MySQLDatabase implements Database {
    public void salvar(String dado) { System.out.println("MySQL: " + dado); }
}

class PostgreSQLDatabase implements Database {
    public void salvar(String dado) { System.out.println("Postgres: " + dado); }
}

class UsuarioService {
    private final Database db;
    public UsuarioService(Database db) { this.db = db; }
    void cadastrar(String usuario) { db.salvar(usuario); }
}

public class Main {
    public static void main(String[] args) {
        Database banco = new PostgreSQLDatabase(); // posso trocar por MySQL sem mudar UsuarioService
        UsuarioService service = new UsuarioService(banco);
        service.cadastrar("Pedro");
    }
}
```
Agora você pode mudar o banco sem alterar o serviço.

---

## Resumo

- S: Facilita manutenção -> classes focadas em uma só coisa.
- O: Evita quebrar código antigo ao adicionar novos comportamentos.
- L: Garante que herança faça sentido.
- I: Interfaces mais claras e específicas.
- D: Código mais flexível e testável.


