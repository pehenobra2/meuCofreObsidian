
## 1. Conceito
![[Pasted image 20250128085941.png]]
*Figura 1*: Representando uma Max-Heap, mostrando que os elementos são partes de um vetor.

- É uma [[Árvores#Árvore binária|AB]] tal que a raiz é maior que os filhos. Ex:
![[Pasted image 20250128090116.png]]
*Figura 2*: Exemplo de uma Max-Heap.
- É sempre uma árvore binária completa, com exceção do último nível

Em um Max-Heap:
- Os filhos são menores ou iguais ao pai
- Ou seja, a raiz é máximo

Note que não é uma árvore binária de busca!
- E os dados estão bem menos estruturados
- Pois estamos interessados apenas no máximo

Dado `v[i]`, quem é o:
- Filho esquerdo?
	- $v[(2*i)+1]$
- Filho direito?
	- $v[(2*i)+2]$
- Pai?
	- $v[(i-1)/2]$

### 1.2 Código criar heap

```C
#define pai(i) ((i-1)/2);

typedef struct {
	int *v;
	int n, tam;
} heap;

heap *criaHeap(int tam){
	heap h = malloc(sizeof(heap));
	h->v = malloc(tam*sizeof(int));
	h->n = 0; h->tam = tam;
	return h;
}
```


---

## 2. Inserindo no Heap

Basta ir subindo no Heap, trocando como pai se necessário
- O irmão já é menor que o pai, não precisamos mexer nele

![[Pasted image 20250128084931.png]]
![[Pasted image 20250128085042.png]]
![[Pasted image 20250128085055.png]]
![[Pasted image 20250128085115.png]]

### 2.1 Código de inserir

```C
void insere(heap *h)
```