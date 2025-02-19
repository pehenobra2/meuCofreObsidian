
## 1. O que é

Node.js é um ambiente de execução de JavaScript baseado no motor V8 do Google Chrome. Ele permite que o JavaScript seja executado no lado do servidor, tornando-se uma opção popular para aplicações web, APIs e sistemas escaláveis. Diferente de ambientes tradicionais que utilizam threads para gerenciar concorrência, o Node.js usa um modelo assíncrono e orientado a eventos, tornando-o eficiente para operações de E/S (entrada e saída).

---

## 2. Como funciona

Node.js opera em um loop de eventos assíncrono, permitindo que ele manipule múltiplas requisições sem precisar criar uma nova thread para cada uma. Isso o torna extremamente eficiente para aplicações em tempo real, como chats, streaming de dados e APIs REST. O Node.js utiliza o mecanismo de event-driven (orientado a eventos) e a biblioteca libuv para oferecer suporte a operações não bloqueantes.

#### Principais Características:

- **Assíncrono e orientado a eventos:** Execução eficiente sem bloqueios.
- **Single-threaded:** Utiliza um único thread de execução com um loop de eventos.
- **Mecanismo V8:** O motor de JavaScript altamente otimizado do Google.
- **Gerenciamento de pacotes com npm:** Possui um vasto ecossistema de bibliotecas e módulos.

---

## 3. Como iniciar

Para começar com Node.js, siga os passos:

### 3.1. Instalação

1. Baixe e instale o Node.js pelo site oficial: [https://nodejs.org/](https://nodejs.org/)
2. Verifique a instalação:
```bash
node -v

npm -v
```

### 3.2. Criando um projeto

1. Inicialize um novo projeto Node.js:
```bash
mkdir meu-projeto && cd meu-projeto
npm init -y
```

--- 
