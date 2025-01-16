
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

## Inserção na Árvore

- **Inserção Inicial**:  
  Todo nó recém-inserido na árvore é, por padrão, **vermelho**.  

- **Ajustes Pós-Inserção**:  
  Após a inserção, são realizadas operações na árvore para garantir que todas as cinco propriedades mencionadas sejam preservadas.  
