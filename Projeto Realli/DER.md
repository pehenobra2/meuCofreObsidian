## **Entidades e Relacionamentos**

### 1. **Cliente**
   - **Atributos**:
     - `id_cliente` (PK) — Identificador único do cliente.
     - `nome` — Nome completo do cliente.
     - `email` (único) — E-mail único do cliente.
     - `senha` — Senha do cliente, criptografada.
     - `telefone` — Número de telefone do cliente.
     - `endereco` — Endereço de entrega do cliente.
     - `data_cadastro` — Data de registro do cliente no sistema.
   - **Relacionamentos**:
     - Um cliente pode ter **vários carrinhos** e **mensagens enviadas via WhatsApp**.

### 2. **Produto**
   - **Atributos**:
     - `id_produto` (PK) — Identificador único do produto.
     - `nome` — Nome do produto.
     - `descricao` — Descrição detalhada do produto.
     - `preco` — Preço do produto.
     - `categoria` — Categoria à qual o produto pertence (e.g., alimentos, bebidas, etc.).
     - `imagem` — URL ou caminho da imagem do produto.
     - `ativo` (booleano) — Status indicando se o produto está disponível para compra.
     - `data_criacao` — Data de criação do produto.
     - `data_atualizacao` — Data da última atualização do produto.
   - **Relacionamentos**:
     - O produto pode estar presente em vários **carrinhos** e gerar **relatórios de vendas**.

### 3. **Carrinho**
   - **Atributos**:
     - `id_carrinho` (PK) — Identificador único do carrinho.
     - `id_cliente` (FK) — Identificador do cliente associado ao carrinho.
     - `valor_total` — Total acumulado no carrinho com base nos produtos e quantidades.
     - `data_criacao` — Data de criação do carrinho.
     - `data_atualizacao` — Data da última atualização do carrinho.
   - **Relacionamentos**:
     - Um **cliente** pode ter **vários carrinhos** ao longo do tempo.
     - O carrinho está relacionado a **vários produtos**, armazenados na tabela `Produto_Carrinho`.

### 4. **Produto_Carrinho**
   - **Atributos**:
     - `id_produto` (FK) — Identificador do produto no carrinho.
     - `id_carrinho` (FK) — Identificador do carrinho.
     - `quantidade` — Quantidade do produto no carrinho.
     - `preco_unitario` — Preço unitário do produto no momento em que foi adicionado ao carrinho.
   - **Relacionamentos**:
     - Relacionamento **N:M** entre **Produto** e **Carrinho**.
     - A quantidade e o preço unitário do produto no carrinho são específicos para cada combinação de carrinho e produto.

### 5. **Administrador**
   - **Atributos**:
     - `id_admin` (PK) — Identificador único do administrador.
     - `email` (único) — E-mail único para login.
     - `senha` — Senha do administrador, criptografada.
     - `nome` — Nome completo do administrador.
     - `data_criacao` — Data de criação da conta administrativa.
   - **Relacionamentos**:
     - O **administrador** tem acesso a todas as funcionalidades de gerenciamento de **produtos** e pode gerar **relatórios de vendas**.

### 6. **Mensagem WhatsApp**
   - **Atributos**:
     - `id_mensagem` (PK) — Identificador único da mensagem.
     - `id_cliente` (FK) — Identificador do cliente que enviou a mensagem.
     - `id_produto_carrinho` (FK) — Relacionamento com os produtos do carrinho, para detalhar quais itens estão sendo negociados.
     - `mensagem` — Texto da mensagem enviada via WhatsApp.
     - `data_envio` — Data e hora em que a mensagem foi enviada.
   - **Relacionamentos**:
     - Cada **cliente** pode ter várias **mensagens** enviadas através do WhatsApp relacionadas aos produtos em seus carrinhos.

### 7. **Relatório de Vendas**
   - **Atributos**:
     - `id_relatorio` (PK) — Identificador único do relatório.
     - `data_inicio` — Data inicial do período de vendas.
     - `data_fim` — Data final do período de vendas.
     - `id_produto` (FK) — Identificador do produto relacionado ao relatório.
     - `quantidade_vendida` — Quantidade do produto vendida no período.
     - `valor_total_vendas` — Valor total das vendas do produto no período.
   - **Relacionamentos**:
     - O **relatório** está relacionado aos **produtos** vendidos, permitindo ao **administrador** monitorar o desempenho de vendas de produtos em determinado período.

---

## **Relacionamentos**

- **Cliente → Carrinho (1:N)**: Cada cliente pode ter vários carrinhos, mas um carrinho pertence a um único cliente. O carrinho é criado quando o cliente adiciona produtos e começa a fazer compras.
  
- **Carrinho → Produto_Carrinho (1:N)**: Um carrinho pode conter vários produtos, com quantidades e preços individuais. O relacionamento **N:M** entre **Produto** e **Carrinho** é modelado pela tabela `Produto_Carrinho`, onde o preço e a quantidade são armazenados para cada combinação de produto e carrinho.

- **Produto → Produto_Carrinho (1:N)**: Cada produto pode aparecer em vários carrinhos, com preços e quantidades variáveis.

- **Cliente → Mensagem WhatsApp (1:N)**: Um cliente pode ter várias mensagens enviadas via WhatsApp. Essas mensagens são geradas quando o cliente opta por finalizar a compra, com os produtos do carrinho sendo enviados para negociação.

- **Produto → Relatório de Vendas (1:N)**: Cada produto pode estar presente em vários relatórios de vendas, nos quais o administrador pode consultar a quantidade vendida e o total gerado em vendas para um determinado período.

- **Administrador → Produto (1:N)**: O administrador tem a capacidade de gerenciar os **produtos**. Ele pode cadastrar, editar, ativar ou desativar produtos, mas não pode deletá-los. Ele tem controle total sobre o catálogo de produtos.

---
