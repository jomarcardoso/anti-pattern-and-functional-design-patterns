# Anti Pattern e Design Pattern para o paradigma Funcional + React

O Anti Pattern surgiu primeiro com o código espaguete.

É um erro comum querer aplicar todos os Padrões de Projeto que aprendeu, sem haver uma necessidade.

*"Várias vezes foi alegado que o uso de Design Patterns, são na verdade indicadores de que o linguagem utilizada que está sendo usada não é poderosa o suficiente."*

Um pattern serve para resolver um problema que a linguagem de programação por si não consegue resolver, se não existe um problema não precisa de um padrão.

*"Quando vejo padrões em meus programas, eu considero eles um sinal de problema. O código do programa deveria refletir soment o problema que está sendo resolvido."

Paul Graham

Peter Norvig afirma que 16 dos 23 padrões de projetos que ele conhecia não eram necessários na linguagem Lisp. Um exemplo é o padrão [Pimpl idiom](https://wiki.c2.com/?PimplIdiom) usado na linguagem C++ (provavelmente) que serve para tornar valores privados. Padrões de projetos por vezes são gambiarras para suprir a ausência de uma feature da linguage. Por exemplo, esse padrão Pimpl Idiom não precisaria existir em Java, pois Java já possui atributos e métodos privados.

As linguagens de programação que evoluem, como o JavaScript, podem preencher essas necessidades e evitar as dores de cabeça do uso de padrões. Abaixo alguns padrões que não são mais usado em JavaScript.

```ts
// module
(function() {
  
}());

// class
function Person(name = '') {
  this.name = name;
}
Person.prototype.sayTheName = function() {
  console.log(this.name)
}

var jomar = new Person('Jomar')
jomar.sayTheName()
// 'Jomar'
```

## Princípios da Programação Funcional

https://youtu.be/srQt1NAHYC0?t=198

### Funções como coisas

Funções transformam coisas.

### Composição

Encapsular várias funções em uma. Você não tem como saber o que aconteceu lá dentro.

Serviços são composições.

### Tipos não são classes

O tipo é a entrada e a saída de uma função.

Não há métodos para manipular aquele tipo.

No paradigma Orientado a Objetos o pagamento é uma das possíveis implementações de `IPayment`:

```ts
interface IPayment {}

class CreditCardPayment implements IPayment {}

class CashPayment implements IPayment {}
```

No paradigma funcional faz mais uso de AND (and, &, \*) do OR (or, |, +). Uma interface é um o AND de todos atributos e os atributos podem ser de um valor ou outro, OR.

```ts
interface Payment {
  amount: number;
  currency: 'dolar' | 'real';
  method: 'cash' | 'credit-card'
}
```

### Funções como parâmetros

Evita repetição de código.

## Padrões funcionais

### Partial Application (Encapsulamento)

Para fazer injeção de dependência, pode-se fazer uma composição salvando a "injeção".

```ts
function getCustomerFromConnectionDatabase(connection: Connection, customerId = 0): Customer {
  return connection.query(`SELECT * FROM customer WHERE id = ${customerId}`;
}

function getCustomerFromDatabase(customerId = 0): Customer {
  return getCustomerFromConnectionDatabase(myCoonection, customerid);
}
```

### Continuations

Não sei se é esse o nome, mas a ideia é mandar funções que serão executadas para tratamento de sucesso e erro.

```ts
function divide(numerador = 1, denominador = 1, success, fail) {
  if (denominador === 0) {
    fail();
  }
  
  success(numerador / denominador);
}
```

### Monadas

### Functors (não sei se é)

### Monoids

### HOF

## Padrões de projeto em React

#### Render Props

## Referências

- [wiki.c2](http://wiki.c2.com/?AntiPattern)
- [Norvig](https://norvig.com/design-patterns/ppframe.htm)
- [wiki.c2 - Are Design Patterns Missing Language Features](https://wiki.c2.com/?AreDesignPatternsMissingLanguageFeatures)
- [Paul Graham](http://www.paulgraham.com/icad.html)
- [wiki.c2 - Design Patterns in Dynamic Programming](https://wiki.c2.com/?DesignPatternsInDynamicProgramming)
