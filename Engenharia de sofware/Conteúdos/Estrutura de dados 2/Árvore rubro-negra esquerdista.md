
![[Pasted image 20250123103951.png]]

Uma **Árvore Binária de Busca (ABB)** Rubro-Negra Esquerdista é uma estrutura de dados que segue as seguintes propriedades:  

1. **Cores dos Nós**:  
   - Cada nó da árvore é classificado como **vermelho** ou **preto**.  

2. **Raiz Preta**:  
   - O nó raiz da árvore sempre tem a cor **preta**.  

3. **Folhas Pretas**:  
   - Todas as folhas da árvore (representadas como nós `NULL`) são sempre **pretas**.  

4. **Restrições para Nós Vermelhos**:  
   - Se um nó é vermelho, ele deve atender aos seguintes critérios:  
     1. Ambos os seus filhos são **pretos**.  
     2. Ele é sempre um filho esquerdo.  

5. **Altura Negra**:  
   - Para qualquer nó, o número de nós **pretos** no caminho até qualquer folha descendente é o mesmo.  
     1. O próprio nó não é contado.  
     2. Este número constante é denominado **altura negra**.

Matematicamente, considerando $bh$ com altura negra:
- O número de nós internos satisfaz:  $n \geq 2^{bh} -1 \geq 2^{h/2} -1$ 
- A altura total é $O(log$ $n)$

---

## Implementação em C

### Definição dos Nós
```C
#include <stdio.h>
#include <stdlib.h>

typedef enum Cor {VERM, PRETO} Cor;

typedef struct No {
    int chave;
    Cor cor;
    struct No *esq, *dir;
} No;
```

### Funções Auxiliares
```C
int ehVerm(No *x){
	if(x != Null){
		return x->cor == VERM;
	}
	return 0;
}

int ehPreto(No *x){
	if(x != Null) return x->cor == PRETO;
	return 1;
}
```

### Operações Fundamentais

#### Rotações:

##### 1. Para Esquerda
![[Pasted image 20250123105753.png]]
```C
No* rot_esq(No* raiz){
	No* x = raiz->dir;
	raiz->dir = x->esq;
	x->esq = raiz;
	x->cor = raiz->cor;
	raiz->cor = VERM;
	return x;
}
```

##### 2. Para Direita
![[Pasted image 20250123110447.png]]
```C
No* rot_dir(No* raiz){
	No* x = raiz->esq;
	raiz->esq = x->dir;
	x->dir = raiz;
	x->cor = raiz->cor;
	raiz->cor = VERM;
	return x;
}
```

#### Subida de Cor

![[Pasted image 20250123110606.png]]
```C
void sobe_verm(No* raiz){
	raiz->cor = VERM;
	raiz->esq->cor = PRETO;
	raiz->dir->cor = PRETO;
}
```

---

## Inserção na Árvore

```C
No *corrige(No *r){
	if(ehPreto(r->esq) && ehVerm(r->dir)){
		r = rot_esq(r);
	}
	if(ehVerm(r->esq) && ehVerm(r->esq->esq)){
		r = rot_dir(r);
	}
	if(ehVerm(r->esq) && ehVerm(r->dir)){
		sobe_cor(r);
	}
	return r;
}


No *insere(No *r, int x){
	if(r != NULL){
		if(x < r->chave) r->esq = insere(r->esq, x);
		else if(x > r->chave) r->dir = insere(r->dir, x);

		r = corrige(r);
		return r;
	}else {
		No *novo = malloc(sizeof(No));
		novo->chave = x;
		novo->esq = novo->dir = NULL;
		novo->cor = VERM;
		return novo;
	}
}
```

---

## Casos de Inserção

### Caso 1: Inserindo no Filho Esquerdo

- Pai preto, filho direito preto

![[Pasted image 20250123113240.png]]

### Caso 2: Inserindo no Filho Direito

- Pai preto, filho esquerdo preto

![[Pasted image 20250123113355.png]]

### Caso 3: Pai vermelho, inserindo no Filho Direito

![[Pasted image 20250123113516.png]]

