
## 1. Extrair método

- Situação: você tem um fragmento de código que pode ser agrupado em um método.
- Solução: transformar o fragmento em um método cujo nome explica o propósito do método
- Motivação: Métodos que são longos demais ou que necessitam de comentários para explicar, são sujeitos a essa refatoração.

3 possíveis situações:
- Trecho extraído não tem variáveis temporárias:
	- Caso mais simples, o trecho é encapsulado em um método sem parâmetros e sem retorno
- Trecho extraído usa variáveis locais que ficaram na origem do código
	- Variáveis locais que não foram declaradas no código extraído devem ser passadas como parâmetros para o novo método.
- Trecho extraído atribui valor a variável local na origem do código.
	- Variável local que tinha valor atribuído pelo código extraído, deverá receber tal valor como retorno do novo método.
	- E se o código extraído tiver mais de um valor sendo atribuído a variáveis locais?
		- É um empecilho para aplicar essa refatoração
		- Variáveis temporárias geralmente são problemáticas na aplicação de refatorações


1. Criar um novo método e nomeá-lo conforme sua intenção (nomeie-o pelo que ele faz, e não como ele faz);
2. Copiar o código extraído do método de origem para o novo método;
3. Procurar no método extraído por referência para variáveis locais declaradas no escolpo do método de origem. Elas serão variáveis locais e parâmetros para o novo método;
4. Verificar se as variáveis temporárias são usada apenas dentro do código extraído. Se sim, declará-las como variáveis temporárias no novo método;
5. Procurar no código extraído variáveis locais que são modificadas no código. Se uma variável local é modificada, verificar se pode tratar o código como uma consulta e atribuir o resultado à variável em questão;
	1. Se isto for estranho ou há mais de uma utilização da variável temporária, o método não poderá ser extraído como ele está. Deve-se usar refatoração **Dividir variável temporária**.
6. Passar como parâmetros para o método-alvo, variáveis de escopo local que são lidas do código extraído;
7. Compilar quando todas as variáveis de escopo local foram tratadas;
8. Substituir o código extraído no método fonte por uma chamada ao método-alvo;
	1. Se quaisquer variáveis temporárias foram movidas para o método novo, verificar se elas foram declaradas fora do método novo. Se sim, remover a declaração
9. Compilar e testar


## 2. Introduzir método

- Situação: O corpo do método é tão claro quanto seu nome
- Solução: Introduza o corpo do método no corpo daqueles que o chama e remova o método.
- Motivação: Apesar de métodos com nomes claros serem bons, às vezes seu corpo já é claro o suficiente e não é necessário torná-lo um método. Portanto, pode-se excluir um nível de indireção ao excluir este método.
