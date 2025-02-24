## 🔷1. Introdução

Este documento descreve os requisitos funcionais e não funcionais do sistema da empresa Realli'di. O sistema permitirá que clientes visualizem e adicionem produtos ao carrinho, sendo encaminhados para o WhatsApp da empresa para negociar o preço e finalizar a compra. Também incluirá um painel administrativo para gestão de produtos e relatórios.

---

## 🔷2. Requisitos Funcionais (RF)

### 2.1. Cadastro e Autenticação de Usuários

- [ ] **RF001** - O sistema deve permitir o cadastro de clientes com nome, e-mail, senha e telefone.
- [ ] **RF002** - O usuário deve poder realizar login utilizando e-mail e senha.
- [ ] **RF003** - O sistema deve permitir a recuperação de senha via e-mail.
- [ ] **RF004** - O cliente deve poder editar seu perfil (nome, telefone, endereço).
- [ ] **RF005** - O administrador deve poder visualizar a lista de usuários cadastrados.

### 2.2. Catálogo de Produtos

- [ ] **RF006** - O sistema deve permitir que os administradores cadastrem produtos com nome, descrição, preço, imagem e categoria.
- [ ] **RF007** - O sistema deve permitir a exclusão e edição de produtos, acessível apenas ao administrador.
- [ ] **RF008** - O cliente deve poder visualizar a listagem de produtos na página de produtos.
- [ ] **RF009** - O cliente deve poder visualizar os detalhes de um produto ao clicar sobre ele.
- [ ] **RF010** - O cliente deve poder pesquisar produtos pelo nome.
- [ ] **RF011** - O cliente deve poder filtrar produtos por categoria.

### 2.3. Carrinho de Compras e WhatsApp

- [ ] **RF012** - O cliente deve poder adicionar produtos ao carrinho.
- [ ] **RF013** - O cliente deve poder remover produtos do carrinho.
- [ ] **RF014** - O sistema deve calcular automaticamente o valor total dos produtos no carrinho.
- [ ] **RF015** - O cliente deve poder clicar em um botão para ser encaminhado ao WhatsApp com a lista dos produtos selecionados.

### 2.4. Painel Administrativo

- [ ] **RF016** - O painel administrativo deve ser acessado pelo caminho `admin/login`.
- [ ] **RF017** - O administrador deve ter acesso a um painel com as seguintes funcionalidades:  
  - Gerenciamento de produtos (Adicionar, editar, ativar e desativar).  
  - Visualização de mensagens enviadas pelo WhatsApp.  
  - Geração de relatórios de vendas (Quantidade de produtos mais pedidos, histórico de negociações).

### 2.5. Segurança e Controle de Acesso

- [ ] **RF018** - O sistema deve garantir que apenas o administrador possa acessar o painel de administração.
- [ ] **RF019** - A autenticação deve ser realizada utilizando JWT.

---

## 🔷3. Requisitos Não Funcionais (RNF)

- [ ] **RNF001** - O sistema deve ser desenvolvido utilizando Spring Boot no backend.
- [ ] **RNF002** - O sistema deve ser desenvolvido utilizando React no frontend.
- [ ] **RNF003** - O banco de dados deve ser PostgreSQL.
- [ ] **RNF004** - O sistema deve utilizar Firebase Hosting para o frontend.
- [ ] **RNF005** - O backend deve ser hospedado no Railway ou Render.
- [ ] **RNF006** - A interface do usuário deve ser responsiva e adaptável para dispositivos móveis e desktop.
- [ ] **RNF007** - O sistema deve responder em menos de 2 segundos para qualquer requisição.
- [ ] **RNF008** - O sistema deve suportar até 10.000 acessos simultâneos sem degradação de desempenho.

---

## 🔷4. Regras de Negócio (RN)

### 4.1. Cadastro e Autenticação de Usuários

- [ ] **RN001** - Apenas clientes podem se cadastrar no sistema. O administrador será pré-definido no backend.
- [ ] **RN002** - Para se cadastrar, o cliente deve fornecer nome, e-mail, senha e telefone válidos.
- [ ] **RN003** - O e-mail informado no cadastro deve ser único.
- [ ] **RN004** - A senha deve ter no mínimo 8 caracteres, incluindo letras e números.
- [ ] **RN005** - O login deve ser realizado com e-mail e senha.
- [ ] **RN006** - O cliente pode recuperar a senha via e-mail, recebendo um link de redefinição.
- [ ] **RN007** - O cliente pode editar suas informações de perfil, mas não pode alterar seu e-mail.
- [ ] **RN008** - O administrador tem acesso ao painel administrativo, mas não pode ser excluído ou editado pelo sistema.

### 4.2. Catálogo de Produtos

- [ ] **RN009** - Somente o administrador pode cadastrar, editar, ativar ou desativar produtos.
- [ ] **RN010** - Cada produto deve conter nome, descrição, preço, categoria e imagem obrigatoriamente.
- [ ] **RN011** - Produtos só podem ser listados para os clientes se estiverem ativos.
- [ ] **RN012** - O cliente pode pesquisar produtos por nome ou filtrar por categoria.
- [ ] **RN013** - O sistema não permite a duplicação de nomes de produtos dentro da mesma categoria.

### 4.3. Carrinho de Compras e WhatsApp

- [ ] **RN014** - O cliente pode adicionar quantos produtos quiser ao carrinho.
- [ ] **RN015** - O sistema deve calcular automaticamente o valor total dos produtos no carrinho.
- [ ] **RN016** - O cliente pode remover qualquer item do carrinho antes de finalizar a compra.
- [ ] **RN017** - Ao clicar em "Finalizar compra", o sistema gera uma mensagem automática no WhatsApp contendo a lista de produtos e seus valores.
- [ ] **RN018** - A negociação de preços e o pagamento não acontecem no sistema, mas sim diretamente no WhatsApp com o vendedor.
- [ ] **RN019** - O carrinho do cliente não é salvo após o fechamento do site, a menos que o cliente esteja autenticado.

### 4.4. Painel Administrativo

- [ ] **RN020** - Apenas o administrador pode acessar o painel administrativo.
- [ ] **RN021** - O painel deve permitir ao administrador visualizar todos os produtos cadastrados e gerenciá-los.
- [ ] **RN022** - O painel deve permitir a geração de relatórios de negociações e produtos mais vendidos.
- [ ] **RN023** - O administrador pode visualizar o histórico de mensagens enviadas pelo WhatsApp.

### 4.5. Segurança e Controle de Acesso

- [ ] **RN024** - O sistema deve utilizar JWT para autenticação de usuários.
- [ ] **RN025** - O cliente não pode acessar nenhuma rota administrativa, mesmo que tente acessar via URL.
- [ ] **RN026** - As senhas devem ser armazenadas criptografadas no banco de dados.
- [ ] **RN027** - O backend deve validar todas as requisições, garantindo que apenas usuários autenticados possam acessar funcionalidades protegidas.
