# Aula — Objetos, Arrays e DOM com JavaScript

## Objetivo da aula

Ao final desta aula, o aluno deverá conseguir:

- Criar objetos em JavaScript;
- Criar arrays de objetos;
- Percorrer listas com `forEach`;
- Exibir dados dinamicamente no HTML usando DOM;
- Criar uma pequena listagem de produtos na tela.

---

## 1. Objetos em JavaScript

Um objeto serve para representar uma coisa do mundo real dentro do código.

Exemplo: um produto.

```js
const produto = {
  nome: "Mouse Gamer",
  preco: 89.90,
  categoria: "Informática"
};
```

Cada informação dentro do objeto é formada por:

```js
chave: valor
```

Exemplo:

```js
nome: "Mouse Gamer"
```

Para acessar uma informação do objeto, usamos o ponto:

```js
console.log(produto.nome);
console.log(produto.preco);
console.log(produto.categoria);
```

Resultado esperado:

```txt
Mouse Gamer
89.9
Informática
```

---

## 2. Arrays em JavaScript

Um array serve para guardar vários valores em uma única variável.

```js
const nomes = ["Ana", "Carlos", "Marina"];
```

Para acessar um item do array, usamos o índice.

```js
console.log(nomes[0]);
console.log(nomes[1]);
console.log(nomes[2]);
```

Atenção: o primeiro item começa no índice `0`.

Porque JavaScript gosta de testar nossa paciência logo cedo.

---

## 3. Array de objetos

Podemos juntar os dois conceitos: criar uma lista com vários objetos.

```js
const produtos = [
  {
    nome: "Teclado Mecânico",
    preco: 199.90,
    categoria: "Informática"
  },
  {
    nome: "Cadeira Gamer",
    preco: 899.90,
    categoria: "Móveis"
  },
  {
    nome: "Monitor 24 polegadas",
    preco: 749.90,
    categoria: "Informática"
  }
];
```

Agora temos uma lista de produtos.

Cada item do array é um objeto.

---

## 4. Percorrendo o array com `forEach`

O `forEach` permite percorrer todos os itens de um array.

```js
produtos.forEach(function(produto) {
  console.log(produto.nome);
});
```

Também podemos usar arrow function:

```js
produtos.forEach((produto) => {
  console.log(produto.nome);
});
```

Exibindo nome e preço:

```js
produtos.forEach((produto) => {
  console.log(`${produto.nome} - R$ ${produto.preco}`);
});
```

---

## 5. DOM: exibindo informações no HTML

O DOM permite que o JavaScript acesse e altere elementos da página HTML.

Exemplo de HTML:

```html
<h1>Lista de Produtos</h1>
<div id="lista-produtos"></div>
```

No JavaScript, podemos selecionar esse elemento:

```js
const listaProdutos = document.querySelector("#lista-produtos");
```

Agora podemos colocar conteúdo dentro dele:

```js
listaProdutos.innerHTML = "Produto cadastrado com sucesso!";
```

---

## 6. Exemplo prático completo

Crie os arquivos abaixo:

```txt
index.html
script.js
```

---

## `index.html`

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Produtos</title>
</head>
<body>
  <h1>Lista de Produtos</h1>

  <div id="lista-produtos"></div>

  <script src="script.js"></script>
</body>
</html>
```

---

## `script.js`

```js
const produtos = [
  {
    nome: "Teclado Mecânico",
    preco: 199.90,
    categoria: "Informática"
  },
  {
    nome: "Cadeira Gamer",
    preco: 899.90,
    categoria: "Móveis"
  },
  {
    nome: "Monitor 24 polegadas",
    preco: 749.90,
    categoria: "Informática"
  }
];

const listaProdutos = document.querySelector("#lista-produtos");

