O desenvolvimento orientado a testes (TDD) é uma prática de desenvolvimento de software que enfatiza a escrita de testes antes do código funcional. Ele segue o ciclo **RED-GREEN-REFACTOR**, com técnicas específicas para guiar o desenvolvimento de código que passa nos testes.

## Ciclo Red-Green-Refactor

#### 1. Red
- Escreva um teste que falhe, pois a funcionalidade ainda não foi implementada
- Isso ajuda a focar nos requisitos do sistema
#### 2. Green
- Escreva o código mais simples que faz o teste passar
- Não se preocupe com otimização ou estrutura neste momento
#### 3. Refactor (Refatorar)
- Melhore o código enquanto mantém os teste verdes (passando)
- Isso garante que o código permaneça limpo e eficiente sem quebrar a funcionalidade

## Técnicas do TDD

#### 1. Falsificação
- Escreva um código mais simples possível para passar no teste, mesmo que ele não seja implementação correta ainda
- Exemplo: Retornar um valor fixo
``` Java
public int somar(int a, int b){
	return 42; // Falsificação: resposta fixa para passar no teste
}
```
#### 2. Duplicação
- Use lógica duplicada no início para que o teste passe, e depois remova a duplicação durante a refatoração
``` Java
public int somar(int a, int b){
	if(a == 1 && b == 1) return 2; // Duplicação específica para passar no teste
	return 0;
}
```
#### 3. Triangulação
- Use vários testes com diferentes entradas para obrigar o código a generalizar o comportamento corretamente
``` Java
public int somar(int a, int b){
	return a+b; // Generalização após diferentes testes
}
```

## Vantagens do TDD
- Garante que o código atenda aos requisitos desde o início
- Melhora a qualidade do código e reduz a chance de bugs
- Facilita a manutenção e refatoração do sistema

---

## Exercício de Fixação

#### 1. Enunciado
Desenvolva, utilizando as técnicas de TDD, o seguinte problema abaixo:

Dada uma string formada por combinações de abre e fecha parênteses, colchetes e chaves. Retorne se a string é balanceada (bem-formada).

Por exemplo, dada a string: $$([])[]({})$$Deve retornar true.
Dadas as strings :$$([))$$ ou   $$((()$$
Deve retornar false.

#### 2. Resolução

##### Passo 1: Criar o Teste (Red)
Primeiro, escrevemos um teste para verificar se uma string é balanceada. Como o método ainda não existe, o teste falhará.
```Java
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

public class ValidadorDeParantesesTest {

	@Test
	public void testStringBalanceada(){
		ValidadorDeParenteses validador = new ValidadorDeParenteses();
		assertTrue(validador.ehBalanceada("([])[]({})")); // Deve retornar true.
		assertFalse(validador.ehBalanceada("([))")); // Deve retornar false.
		assertFalse(validador.ehBalanceada("((()")); //Deve retornar false.
	}
}
```
Ao executar, o teste falha, porque o método ``ehBalanceada`` ainda não foi implementado.

##### Passo 2: Código mais simples (Green)
Criamos o método ``ehBalanceada`` retornando uma resposta fixa apenas para passar o teste inicial.
```Java
public class ValidadorDeParenteses {
	public boolean ehBalanceada(String s){
		return true; //Falsificação: sempre retorna true.
	}
}
```
Neste ponto, o teste para ``"([])[]({})"`` passará, mas o outros testes falharão.

##### Passo 3: Melhorar com Duplicação (Green)
Ajustamos o código para tratar casos específicos.
```Java
public class ValidadorDeParenteses(){
	public boolean ehBalanceada(String s){
		if(s.equals("([])[]({})")) return true; // Caso específico
		if(s.equals("([)]")) return false; // Caso específico
		if(s.equals("((()")) return false; // Caso específico
		return false;
	}
}
```
Agora todos os testes passam, mas o código ainda está específico demais.

##### Passo 4: Generalização com Triangulação (Refactor)
Generalizamos o código para lidar com qualquer string. Usamos uma pilha para verificar a estrutura balanceada.
```Java
import java.util.Stack;

public class ValidadorDeParenteses(){
	Stack<Character> pilha = new Stack<>();

	for(char c : s.toCharArray()){ //for-each
		if( c == '(' || c == '[' || c == '{'){
			pilha.push(c);
		}else{
			if(pilha.isEmpty()) return false;
			char topo = pilha.pop();
			if((c == ')' && topo != '(') ||
			   (c == ']' && topo != '[') ||
			   (c == '}' && topo != '{')) {
				   return false;
			}
		}
	} 
	return pilha.isEpmty(); // Pilha deve estar vazia se for bem-formada.
}
```

##### Resumo
1. Escrevemos testes primeiro para os casos fornecidos
2. Implementamos o código simples para passar nos testes
3. Generalizamos a solução após triangulação e refatoração
4. Adicionamos mais testes para validar a robustez do código