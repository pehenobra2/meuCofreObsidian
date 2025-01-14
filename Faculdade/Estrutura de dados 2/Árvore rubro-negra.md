Uma **árvore rubro-negra**(ou Red-Black Tree) é uma estrutura de dados baseada em árvore binária de busca que contém seu balanceamento de forma eficiente, garantindo, que a altura da árvore seja sempre proporcional ao logaritmo de número de nós. Isso assegura que as operações de busca, inserção e remoção tenham um desempenho próximo de $O(log n)$.

### Propriedades
- **Cada nó é vermelho ou preto**: Isso ajuda a controlar o balanceamento da árvore
- **A raiz é sempre preta**: Isso garante que a propriedade de balanceamento comece a partir do topo
- **Nó vermelho não pode ter um filho vermelho** (propriedade de não consecutividade): Isso evita longas cadeias de nós vermelhos
- **Todo caminho de um nó até suas folhas descendentes nulas contém o mesmo número de nós pretos**: Isso é chamado de *black height* e assegura o balanceamento
- **Nós nulos (ou folhas externas) são considerados pretos**: Essas folhas ajudam a simplificar as regras

### Exemplo

![](https://upload.wikimedia.org/wikipedia/commons/thumb/6/66/Red-black_tree_example.svg/500px-Red-black_tree_example.svg.png)

- Observe que:
	- Não há dois nós vermelhos consecutivos
	- O número de nós pretos em todos os caminhos é o mesmo

### Operações

#### 1. Inserção

Quando um nó é inserido, ele é inicialmente colocado como vermelho. Se isso violar alguma regra, são realizadas operações de **rotação** e/ou **mudança de cores** para restaurar o balanceamento.