produtos.forEach((produto) => {
  listaProdutos.innerHTML += `
    <div>
      <h2>${produto.nome}</h2>
      <p>Preço: R$ ${produto.preco}</p>
      <p>Categoria: ${produto.categoria}</p>
      <hr>
    </div>
  `;
});
```

---

## 7. Melhorando a exibição com CSS simples

Atualize o `index.html`:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Produtos</title>

  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f2f2f2;
      padding: 20px;
    }

    h1 {
      text-align: center;
    }

    #lista-produtos {
      display: flex;
      gap: 16px;
      flex-wrap: wrap;
      justify-content: center;
    }

    .card {
      background-color: white;
      width: 250px;
      padding: 16px;
      border-radius: 8px;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
    }

    .card h2 {
      margin-top: 0;
    }
  </style>
</head>
<body>
  <h1>Lista de Produtos</h1>

  <div id="lista-produtos"></div>

  <script src="script.js"></script>
</body>
</html>
```

Atualize o `script.js`:

```js
const produtos = [
  {
    nome: "Teclado Mecânico",
    preco: 199.90,
    categoria: "Informática"
  },
  {
    nome: "Cadeira Gamer",
    preco: 899.90,
    categoria: "Móveis"
  },
  {
    nome: "Monitor 24 polegadas",
    preco: 749.90,
    categoria: "Informática"
  }
];

const listaProdutos = document.querySelector("#lista-produtos");

produtos.forEach((produto) => {
  listaProdutos.innerHTML += `
    <div class="card">
      <h2>${produto.nome}</h2>
      <p><strong>Preço:</strong> R$ ${produto.preco}</p>
      <p><strong>Categoria:</strong> ${produto.categoria}</p>
    </div>
  `;
});
```

---

## 8. Atividade prática

Crie uma página que exiba uma lista de alunos.

Cada aluno deve ter:

- nome;
- idade;
- curso;
- nota.

Exemplo de array:

```js
const alunos = [
  {
    nome: "Ana",
    idade: 20,
    curso: "Engenharia de Software",
    nota: 8.5
  },
  {
    nome: "Carlos",
    idade: 22,
    curso: "Sistemas de Informação",
    nota: 7.8
  },
  {
    nome: "Marina",
    idade: 19,
    curso: "Análise e Desenvolvimento de Sistemas",
    nota: 9.2
  }
];
```

A página deve mostrar cada aluno em um card.

---

## 9. Desafio extra

Mostre uma mensagem diferente de acordo com a nota do aluno:

- Se a nota for maior ou igual a `7`, mostrar: `Aprovado`;
- Se a nota for menor que `7`, mostrar: `Revisar conteúdo`.

Exemplo:

```js
const situacao = aluno.nota >= 7 ? "Aprovado" : "Revisar conteúdo";
```

Depois exiba essa situação dentro do card.

---

## 10. Código base para o desafio

```js
const alunos = [
  {
    nome: "Ana",
    idade: 20,
    curso: "Engenharia de Software",
    nota: 8.5
  },
  {
    nome: "Carlos",
    idade: 22,
    curso: "Sistemas de Informação",
    nota: 7.8
  },
  {
    nome: "Marina",
    idade: 19,
    curso: "Análise e Desenvolvimento de Sistemas",
    nota: 9.2
  },
  {
    nome: "João",
    idade: 21,
    curso: "Ciência da Computação",
    nota: 5.9
  }
];

const listaAlunos = document.querySelector("#lista-alunos");

alunos.forEach((aluno) => {
  const situacao = aluno.nota >= 7 ? "Aprovado" : "Revisar conteúdo";

  listaAlunos.innerHTML += `
    <div class="card">
      <h2>${aluno.nome}</h2>
      <p><strong>Idade:</strong> ${aluno.idade}</p>
      <p><strong>Curso:</strong> ${aluno.curso}</p>
      <p><strong>Nota:</strong> ${aluno.nota}</p>
      <p><strong>Situação:</strong> ${situacao}</p>
    </div>
  `;
});
```

---

## 11. Fechamento prático

Nesta aula, usamos:

```js
const objeto = {
  chave: valor
};
```

```js
const array = [];
```

```js
array.forEach(() => {});
```

```js
document.querySelector();
```

```js
elemento.innerHTML += "conteúdo";
```

Esses recursos aparecem o tempo todo em projetos reais com JavaScript.

Quem entende isso, já começa a sair do JavaScript decorado e entra no JavaScript usado de verdade.