### Caso 4: Pai preto, Inserindo no Filho Esquerdo

![[Pasted image 20250123114302.png]]

### Caso 5: Pai preto, Inserindo no Filho Direito

![[Pasted image 20250123114355.png]]

### Corrigindo Problemas no Pai

- Se o filho direito for vermelho, rotacionamos para esquerda
![[Pasted image 20250123114538.png]]
- Se o filho esquerdo for vermelho, basta subir a cor
![[Pasted image 20250123114621.png]]
- Se o filho esquerdo e seu neto esquerdo forem vermelhos, rotacionamos para a direita
![[Pasted image 20250123114750.png]]






- **Inserção Inicial**:  
  Todo nó recém-inserido na árvore é, por padrão, **vermelho**.  

- **Ajustes Pós-Inserção**:  
  Após a inserção, são realizadas operações na árvore para garantir que todas as cinco propriedades mencionadas sejam preservadas.  


Consideramos $bh$ a altura negra da árvore. Há pelo menos $2^{bh}-1$ nós não-nulos na árvore.

A altura negra $bh$ é pelo menos a metade da altura $h$ da árvore.
- Não existe nó vermelho com filho vermelho
- O número de nós internos *n* é : $n >= 2^{bh} -1 >= 2^{h/2} -1$
- Ou seja: $h <= 2 log(n+1) = O(log n)$

---
## Código

```C
typedef enum Cor {VERM, PRETO};

typedef struct No{
	int chave;
	enum Cor cor;
	struct No *esq, *dir;
} No;

int ehVerm(No *x){
	if(x != Null){
		return x->cor == VERM;
	}
	return 0;
}

int ehPreto(No *x){
	if(x != Null) return x->cor == PRETO;
	return 1;
}
```


## Rotações para direita e para esquerda

### 1. Para esquerda



```C
No* rot_esq(No* raiz){
	No* x = raiz->dir;
	raiz->dir = x->esq;
	x->esq = raiz;
	x->cor = raiz->cor;
	raiz->cor = VERM;
	return x;
}
```


### 2. Para direita



```C
No* rot_dir(No* raiz){
	No* x = raiz->esq;
	raiz->esq = x->dir;
	x->dir = raiz;
	x->cor = raiz->cor;
	raiz->cor = VERM;
	return x;
}
```

## Subindo cor





## Inserção

Inserirmos como em uma ABB, mas precisamos manter as propriedades da árvore rubro-negra esquerdista.



### Caso 1

- Nó é preto
	- não sabemos a cor do seu pai
	- nem se ele é o filho esquerdo ou direito
- Filho direito é preto 
- Inserimos no filho esquerdo


### Caso 2

- Nó é preto
	- não sabemos a cor do seu pai
	- nem se ele é o filho esquerdo ou direito
- Filho esquerdo é preto
- Inserimos no filho direito


### Caso 3

- Nó é preto
	- não sabemos a cor do seu pai
	- nem se ele é o filho esquerdo ou direito
- Filho esquerdo é vermelho
- Inserimos o no filho direito


### Caso 4

- Nó é vermelho
	- seu pai é preto
	- é o filho esquerdo
- Inserimos no filho esquerdo


### Caso 5

- Nó é vermelho
	- seu pai é preto
	- é o filho esquerdo
- Inserimos no filho direito


## Resolvendo problemas no pai

Quais problemas sobraram para o pai resolver?
- Talvez o filho direito seja vermelho (não é esquerdista)
- Só poder ter acontecido por que a cor vermelha subiu

Se o filho esquerdo for preto, basta rotacionar para a esquerda


Se o filho esquerdo for vermelho, basta subir a cor


Quais problemas sobraram para o pai resolver?
- Talvez o filho esquerdo seja vermelho
- E o neto mais a esquerda seja vermelho


## Conclusão 

As árvores rubro negras esquerdistas suportam as seguintes operações:
- busca
- inserção
- remoção
todas em tempo $O(log$ $n)$ 

É uma variante da árvore rubro-negra com menos operações para corrigir a árvore na inserção e na remoção