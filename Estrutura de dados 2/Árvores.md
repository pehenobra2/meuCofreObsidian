
### Definição

Uma árvore é uma estrutura de dados composta por um conjunto de nós interconectados, que obedece às seguintes propriedades:
- **Nó raiz**: Existe um nó especial, chamado nó raiz, que é o ponto de partida da árvore.
- ´**Estrutura hierárquica**: A árvore possui uma organização hierárquica, onde cada nó pode ter um ou mais nós filhos, e cada nó, exceto a raiz, tem um nó pai.
- **Caminhos únicos**: Para quaisquer dois nós distintos *a* e *b*, existe, no máximo, um caminho único entre eles, o que garante que não há ciclos na árvore.
![Árvore](https://www.alura.com.br/artigos/assets/estruturas-de-dados-introducao/imagem4.png)
*Figura 1: Representação de como funciona uma árvore, onde o nível 0 é o nó raiz, o nível 1 e 2 sendo os nós filhos, e o nível 3 sendo as folhas.*

---
### Árvore binária

Uma árvore binária é uma árvore em que cada nó tem no **MÁXIMO** 2 filhos (esquerdo e direito). Essa limitação torna as árvores binárias uma forma eficiente de armazenar e organizar dados.

#### Conceitos Fundamentais

- **Nó folha**: Um nó que não possui filhos é chamado de **folha** (Como representado no nível 3 da figura 1). 
- **Descendentes**: Dado um nó *x*, qualquer nó que possa ser alcançado a partir de *x*, seja pela subárvore à esquerda ou à direita, é considerado um **descendente** de *x*.
- **Estrutura recursiva**: Uma árvore binária é, por natureza, uma estrutura recursiva. Isso significa que, dado um nó *x* qualquer, tanto o nó *x* quanto seus descendentes formam uma árvore binária. Se *x* for o filho esquerdo (ou direito) de um nó *y* dizemos que a árvore com raiz em *x* é uma subárvore esquerda (ou direita) de *y*.
![[Pasted image 20250109120011.png]]
*Figura 2: Demonstração da definição de subárvores.*
- **Caminho e comprimento**:  O caminho entre dois nós *x* e *y* é a sequência de nós percorridos para ir de um nó ao outro. O **comprimento do caminho** é o número total de nós atravessados. 
- **Níveis e crescimento**: Os nós de uma árvore binária são organizados em níveis, numerados a partir de 0 (onde o nível 0 é a raiz, como mostrado na figura 1). O número máximo de nós em um nível *K* é $2^k$, o que faz com que a árvore cresça exponencialmente à medida que avançamos para níveis mais profundos

---
#### Propriedades de Árvores Binárias
- **Árvore completa**: Uma árvore binária é chama de **completa** quando todos os seus níveis, do nível 0 até o nível *K*, estão completamente preenchidos, contendo exatamente $2^k$ nós em cada nível.
- **Altura de um nó**: A **altura** de um nó é definida como a distância (medida em número de arestas) entre ele e o seu descendente mais afastado, ou seja, o nó folha mais distante.
- **Profundidade de um nó**: A profundidade de um nó é a distância entre ele e a raiz da árvore, medida em número de arestas. A raiz, por definição, possui profundamente igual a 0.
- **Árvore balanceada**: uma árvore binária é considerada **balanceada** se, para cada nó, as alturas de suas subárvores esquerda e direita diferem no máximo por 1, ou, de forma equivalente, se todas as folhas possuem profundidades próximas. Árvores balanceadas são desejáveis porque garantem eficiência em operações como busca, inserção e remoção. Em geral, a altura de uma árvore binária balanceada com *n* nós é aproximadamente $\log_2 n$, tornando essas operações rápidas, com complexidade *O (log n)*.


### Implementação

1.  Estrutura do nó
``` c
typedef struct no{
	int dado; //Valor armazenado no nó
	struct no *esq, *dir; //Ponteiros para subárvore esquerda e direita
}no;
```

2. Função para criar um novo nó
``` c
No* criarNo(int valor){
	No* novo = (No*)malloc(sizeof(No));
	novo->dado = valor;
	novo->esq = NULL;
	novo->dir = NULL;
	return novo;
}
```

3. Função para inserir um valor na árvore
``` c
No* inserir(No* raiz, int valor){
	if(raiz == NULL) {
		return criarNo(valor); //caso base: insere o nó
	}
	if(valor < raiz->dado){
		raiz->esq = inserir(raiz->esq, valor); // Insere na subárvore esquerda
	} else if (valor > raiz->dado){
		raiz->dir = inserir(raiz->dir, valor); // Insere na subárvore direita
	} 
	return raiz; // Retorna a raiz (inalterada)
}
```

4. Função para encontrar o menor valor em uma subárvore
``` c

No* menorValor(No* raiz) {
	No* atual = raiz;
	while (atual != NULL && atual->esq != NULL) { 
		atual = atual->esq; 
	} 
	return atual;
}
```
5. Função para remover um nó da árvore
``` c
No* remover(No* raiz, int valor){
	if(raiz == NULL){
		return NULL; // Nó não encontrado
	}

	if(valor < raiz->dado){
		raiz->esq = remover(raiz->esq, valor); // Busca na subárvore esquerda
	} else if(valor > raiz->dado){
		raiz->dir = remover(raiz->dir, valor); // Busca na subárvore direita	
	} else {
		// Caso 1: Nó folha
		if(raiz->esq == NULL && raiz->dir == NULL){
			free(raiz);
			return NULL;
		}
		//Caso 2: Um único filho
		else if(raiz->esq == NULL){
			No* temp = raiz->dir;
			free(raiz);
			return temp;
		} else if(raiz->dir == NULL){
			No* temp = raiz->esq;
			free(raiz);
			return temp;
		}
		// Caso 3: Dois filhos
		else {
			No* temp = menorValor(raiz->dir); //menor valor na subárvore direita
			raiz->dado = temp->dado; // Substitui pelo valor do sucessor
			raiz->dir = remover(raiz->dir, raiz->dado); // Remove o sucessor
		}
	}
	return raiz;
}
```

---
### Percurso em profundidade na árvore binária

O percurso em profundidade explora os nós de uma árvore descendo o máximo possível em uma subárvore antes de retroceder. Ele pode ser realizado em três ordens principais:

1. Pré-ordem
	Na pré-ordem, o nó atual é visitado antes de suas subárvores. A ordem é:
	1. Visite o nó atual
	2. Percorra a subárvore esquerda
	3. Percorra a subárvore direita

	#### Aplicações
	- Utilizado para copiar a estrutura da árvore
	- Recomendado quando é necessário processar o nó antes de suas subárvores

	#### Exemplos
	![[Pasted image 20250109143545.png]]
	- **Sequência resultante**: 50, 30, 20, 40, 70, 60, 80.


	![[Pasted image 20250109143755.png]]
	- **Sequência resultante**: 10, 5, 3, 4, 20, 15, 30, 40.


	#### Código
``` c
void pre_ordem(No* raiz){
	printf("%d", raiz->dado); //Visita o nó atual
	pre_ordem(raiz->esq); // Percorre a subárvore esquerda
	pre_ordem(raiz->dir); // Percorre a subárvore direita
}
```

2. Pós-ordem
	Na pós-ordem, o nó atual é visitado após de suas subárvores. A ordem é:
	1. Percorra a subárvore esquerda
	2. Percorra a subárvore direita
	3. Visite o nó atual

	#### Aplicações
	- Útil para apagar ou liberar memória da árvore
	- Recomendado para realizar cálculos em estruturas hierárquicas

	#### Exemplos
	![[Pasted image 20250109143545.png]]
	- **Sequência resultante**: 20, 40, 30, 60, 80, 70, 50.


	![[Pasted image 20250109143755.png]]
	- **Sequência resultante**: 4, 3, 5, 15, 40, 30, 20, 10.


	#### Código
``` c
void pos_ordem(No* raiz){
	pos_ordem(raiz->esq); // Percorre a subárvore esquerda
	pos_ordem(raiz->dir); // Percorre a subárvore direita
	printf("%d", raiz->dado); //Visita o nó atual
}
```


3. Em ordem
	Na em ordem, o nó atual é visitado entre as visitas às suas subárvores. A ordem é:
	1. Percorra a subárvore esquerda
	2. Visite o nó atual
	3. Percorra a subárvore direita

	#### Aplicações
	- Em uma árvore binária de busca (BST), o percurso em ordem resulta em uma lista ordenada
	- Útil para exibir os valores em ordem crescente

	#### Exemplos
	![[Pasted image 20250109143545.png]]
	- **Sequência resultante**: 20, 30, 40, 50, 60, 70, 80.


	![[Pasted image 20250109143755.png]]
	- **Sequência resultante**: 4, 3, 5, 10, 15, 20, 30, 40.


	#### Código
``` c
void em_ordem(No* raiz){
	em_ordem(raiz->esq); // Percorre a subárvore esquerda
	printf("%d", raiz->dado); //Visita o nó atual
	em_ordem(raiz->dir); // Percorre a subárvore direita
}
```

