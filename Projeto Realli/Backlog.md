## 📌 **Épicos**
1. **Gerenciamento de Usuários**
2. **Catálogo de Produtos**
3. **Carrinho de Compras e Integração com WhatsApp**
4. **Painel Administrativo**
5. **Segurança e Controle de Acesso**
6. **Monitoramento e Desempenho**

---

## 📋 **Histórias de Usuário**

### 📌 1. Gerenciamento de Usuários

#### 🏷️ Cadastro e Autenticação
- **US001** - Como cliente, quero me cadastrar informando nome, e-mail, telefone e senha para acessar o sistema.
- **US002** - Como cliente, quero fazer login com meu e-mail e senha para acessar minha conta.
- **US003** - Como cliente, quero redefinir minha senha via e-mail caso eu a esqueça.
- **US004** - Como cliente, quero poder editar meu perfil para atualizar meus dados pessoais.
- **US005** - Como administrador, quero visualizar todos os usuários cadastrados.

### 📌 2. Catálogo de Produtos

#### 🏷️ Cadastro e Gerenciamento de Produtos
- **US006** - Como administrador, quero cadastrar um produto informando nome, descrição, preço, imagem e categoria.
- **US007** - Como administrador, quero editar as informações de um produto já cadastrado.
- **US008** - Como administrador, quero ativar ou desativar um produto sem precisar excluí-lo.
- **US009** - Como administrador, quero visualizar todos os produtos cadastrados no sistema.

#### 🏷️ Visualização e Pesquisa de Produtos
- **US010** - Como cliente, quero visualizar a lista de produtos disponíveis para compra.
- **US011** - Como cliente, quero visualizar os detalhes de um produto ao clicar sobre ele.
- **US012** - Como cliente, quero pesquisar produtos pelo nome.
- **US013** - Como cliente, quero filtrar produtos por categoria.

### 📌 3. Carrinho de Compras e Integração com WhatsApp

#### 🏷️ Adição e Remoção de Produtos
- **US014** - Como cliente, quero adicionar produtos ao meu carrinho de compras.
- **US015** - Como cliente, quero remover produtos do meu carrinho.
- **US016** - Como cliente, quero que o valor total do carrinho seja atualizado automaticamente.

#### 🏷️ Finalização da Compra
- **US017** - Como cliente, quero clicar em um botão para ser encaminhado ao WhatsApp da loja com a lista dos produtos do meu carrinho.
- **US018** - Como cliente, quero que o sistema gere automaticamente uma mensagem contendo os produtos escolhidos e seus preços.

### 📌 4. Painel Administrativo

#### 🏷️ Gestão de Produtos
- **US019** - Como administrador, quero acessar um painel administrativo para gerenciar os produtos.
- **US020** - Como administrador, quero visualizar a lista de produtos cadastrados no painel.

#### 🏷️ Gestão de Mensagens via WhatsApp
- **US021** - Como administrador, quero visualizar as mensagens enviadas pelos clientes via WhatsApp.

#### 🏷️ Relatórios
- **US022** - Como administrador, quero gerar relatórios de vendas por período.
- **US023** - Como administrador, quero visualizar os produtos mais vendidos.
- **US024** - Como administrador, quero visualizar o histórico de negociações realizadas pelo WhatsApp.

### 📌 5. Segurança e Controle de Acesso

- **US025** - Como administrador, quero acessar o painel administrativo apenas com credenciais válidas.
- **US026** - Como sistema, preciso garantir que apenas administradores possam acessar o painel de administração.
- **US027** - Como cliente, quero que minhas senhas sejam armazenadas de forma segura para evitar vazamentos.
- **US028** - Como sistema, preciso validar todas as requisições para garantir que apenas usuários autenticados acessem funcionalidades protegidas.

### 📌 6. Monitoramento e Desempenho

- **US029** - Como administrador, quero monitorar o desempenho do sistema com métricas de acessos e uso.
- **US030** - Como administrador, quero receber alertas caso o sistema apresente falhas ou lentidão.
- **US031** - Como sistema, quero garantir que todas as requisições sejam processadas em menos de 2 segundos.

---

## 🔍 **Critérios de Aceitação**

### ✅ Autenticação e Cadastro
- O cliente deve fornecer um e-mail único ao se cadastrar.
- A senha deve ter no mínimo 8 caracteres, incluindo letras e números.
- O administrador não pode ser cadastrado via interface pública.

### ✅ Catálogo de Produtos
- Apenas produtos ativos devem ser exibidos para os clientes.
- O sistema deve permitir a pesquisa de produtos por nome.
- O sistema deve permitir filtragem por categoria.

### ✅ Carrinho e WhatsApp
- O carrinho deve calcular automaticamente o total dos produtos.
- O link para WhatsApp deve ser gerado dinamicamente com os produtos selecionados.
- O sistema não salva o carrinho caso o usuário não esteja autenticado.

### ✅ Painel Administrativo
- O administrador deve ser autenticado para acessar o painel.
- O painel deve exibir a lista de produtos cadastrados.
- O relatório de vendas deve incluir data de início, data de fim, quantidade vendida e valor total.

### ✅ Segurança
- Todas as senhas devem ser armazenadas criptografadas.
- Apenas usuários autenticados podem acessar o sistema.
- O backend deve validar JWT antes de processar qualquer requisição protegida.

### ✅ Monitoramento e Desempenho
- O sistema deve suportar até 10.000 acessos simultâneos.
- O tempo de resposta das requisições deve ser inferior a 2 segundos.
- O administrador deve receber alertas em caso de falhas ou degradação de performance.
