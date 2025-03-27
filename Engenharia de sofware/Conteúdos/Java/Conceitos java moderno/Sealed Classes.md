As **Sealed Classes** foram introduzidas no **Java 15 (preview)** e ficaram estáveis no **Java 17**. Elas oferecem um novo **controle sobre herança**, permitindo especificar **quais classes podem estender uma superclasse**.

Elas são úteis para **garantir a segurança do design**, **melhorar a legibilidade do código** e **otimizar o desempenho**.

## 1. Como funciona uma Sealed Class?

- Uma classe selada (`sealed`) define um conjunto fixo de subclasses que podem estendê-la.
- Qualquer outra classe fora dessa lista será impedida de herdar a superclasse.

**Exemplo:**
```java
sealed class Forma permits Circulo, Retangulo {}

final class Circulo extends Forma {}
final class Retangulo extends Forma {}
```

✔ **Agora, apenas `Circulo` e `Retangulo` podem estender `Forma`!**  
❌ **Qualquer outra tentativa de herança resultará em erro de compilação.**

---

## 2. Modificadores Permitidas para Subclasses

As subclasses de uma **Sealed Class** devem ser **explicitamente** marcadas com um dos três modificadores:

| **Modificador** | **O que faz?**                                               | **Exemplo**                                  |
| --------------- | ------------------------------------------------------------ | -------------------------------------------- |
| `final`         | **Impede** que haja mais subclasses.                         | `final class Circulo extends Forma {}`       |
| `sealed`        | **Permite** herança, mas apenas para subclasses específicas. | `sealed class Figura permits Quadrado {}`    |
| `non-sealed`    | **Permite herança livremente** (como uma classe normal).     | `non-sealed class Poligono extends Forma {}` |

---

## 3. Exemplo com todos os modificadores

```java
// Superclasse selada que só permite Circulo e Retangulo herdarem dela.
sealed class Forma permits Circulo, Retangulo, Poligono {}

// Não pode ter subclasses (final)
final class Circulo extends Forma {}

// Pode ser herdado apenas por Quadrado (sealed)
sealed class Retangulo extends Forma permits Quadrado {}

final class Quadrado extends Retangulo {}

// Pode ser herdado por qualquer classe (non-sealed)
non-sealed class Poligono extends Forma {}

class Triangulo extends Poligono {} // ✅ Permitido
class Hexagono extends Poligono {} // ✅ Permitido
```

✔ **`Circulo` e `Quadrado` são `final`, então não podem ter subclasses.**  
✔ **`Retangulo` é `sealed`, permitindo apenas `Quadrado` como subclasse.**  
✔ **`Poligono` é `non-sealed`, então qualquer classe pode herdar dele.**

---

## 4. Benefícios das Sealed Classes

### 4.1. Maior controle sobre a Herança

Antes, **qualquer classe** poderia herdar de outra. Agora, com `sealed`, podemos **restringir** quem pode herdar.

### 4.2. Melhor Otimização pelo compilador

Como o compilador **conhece todas as subclasses de uma `sealed class`**, ele pode realizar otimizações **mais eficientes**.

Exemplo: Um **switch** com pattern matching pode ser mais rápido porque o compilador sabe **todas as possibilidades**.
```java
static double calcularArea(Forma forma) {
    return switch (forma) {
        case Circulo c -> Math.PI * Math.pow(10, 2);  // Exemplo fixo
        case Retangulo r -> 10 * 20;  // Exemplo fixo
    };
}
```

O compilador garante que todas as subclasses estão cobertas no switch!

### 4.3. Melhoria no Pattern Matching

Junto com **Pattern Matching for Switch (Java 17+),** as `sealed classes` tornam os **switches mais seguros e concisos**.

- Antes (Java 14 - sem pattern matching)
```java
if (forma instanceof Circulo) {
    Circulo c = (Circulo) forma;
    return Math.PI * Math.pow(10, 2);
} else if (forma instanceof Retangulo) {
    Retangulo r = (Retangulo) forma;
    return 10 * 20;
}
```

- Agora (Java 17+)
```java
return switch (forma) {
    case Circulo c -> Math.PI * Math.pow(10, 2);
    case Retangulo r -> 10 * 20;
};
```

---

## 5. Quando usar Sealed Classes?

**Use Sealed Classes Quando...** :
- Você quer **controlar quais classes podem herdar** de uma superclasse.
- Sua hierarquia de classes tem um **conjunto fixo e conhecido de subclasses**
- Você quer **melhorar a segurança e o design do código**.
- Você quer **permitir apenas algumas extensões específicas**, mas não todas.
- Você deseja **otimizar o desempenho**, especialmente em **switch expressions**.

---