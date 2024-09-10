# Boas vindas ao conteúdo avançado do módulo 2 - Lógica e Algoritmos 

## Revisão JS e ES6

---

1. [Variáveis](#variáveis)

2. [String X Template string](#string-x-template-string)

3. [Function X Arrow function](#function-x-arrow-function)

4. [Função Callback](#função-callback)

5. [Conditional if...else X Ternary operator](#conditional-if...else-x-ternary-operator)

6. [Objetos](#objetos)

7. [Datas](#date)

8. [Classes](#classes)

9. [Arrays](#arrays)

10. [Métodos de iteração](#métodos-de-iteração)

    - [while](#while)
    - [for](#for)
    - [for...of](#for...of)
    - [map](#map)
    - [find](#find)
    - [filter](#filter)
    - [sort](#sort)
    - [reduce](#reduce)


---

### Variáveis

Declarando variáveis:

```js
var nome = 'Pessoa'
```

Formato ES6:

```js
const nome = 'Pessoa'

let idade = 18
idade = 19
```

MDN: [var](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/var), [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const), [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)

---

### String X Template string

Exemplo de string:

```js
const frase = 'Olá, mundo!'

console.log(frase)
```

Exemplo de template string:

```js
const nome = 'Alunos'

const templateString = `Olá, ${nome}`

console.log(templateString)
```

MDN: [Template strings](https://developer.cdn.mozilla.net/pt-BR/docs/Web/JavaScript/Reference/template_strings)

---

### Function X Arrow function

Declarando funções:

```js
function falar() {
  return 'Pipipi popopo'
}

function dobro(num) {
  return num * 2
}

function calcularMedia(nota1, nota2, nota3) {
  const soma = (nota1 + nota2 + nota3)
  const media = soma / 3
  return media
}
```

Ou, podemos declarar as mesmas funções da seguinte forma:

```js
const falar = function() {
  return 'Pipipi popopo'
}

const dobro = function(num) {
  return num * 2
}

const calcularMedia = function(nota1, nota2, nota3) {
  const soma = (nota1 + nota2 + nota3)
  const media = soma / 3
  return media
}
```

Arrow function possui uma sintaxe mais curta, e sabemos que é uma função pelo símbolo `=>`
```js
const falar = () => {
  return 'Pipipi popopo'
}

const dobro = (num) => {
  return num * 2
}

const calcularMedia = (nota1, nota2, nota3) => {
  const soma = (nota1 + nota2 + nota3)
  const media = soma / 3
  return media
}
```

Conseguimos deixar a função ainda mais concisa, pois:
- caso a função só tenha uma linha de instrução, as chaves `{}` são opcionais
- e ao remover as chaves `{}`, o `return` é implícito e, portanto, também removemos:

  ```js
  const falar = () => 'Pipipi popopo'

  const dobro = num => num * 2
  ```

- caso a função só tenha 1 parâmetro, os parênteses em volta do parâmetro `(param)` também são opcionais:

  ```js
  const dobro = num => num * 2
  ```

MDN: [Arrow function](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

---
### Função Callback

> Uma função callback é uma função passada a outra função como parâmetro, que é então invocada dentro da função externa para completar algum tipo de rotina ou ação. *Fonte MDN: [callback](https://developer.mozilla.org/pt-BR/docs/Glossario/Callback_function)*

```js
function somar(a, b) {
  return a + b
}

function subtrair(a, b) {
  return a - b
}

function multiplicar(a, b) {
  return a * b
}

function dividir(a, b) {
  return a / b
}

function ordenar(a, b) {
  if (a <= b) {
    return [a, b]
  } else {
    return [b, a]
  }
}

function calcular(a, b, callback) {
  return callback(a, b)
}

const num1 = 7
const num2 = 2

const somaDoisNumeros = calcular(num1, num2, somar)
console.log(somaDoisNumeros) // 9

const subtracaoDoisNumeros = calcular(num1, num2, subtrair)
console.log(subtracaoDoisNumeros) // 5

const multiplicacaoDoisNumeros = calcular(num1, num2, multiplicar)
console.log(multiplicacaoDoisNumeros) // 14

const divisaoDoisNumeros = calcular(num1, num2, dividir)
console.log(divisaoDoisNumeros) // 3.5

const ordenarDoisNumeros = calcular(num1, num2, ordenar)
console.log(ordenarDoisNumeros) // [2, 7]
```

Deixando a sintaxe reduzida:

```js
const somar = (a, b) => a + b

const subtrair = (a, b) => a - b

const multiplicar = (a, b) => a * b

const dividir = (a, b) => a / b

const ordenar = (a, b) => (a <= b) ? [a, b] : [b, a]

const calcular = (a, b, callback) => callback(a, b)
```

---

### Conditional if...else X Ternary operator

Exemplo de condicional usando `if...else`:

```js
const nota = 3

if (nota >= 7) {
  return 'aprovado'
} else {
  return 'reprovado'
}
```

Exemplo de condicional usando ternário:

```js
const nota = 3

(nota >= 7) ? 'aprovado' : 'reprovado'
```

MDN: [if...else](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/if...else), [ternary](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/Operador_Condicional)

---

### Objetos

Declaração de objetos

```js
const objeto = new Object()
objeto.nome = 'cadeira'
objeto.tipo = 'madeira'
objeto.peso = 7

const pokemon = {
  nome: 'Pikachu',
  tipo: 'elétrico',
  altura: 40.6,
}
```

Acessando o valor de uma propriedade do objeto.

```js
console.log(pokemon.nome) // Pikachu
```

Declarando uma variável de mesmo nome que a propriedade.

```js
const nome = pokemon.nome
const tipo = pokemon.tipo
const altura = pokemon.altura

console.log(nome) // Pikachu
console.log(tipo) // elétrico
console.log(altura) // 40.6
```

Atribuição via desestruturação

```js
const { nome, tipo, altura } = pokemon

console.log(nome) // Pikachu
console.log(tipo) // elétrico
console.log(altura) // 40.6
```

MDN: [destructuring assignment](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/Atribuicao_via_desestruturacao)

---


### Date

```js
const hoje = new Date()

console.log(hoje) // 2020-09-05T10:56:49.693Z

const dia = hoje.getDate()
const mes = hoje.getMonth()
const ano = hoje.getFullYear()

console.log(dia, mes, ano) // 5 8 2020 🤔

const dataFormatada = hoje.toLocaleDateString('pt-BR')
console.log(dataFormatada) // 05/09/2020

const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' }
const dataLonga = hoje.toLocaleDateString('pt-BR', options)
console.log(dataLonga) // sábado, 5 de setembro de 2020
```
MDN: [date](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Date),
[toLocaleDateString](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleDateString)

---

### Classes

```js
class Pessoa {
  constructor(nome, idade, andando = false, caminhada = 0) {
    this.nome = nome
    this.idade = idade
    this.andando = andando
    this.caminhada = caminhada
  }

  andar(metros) {
    this.andando = true
    this.caminhada += metros
  }
}

const professora = new Pessoa('Cintia', 35)
console.log(professora) // Pessoa { nome: 'Cintia', idade: 35, andando = false, caminhada: 0 }

professora.andar(200)
console.log(professora) // Pessoa { nome: 'Cintia', idade: 35, andando = true, caminhada: 200 }

```

MDN: [class](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Classes)

---

### Arrays

Declaração de arrays

```js
const lista = new Array('pera', 'uva', 'maçã')

const numeros = [9, 2, 5]
```

Acessando elementos pela posição do array:

```js
const primeiroItem = lista[0]

console.log(primeiroItem) // pera
```

Tamanho de array:

```js
const tamanho = numeros.length

console.log(tamanho) // 3
```

Atribuição via desestruturação

```js
const [primeiro, segundo, terceiro] = lista

console.log(primeiro) // pera
console.log(segundo) // uva
console.log(terceiro) // maçã
```

---

### Métodos de iteração

#### while

```js
let i = 0

while (i < numeros.length) {
  const dobro = numeros[i] * 2
  console.log(dobro)
  i++
}
// 18
// 4
// 10
```
MDN: [while](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/while)

---

#### for

```js
for (let i = 0; i < numeros.lenght; i++) {
  const dobro = numeros[i] * 2

  console.log(dobro)
}
// 18
// 4
// 10
```
MDN: [for](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/for)

---

#### for...of

```js
for (numero of numeros) {
  const dobro = numero * 2

  console.log(dobro)
}
// 18
// 4
// 10
```
MDN: [for...of](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/for...of)

---
#### map
> O método `map()` invoca a função `callback` passada por argumento para cada elemento do Array e devolve um novo Array como resultado. *Fonte: [MDN map](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/map)*

```js
function dobrar(item) {
  return item * 2
}

const numerosDobrados = numeros.map(dobrar)

console.log(numerosDobrados) // [18, 4, 10]
```

Deixando mais conciso:

```js
const numerosDobrados = numeros.map(function (item) {
  return item * 2
})

console.log(numerosDobrados) // [18, 4, 10]
```

Refatorando para JS moderno:

```js
const numerosDobrados = numeros.map(item => item * 2)

console.log(numerosDobrados) // [18, 4, 10]
```

Obs: o método `map` não alterar o array original. Ele retorna um array novo com o resultado do `map`.

---

#### find

> O método find executa a função callback uma vez para cada elemento presente no array até que encontre um onde callback  retorne o valor true. Se o elemento é encontrado, find retorna imediatamente o valor deste elemento. Caso contrário, find retorna undefined. *Fonte MDN: [find](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/find)*

```js
function procuraCinco(item) {
  return item === 5
}

const achouCinco = numeros.find(procuraCinco)

console.log(achouCinco) // 5
```

---

#### filter

```js
function impar(item) {
  return item % 2 !== 0
}

const numerosImpares = numeros.filter(impar)
```

Deixando mais conciso:

```js
const numerosImpares = numeros.filter(function (item) {
  return item % 2 !== 0
})
```

Refatorando para JS moderno:

```js
const numerosImpares = numeros.filter(item => item % 2 !== 0)

console.log(numerosImpares) // [9, 5]
```

Obs: o método `filter` não alterar o array original. Ele retorna um array novo com o resultado do `filter`.

MDN: [filter]()

---

#### sort
O método `sort` recebe uma função de callback opcional. Caso a função não seja fornecida, o array segue a ordenação dos caracteres Unicode.
> Se o parâmetro funcaoDeComparacao é fornecido, o array será ordenado de acordo com o valor de retorno da funcaoDeComparacao. Considerando que a e b são dois elementos sendo comparados, então:
>  - Se `funcaoDeComparacao(a, b)` for menor que 0, ordena `a` para um índice anterior a `b`, i.e. `a` vem primeiro.
>  - Se `funcaoDeComparacao(a, b)` retornar 0, deixa `a` e `b` inalterados em relação um ao outro, mas ordenado em relação a todos os outros elementos.
>  - Se `funcaoDeComparacao(a, b)` é maior que 0, ordena `b` para um índice anterior que `a`. `funcaoDeComparacao(a, b)` sempre deve retornar o mesmo valor dado um par específico de elementos `a` e `b` como seus dois parâmetros. Se resultados inconsistentes são retornados, então a ordenação é indefinida.
>
> *Fonte MDN: [sort](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)*


```js
function funcaoDeComparacao(a, b) {

  if (a < b) {
    return -1 // ao retornar valor negativo, a ordem fica [a, b]
  } else if (a > b) {
    return 1 // ao retornar valor positivo, a ordem fica [b, a]
  } else {
    return 0 // ao retornar valor nulo, a ordem permanece [a, b]
  }
}

numeros.sort(funcaoDeComparacao)

console.log(numeros) // [2, 5, 9]
```

Deixando mais conciso:

```js
function funcaoDeComparacao(a, b) {
  return a - b
}

numeros.sort(funcaoDeComparacao)

console.log(numeros) // [2, 5, 9]
```

Refatorando para JS moderno:

```js
numeros.sort((a, b) => a - b)

console.log(numeros) // [2, 5, 9]
```

**Obs: o método `sort` altera o array original!**

---

#### reduce

O método `reduce` recebe uma função callback com alguns parâmetros e essa função é executada a cada elemento presente no array. O resultado é a redução do array a um valor só. Normalmente, utilizamos os dois primeiros parâmetros: `acumulador` e `itemAtual`.

Por exemplo, podemos executar a soma de todos os valores do array utilizando o método `reduce`:

```js
function somarTodos(acumulador, itemAtual) {
  return acumulador + itemAtual
}

const numerosSomados = numeros.reduce(somarTodos)

console.log(numerosSomados) // 16
```

Deixando mais conciso:

```js
const numerosSomados = numeros.reduce(function (acumulador, itemAtual) {
  return acumulador + itemAtual
})

console.log(numerosSomados) // 16
```

Refatorando para JS moderno:

```js
const numerosSomados = numeros.reduce((acumulador, itemAtual) => acumulador + itemAtual)

console.log(numerosSomados) // 16
```

MDN: [reduce](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

---
