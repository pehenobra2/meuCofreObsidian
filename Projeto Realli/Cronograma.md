## 🔷Fase 1: Planejamento e Análise

- [x] 1. Definição dos Requisitos
	- [x] Levantar funcionalidades essenciais para clientes e administradores
	- [x] Criar um documento de requisitos detalhado 
	- [x] Definir regras de negócio
- [x] 2. Definição do Modelo de Dados
	- [x] Criar o DER do banco de dados
	- [x] Definir tabelas

---

## 🔷Fase 2: Configuração Inicial

- [x] 1. Criar o repositório no GitHub e organizar as branches
- [ ] 2. Configurar o projeto backend com spring boot e conectar ao Postgresql
- [ ] 3. Criar o front com react e configurar roteamento
- [ ] 4. Definir a estrutura inicial das pastas no front e backend

---

## 🔷Fase 3: Desenvolvimento Backend

- [ ] 1. Criar os endpoints principais:
	- [ ] Cliente: Registro, login, edição de perfil
	- [ ] Produtos: Listagem, busca, detalhes.
	- [ ] Carrinho: Adicionar/remover produtos, calcular total
	- [ ] WhatsApp: Geração de link dinâmico com os produtos escolhidos.
	- [ ] Administração: CRUD de produtos, visualização de pedidos, geração de relatórios.
- [ ] 2. Implementar autenticação e autorização com JWT
- [ ] 3. Criar testes unitários e integração com JUnit
- [ ] 4. Documentação do back

---

## 🔷Fase 4: Desenvolvimento Frontend

- [ ] 1. Criar páginas e componentes reutilizáveis
- [ ] 2. Implementar fluxo de autenticação
- [ ] 3. Desenvolver as páginas:
	- [ ] Públicas: página inicial, listagem de produtos, detalhes do produto
	- [ ] Clientes: carrinho, botão para encaminhar produtos ao WhatsApp
	- [ ] Administração: Gerenciamento de produtos, histórico de negociações.
- [ ] 4. Integração chamadas à API usando Axios
- [ ] 5. Criar um design responsivo e intuitivo

---

## 🔷Fase 5: Testes e refinamento

- [ ] 1. Testes manuais e automatizados para backend e frontend
- [ ] 2. Ajustes de performance no backend
- [ ] 3. Revisão da UI/UX para melhorar a experiência do usuário

---

## 🔷Fase 6: Deploy e Monitoramento

- [ ] 1. Frontend:
	- [ ] Fazer o deploy no Firebase hosting
	- [ ] Configurar regras de segurança no firebase
- [ ] 2. Backend:
	- [ ] Deploy no Railway ou Render
	- [ ] Alternativamente, usar um servidor VPS (DigitalOcean ou AWS EC2)
	- [ ] Configurar monitoramento com Prometheus + Grafana + Alertmanager.

---