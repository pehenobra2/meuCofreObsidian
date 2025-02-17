
React é uma biblioteca JavaScript de código aberto, desenvolvida pelo Facebook, utilizada para criar interfaces de usuário (UI) dinâmicas e interativas para aplicações web e móveis. 

---

## 1. Como o React Funciona ❓

React é baseado em um conceito chamado componentização, que permite dividir a UI em pequenas partes reutilizáveis, chamadas de componentes. Esses componentes podem ser funcionais ou baseados em classes, e são responsáveis por renderizar e atualizar o conteúdo da interface de acordo com o estado da aplicação.

---

## 2. Principais Características do React ✨

1. **Declarativo**: Em vez de manipular diretamente o DOM (Document Object Model), o React permite que os desenvolvedores descrevam como a UI deve parecer em qualquer ponto do tempo. Quando o estado da aplicação muda, o React atualiza automaticamente a UI para refletir essas mudanças de forma eficiente.
2. **Componente baseado**: Tudo no React é um componente desde, elementos simples, como botões, até partes complexas, como páginas inteiras. Isso torna o código mais modular, reutilizável e fácil de testar.
3. **Virtual DOM**: O React utiliza um conceito chamado Virtual DOM para melhorar a performance. Ao invés de atualizar o DOM real diretamente sempre que há uma mudança, o React cria uma versão virtual do DOM, realiza as modificações necessárias, e então calcula as diferenças entre o Virtual DOM e o DOM real (esse processo é chamado de "reconcilation"). Somente as partes que mudaram são atualizadas, tornando o processo muito mais rápido.
4. **Unidirecionalidade de dados**: O fluxo de dados no React é unidirecional, ou seja, os dados fluem de cima para baixo, dos componentes pais para os filhos, o que ajuda a entender e controlar o estado da aplicação de forma mais previsível.
5. Uso do JSX: o React utiliza JSX (JavaScript XML), uma sintaxe que mistura HTML com JavaScript. Isso torna o código mais intuitivo e legível, pois permite escrever componentes de forma declarativa:
	1. Facilita a criação de interfaces dinâmicas.
	2. Permite inserir expreções JavaScript diretamente no HTML
```jsx
const Botao = () => <button>Clique Aqui</button>;
```


---

## 3. Principais Conceitos do React 🧩

### 3.1 Componentes

Os componentes no React podem ser funcionais (usando funções) ou baseado em classes (usando a sitaxe `classe`). Com a chegada do Hooks, que permitem adicionar estado e outros recursos a componentes funcionais, os componentes funcionais se tornaram mais populares.

### 3.2 Estado (State)

O estado é um objeto dentro de um componente que armazena dados que podem mudar ao longo do tempo. Quando o estado de um componente muda, o React atualiza automaticamente a UI para refletir a mudança.

### 3.3 Props

Props são propriedades passadas para componentes filhos de componentes pais. Elas são imutáveis e servem para passar dados ou funções de um componente para outro.

### 3.4 Hooks

Os Hooks são funções introduzidas no React 16.8 que permitem adicionar funcionalidades como estado e efeitos colaterais componentes funcionais, sem a necessidade de usar classes. Os Hooks mais comuns são:
- `useState`: Para declarar e atualizar o estado.
- `useEffect`: Para executar efeitos colaterais, como chamadas a APIs, após a renderização do componente.
- `useContext`: Para acessar o conteúdo global da aplicação.

---

## 4. Vantagens do React 🔺

- **Desempenho**: O uso do Virtual DOM e a atualização eficiente das partes modificadas da UI fazem do React uma escolha muito rápida e eficiente.
- **Modularidade e Reutilização**: Componentes reutilizáveis tornam o código mais organizado e fácil de manter.
- **Ecossistema Rico**: O React tem uma comunidade ativa e um vasto ecossistema de ferramentas e bibliotecas, como o React Router (para navegação), Redux ou Context API (para gerenciamento de estado), entre outras.
- **Facilidade de integração**: O React pode ser facilmente integrado a outras bibliotecas ou frameworks, e é usado tanto em aplicações de uma única página (SPA) quanto em projetos mais complexos.

---

## 5. React Native 📱

Além de ser amplamente utilizado para desenvolvimento web, o React também possui uma versão chamada React Native, que permite criar aplicações móveis para IOS e Android com a mesma base de código JavaScript, utilizando componentes nativos.

