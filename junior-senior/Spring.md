
# 1. O conceito fundamental: O container (ApplicationContext)

Imagine o Spring não com um framework, mas como um ecossitema vivo onde seus objetos habitam.

No java puro, você é o deus do seu código. Você cria objetos (`new Service()`), você destrói objetos, você amarra um no outro. No Spring, você abdica desse poder. Você entrega o controle para o Spring container (representado pela interface `ApplicationContext`).

Como funciona a inversão de controle (IoC) na teoria:

1. Configuração: Você fornece "metadados" (seja via xml antigo, ou classes `@Configuration` e anotações `@Component`).
2. Bean Definition: Ao iniciar, o Spring não cria seus objetos imediatamente. Ele primeiro lê todas as suas classes e cria uma "receita" de cada uma, chamada `BeanDefinition`. Ele monta um mapa mental de tudo que vai precisar ser criado.
3. Instanciação: Só depois de entender o mapa, ele começa a criar as instâncias e injetar as dependências

> **Visão de arquiteto**: Isso desacopla a definição de como um objeto é criado da utilização dele.

---