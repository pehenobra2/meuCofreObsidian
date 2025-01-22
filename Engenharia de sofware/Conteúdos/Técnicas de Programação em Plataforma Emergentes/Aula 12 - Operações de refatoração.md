
# Refatoração de Código

A refatoração de código é uma prática essencial para manter a manutenção e legibilidade do software. Abaixo, discutimos algumas importantes operações de refatoração: **Extrair Método**, **Introduzir Método**, **Mover Método**, **Mover Campo (Atributo)** e **Extrair Classe**.

## 1. Extrair Método

- **Situação:**  
  Quando você tem um fragmento de código que pode ser agrupado em um método.

- **Solução:**  
  Transformar o fragmento em um método cujo nome explica seu propósito.

- **Motivação:**  
  Métodos longos ou que necessitam de muitos comentários podem se beneficiar dessa refatoração, tornando o código mais modular e legível.

### 1.1 Possíveis Situações

- **Trecho extraído não tem variáveis temporárias:**  
  O trecho é encapsulado em um método sem parâmetros e sem retorno.
  
- **Trecho extraído usa variáveis locais da origem:**  
  Variáveis locais da origem devem ser passadas como parâmetros para o novo método.
  
- **Trecho extraído atribui valores a variáveis locais:**  
  A variável deve receber seu valor como retorno do novo método.  
  Se houver mais de uma variável sendo atribuída, essa refatoração pode se tornar mais complexa e exigir outras modificações, como a **Divisão de Variáveis Temporárias**.

### 1.2 Passos para Extrair um Método

1. Criar um novo método com um nome significativo.
2. Copiar o código extraído para o novo método.
3. Identificar e passar como parâmetros as variáveis locais usadas no trecho extraído.
4. Declarar variáveis temporárias dentro do novo método, se usadas apenas nele.
5. Tratar variáveis locais modificadas no código extraído. Caso haja dificuldades, pode ser necessário refatorar essas variáveis antes.
6. Compilar e testar.
7. Substituir o código original pela chamada ao novo método.
8. Remover declarações desnecessárias de variáveis.
9. Compilar e testar novamente.

### 1.3 Exemplo

- **Antes da Refatoração:**
```java
public void processarPedido() {
    double total = 0;
    for (Item item : itens) {
        total += item.getPreco() * item.getQuantidade();
    }
    System.out.println("Total do pedido: " + total);
}
```
- Depois da refatoração:
```java
public void processarPedido() {
    double total = calcularTotal();
    System.out.println("Total do pedido: " + total);
}

private double calcularTotal() {
    double total = 0;
    for (Item item : itens) {
        total += item.getPreco() * item.getQuantidade();
    }
    return total;
}
```

---

## 2. Introduzir Método

- **Situação:**  
  O corpo do método é tão simples quanto seu nome.

- **Solução:**  
  Substituir a chamada ao método diretamente pelo seu corpo e remover a definição do método.

- **Motivação:**  
  Embora a modularização seja benéfica, em alguns casos um método pode ser tão simples que adiciona complexidade desnecessária ao código. Reduzir esse nível de abstração torna o código mais direto e fácil de entender.

- **Outras Motivações:**
  - Métodos excessivamente pequenos que apenas delegam chamadas.
  - Código mal estruturado que pode ser refinado após essa refatoração.

### 2.1 Passos para Introduzir um Método

1. Verificar se o método não é polimórfico.
2. Encontrar todas as chamadas ao método.
3. Substituir cada chamada pelo corpo do método.
4. Remover a definição do método.
5. Compilar e testar.

### 2.2 Exemplo

- **Antes da Refatoração:**
```java
public void exibirMensagem() {
    System.out.println("Bem-vindo ao sistema!");
}

public void iniciar() {
    exibirMensagem();
}
```
- Depois da refatoração:
```java
public void iniciar() {
    System.out.println("Bem-vindo ao sistema!");
}
```

---

## 3. Mover Método

- **Situação:**  
  Um método é utilizado mais por outra classe do que pela sua própria classe.

- **Solução:**  
  Mover o método para a classe onde ele é mais relevante.

- **Motivação:**  
  Reduzir o acoplamento entre classes e melhorar a organização do código.

### 3.1 Passos para Mover um Método

1. Examinar os elementos usados pelo método:
   1. Identificar todos os atributos e métodos que o método acessa na classe original.
   2. Se esses elementos forem usados apenas pelo método que será movido, movê-los também.
   3. Se forem usados por outros métodos, avaliar se esses métodos também devem ser movidos.