---

## 6. Criando a primeira Aplicação com Create React app 🏗️

### 6.1 Instalando as Ferramentas Necessárias

Antes de começar, é necessário instalar:

- Visual Studio Code (VS code) - Editor de código recomendado.
- Node.js - Inclui o gerenciador de pacotes `npm`, necessário para instalar e rodar o React.

Após instalar o Node.js você pode verificar se a instalação foi bem-sucedida executando o seguinte comando no terminal:
```sh
node -v
```
Se aparecer a versão instalada, significa que está tudo certo!

### 6.2  Criando projeto React

Abra o terminal na pasta onde deseja criar o projeto e execute o seguinte comando:
```sh
npx create-react-app .
```
O processo pode levar alguns minutos. Quando a instalação estiver concluída, aparecerá a mensagem **"Happy hacking"** no terminal.

Agora, entre na pasta do projeto e inicie o servidor de desenvolvimento:
```sh
cd nome-do-projeto
npm start
```
Isso abrirá o navegador automaticamente em http://localhost:3000/, exibindo a aplicação React padrão.
### 6.3 Package.json

O arquivo `package.json` é criado automaticamente e contém:
- O nome e a versão do projeto.
- A lista de dependências necessárias para a aplicação.
- Os scripts disponíveis como `npm start` para rodar o servidor.
Exemplo de `package.json`:
```json
{
  "name": "meu-projeto",
  "version": "0.1.0",
  "dependencies": {
    "react": "^18.0.0",
    "react-dom": "^18.0.0"
  },
  "scripts": {
    "start": "react-scripts start"
  }
}
```
### 6.4 Estrutura da Pasta `src/`

Dentro dessa pasta, encontramos alguns arquivos essenciais:

1. `App.js` ➡️ O principal componente da aplicação, onde o código da interface é escrito.
2. `App.css` ➡️ O arquivo de estilos padrão aplicado ao `App.js`

Podemos editar o conteúdo de `App.js` para personalizar a interface inicial. Por exemplo:
```jsx
funcion App(){
	return <h1>Olá, React!</h1>
}

export default App;
```
Após salvar, a aplicação será atualizada automaticamente no navegador.

---

## 7. Funções JS 🚀

No react, as funções JS desempenham um papel fundamental na criação de componentes, manipulação de eventos e lógica da aplicação. Aqui estão alguns conceitos essenciais sobre funções em JS e como elas são utilizadas React:

### 7.1. Declaração de Funções

Existem várias formas de declarar funções em JS:

```js
// Função tradicional
function saudacao(nome) {
  return `Olá, ${nome}!`;
}

// Função anônima atribuída a uma variável
const saudacao2 = function (nome) {
  return `Olá, ${nome}!`;
};

// Arrow function (mais usada no React)
const saudacao3 = (nome) => `Olá, ${nome}!`;
```

### 7.2. Funções como Props

No React, podemos passar funções como propriedades para componentes filhos, permitindo a comunicação entre eles.

```jsx
const Botao = ({ aoClicar }) => <button onClick={aoClicar}>Clique aqui</button>;

const App = () => {
  const mostrarAlerta = () => alert("Botão clicado!");

  return <Botao aoClicar={mostrarAlerta} />;
};
```

### 7.3. Manipulação de Eventos

Eventos em React são tratados com funções, geralmente utilizando arrow functions para manter o contexto do `this`.

```jsx
const App = () => {
  const lidarComClique = () => {
    console.log("Botão foi clicado!");
  };

  return <button onClick={lidarComClique}>Clique aqui</button>;
};
```

### 7.4. Funções de Callback

No React, callbacks são usados em diversos momentos, como ao mapear listas ou lidar com eventos assíncronos.

```js
const numeros = [1, 2, 3, 4];
const dobrados = numeros.map((num) => num * 2); // [2, 4, 6, 8]
```

### 7.5. Funções Assíncronas

Com `async/await`, podemos lidar com operações assíncronas, como chamadas a APIs.

```jsx
const buscarDados = async () => {
  const resposta = await fetch("https://jsonplaceholder.typicode.com/todos/1");
  const dados = await resposta.json();
  console.log(dados);
};

buscarDados();
```

---
