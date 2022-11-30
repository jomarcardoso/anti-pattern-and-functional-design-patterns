# Anti Pattern e Design Pattern para o paradigma Funcional

O Anti Pattern surgiu primeiro com o código espaguete.

É um erro comum querer aplicar todos os Padrões de Projeto que aprendeu, sem haver uma necessidade.

Um pattern serve para resolver um problema, se não existe um problema não precisa de um padrão.

https://youtu.be/srQt1NAHYC0?t=198

## Princípios da Programação Funcional

### Funções como coisas

Funções transformam coisas.

### Composição

Encapsular várias funções em uma.

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

## Padrões funcionais

### Monadas

### Functors (não sei se é)

### Monoids

### HOF

## Padrões de projeto em React

#### Render Props

## Referências

- [wiki.c2](http://wiki.c2.com/?AntiPattern)
