
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

### 7.4. Iteração e Transformação de Arrays

No JavaScript, funções de callback são amplamente utilizadas para manipular arrays de forma eficiente. Algumas das funções mais comuns são:

- `.map()`: Cria um novo array transformando cada elemento do original.
```js
const numeros = [1, 2, 3, 4];
const dobrados = numeros.map(num => num * 2);
console.log(dobrados); // [2, 4, 6, 8]
```

- `.forEach()`: Executa uma função para cada elemento do array sem retornar um novo array.
```js
const nomes = ["Ana", "João", "Carlos"];
nomes.forEach(nome => console.log(nome));
```

- `.filter()`: Retorna um novo array contendo apenas os elementos que atendem a uma condição específica.
```js
const idades = [15, 30, 18, 22, 10];
const adultos = idades.filter(idade => idade >= 18);
console.log(adultos); // [30, 18, 22]
```

- `.reduce()`: Acumula os valores de um array em um único resultado.
```js
const numeros = [1, 2, 3, 4];
const soma = numeros.reduce((acumulador, atual) => acumulador + atual, 0);
console.log(soma); // 10
```

- `.find()`: Retorna o primeiro elemento do array que satisfaz uma condição.
```js
const produtos = [{nome: "Notebook", preco: 2000}, {nome: "Mouse", preco: 50}];
const caro = produtos.find(produto => produto.preco > 1000);
console.log(caro); // { nome: 'Notebook', preco: 2000 }
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

### 7.6. Outras Funções úteis em arrays

Além do `.map()`, `.forEach()`, `.filter()`, `.reduce()`e  `.find()`, temos:

- `.findIndex()`: Retorna o índice do primeiro elemento que satisfaz a condição.
```js
const frutas = ["maçã", "banana", "uva"];
const indice = frutas.findIndex(fruta => fruta === "banana");
console.log(indice); // 1
```

- `.some()`: Retorna `true` se **pelo menos um** elemento satisfizer a condição.
```js
const notas = [3, 5, 7, 9];
const temNotaBoa = notas.some(nota => nota >= 7);
console.log(temNotaBoa); // true
```

- `.every()`: Retorna `true` se **todos** os elementos passarem na condição.
```js
const alturas = [1.80, 1.75, 1.90];
const todosAltos = alturas.every(altura => altura > 1.70);
console.log(todosAltos); // true
```

- `.sort()`: Ordena os elementos do array.
```js
const numeros = [10, 2, 8, 30];
numeros.sort((a, b) => a - b);
console.log(numeros); // [2, 8, 10, 30]
```

- `.reverse()`: Inverte a ordem dos elementos.
```js
const letras = ["a", "b", "c"];
letras.reverse();
console.log(letras); // ['c', 'b', 'a']
```

---

## 8. Styled Components

### 8.1. O que é

Styled Components é uma biblioteca para estilização de componentes em aplicações React e React Native, baseada em JavaScript e CSS-in-JS. Com ela, os estilos são escritos dentro dos próprios componentes, garantindo encapsulamento e facilitando a reutilização. Além disso, Styled Components aproveita o poder das Tagged Template Literals do JavaScript para criar estilos dinâmicos de forma elegante e eficiente.

### 8.2. Como baixar

Para utilizar Styled Components, primeiro é necessário instalá-lo no projeto. Utilize um dos seguintes comandos, dependendo do seu gerenciador de pacotes:

- **Com npm:**
```bash
npm install styled-components
```

- Se estiver utilizando TypeScript, recomenda-se instalar também os tipos do Styled Components:
```bash
npm install --save-dev @types/styled-components
```
### 8.3. Como utilizar

Após a instalação, Styled Components pode ser utilizado para criar componentes estilizados. Veja um exemplo prático:
```js
import styled from 'styled-components';

const Botao = styled.button`
  background-color: #3498db;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  font-size: 16px;
  cursor: pointer;
  transition: background 0.3s;

  &:hover {
    background-color: #2980b9;
  }
`;

function App() {
  return <Botao>Clique aqui</Botao>;
}

export default App;
```

### 8.4. Vantagens do Style Components

- **Escopo local**: os estilos são aplicados apenas ao componente onde foram definidos, evitando conflitos globais.
- **Facilidade de manutenção**: cada componente carrega seus próprios estilos, tornando o código mais organizado.
- **Suporte a temas**: Styled Components permite a criação de temas reutilizáveis, facilitando a personalização da aplicação.
- **Estilização dinâmica**: É possível passar props para modificar os estilos dinamicamente com base em propriedades do componente.

Exemplo de estilização condicional:
```js
const BotaoDinamico = styled.button`
  background-color: ${props => (props.primario ? "#2ecc71" : "#e74c3c")};
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  font-size: 16px;
  cursor: pointer;
`;

function App() {
  return (
    <>
      <BotaoDinamico primario>Confirmar</BotaoDinamico>
      <BotaoDinamico>Cancelar</BotaoDinamico>
    </>
  );
}
```
Neste exemplo, o botão recebe cores diferentes dependendo da prop `primario`.

---

## 9. `useState` 

O `useState` é um hook do React que permite adicionar estados a componentes funcionais. Antes do React Hooks, o estado só podia ser usado em componentes de classe, mas com `useState`, podemos gerenciar estados diretamente dentro de componentes funcionais.

### 9.1. O que é o estado no React

No React, o **estado** é uma variável que armazena informações dinâmicas e pode mudar ao longo do tempo, influenciando a renderização do componente. Sempre que um estado é atualizado, o React re-renderiza o componente para refletir as mudanças.

Por exemplo, um botão de "curtir" pode armazenar no estado o número de cliques.

### 9.2. Quando usar `useState`

Use `useState` para armazenar valores mutáveis dentro de um componente, como:
- Dados de formulários (nome, e-mail)
- Contadores
- Estados de exibição (exemplo: abrir/fechar modal)
- Listas e coleções dinâmicas

Se precisar de compartilhar estados entre componentes, use **Context API** ou `useReducer`.

### 9.3. Como usar o `useState`

O `useState` retorna um array com dois elementos:

1. O valor atual do estado (exemplo: `contador`)
2. Uma função para atualizar o estado (exemplo: `setContador`)

**Exemplo básico**:
```js
import { useState } from "react";

function Contador() {
  const [contador, setContador] = useState(0); // Estado inicial = 0

  return (
    <div>
      <p>O contador está em: {contador}</p>
      <button onClick={() => setContador(contador + 1)}>Incrementar</button>
    </div>
  );
}

export default Contador;
```
- O estado `contador` começa com 0.
- `setContador` é chamada quando o botão é clicado, atualizando o estado e forçando uma nova renderização.

### 9.4. Atualização de estado

⚠️ Nunca atualize o estado diretamente:
Errado ❌:
```js
contador = contador + 1; // Isso não funciona!
```

Certo ✅:
```js
setContador(contador + 1);
```

Se o novo estado depender do estado anterior, use uma função de atualização:
```js
setContador(prevContador => prevContador + 1);
```


### 9.5. Estado com strings, objetos e arrays

O `useState` pode armazenar mais do que números.

- String:
```js
const [nome, setNome] = useState("João");

setNome("Maria"); // Atualiza o estado para "Maria"
```

- Objeto:
```js
const [usuario, setUsuario] = useState({ nome: "Ana", idade: 25 });

setUsuario({ ...usuario, idade: 26 }); // Atualiza apenas a idade
```

- Array:
```js
const [itens, setItens] = useState(["Maçã", "Banana"]);

setItens([...itens, "Laranja"]); // Adiciona um novo item ao array
```

---