2. Verificar a hierarquia de classes:
   1. Analisar se o método está presente em subclasses ou superclasses.
   2. Se houver declarações polimórficas do método, garantir que a movimentação não quebre o polimorfismo.
3. Criar o método na classe de destino, escolhendo um nome mais apropriado para o novo contexto.
4. Copiar o código original para o novo método na nova classe:
   1. Ajustar o código para garantir seu funcionamento na nova classe.
   2. Se o método acessar elementos da classe original, referenciá-los corretamente.
   3. Se necessário, passar o objeto da classe original como parâmetro para o novo método.
5. Tratar exceções, se necessário.
6. Compilar a nova classe e testar para garantir que o método funcione corretamente.
7. Determinar como referenciar a nova classe na classe original:
   1. Se já existir um campo ou método que armazene uma referência à nova classe, usá-lo.
   2. Caso contrário, criar um novo campo que armazene a referência à nova classe.
8. Transformar o método original em um método de delegação (se necessário):
   1. Se houver muitas referências ao método original, criar um método que apenas delegue a execução para o novo método.
9. Compilar e testar novamente.
10. Decidir se o método original deve ser removido ou mantido como delegação:
   1. Manter um método de delegação pode facilitar a migração gradual do código.
11. Se o método original for removido, atualizar todas as referências.

### 3.2 Exemplo

- **Antes da Refatoração:**
```java
class Pedido {
    public double calcularDesconto() {
        return total * 0.1;
    }
}

- Depois da refatoração:
```java
class Pedido {
    public double calcularDesconto() {
        return DescontoUtil.calcularDesconto(total);
    }
}

class DescontoUtil {
    public static double calcularDesconto(double total) {
        return total * 0.1;
    }
}
```

---

## 4. Mover Campo (Atributo)

- **Situação:**  
  Um campo é utilizado mais por outra classe do que pela classe em que está definido.

- **Solução:**  
  Mover o campo para a classe onde ele é mais relevante.

- **Motivação:**  
  Reduzir a dependência desnecessária entre classes e melhorar a coesão.

### 4.1 Passos para Mover um Campo

1. Se o campo for público, encapsulá-lo antes da movimentação:
   1. Utilizar a refatoração **Encapsular Campo**, criando métodos `get` e `set`.
   2. Se o campo for frequentemente acessado, considerar a refatoração **Auto-encapsulamento Campo**.
2. Compilar e testar para garantir que o encapsulamento esteja funcionando corretamente.
3. Criar o novo campo na classe de destino.
4. Compilar e testar a classe de destino (a nova classe).
5. Determinar como referenciar a nova classe na classe original:
   1. Se já existir um campo ou método na classe original que referencie a nova classe, utilizá-lo.
   2. Caso contrário, criar um novo campo ou método que retorne o objeto da nova classe.
   3. A referência pode ser temporária até que futuras refatorações permitam sua remoção.
6. Remover o campo da classe original.
7. Atualizar todas as referências ao campo original.
8. Compilar e testar novamente após cada alteração.

### 4.2 Exemplo
- Antes da refatoração:
```java
class Pedido {
    private Cliente cliente;
    private String enderecoEntrega;
}
```
- Depois da refatoração:
```java
class Pedido {
    private Cliente cliente;
}

class Cliente {
    private String enderecoEntrega;
}
```

---

## 5. Extrair Classe

- **Situação:**  
  Uma classe está lidando com mais responsabilidades do que deveria.

- **Solução:**  
  Criar uma nova classe e mover campos e métodos relevantes para ela.

- **Motivação:**  
  Melhorar a organização do código e seguir o princípio da responsabilidade única.

### 5.1 Passos para Extrair uma Classe

1. Identificar responsabilidades distintas dentro da classe original.
2. Criar uma nova classe para separar essas responsabilidades.
3. Usar a refatoração [[Aula 12 - Operações de refatoração#4. Mover campo (Atributo)|Mover Campo]] para transferir os campos apropriados para a nova classe.
4. Usar a refatoração [[Aula 12 - Operações de refatoração#3. Mover método|Mover Método]] para transferir os métodos relacionados para a nova classe.
5. Ajustar as referências para a nova classe.
6. Revisar a interface de cada classe e otimizar as dependências.
7. Compilar e testar para garantir que a refatoração foi bem-sucedida.

### 5.2 Exemplo

- Antes da refatoração:
```java
class Pessoa {
    private String nome;
    private String telefone;
    private String endereco;
}
```
- Depois da refatoração:
```java
class Pessoa {
    private String nome;
    private Contato contato;
}

class Contato {
    private String telefone;
    private String endereco;
}
```

---


