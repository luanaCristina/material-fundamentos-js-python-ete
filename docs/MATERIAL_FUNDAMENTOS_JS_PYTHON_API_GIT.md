# Material de prática: JavaScript, Python, APIs, MongoDB e Git/GitHub

## Para que serve este material?

Este material foi feito para alunos do primeiro módulo que querem **aprender a fazer**, não decorar comandos.

A mentalidade que vamos praticar é:

1. entender o problema;
2. dividir o problema em partes menores;
3. procurar a sintaxe na documentação;
4. adaptar um exemplo pequeno;
5. executar;
6. observar o erro;
7. corrigir;
8. testar novamente;
9. salvar uma versão funcionando.

> Programador não é a pessoa que memoriza todos os comandos. É a pessoa que sabe investigar, testar e explicar o que escreveu.

Os exemplos usam JavaScript executado com Node.js e Python executado pelo interpretador Python.

---

## Sumário

1. Preparação do ambiente
2. Como executar JavaScript e Python no VS Code
3. Variáveis, constantes e tipos
4. Escopos, variáveis globais, locais, shadowing e nested scopes
5. Arrays, listas, vetores, matrizes, objetos e dicionários
6. Convenções de nomenclatura
7. Operadores aritméticos, relacionais e lógicos
8. Entrada e saída: `console.log`, `input`, `prompt` e terminal
9. Condicionais
10. Laços de repetição
11. Funções e `def`
12. Funções anônimas, `return`, arrow functions e IIFE
13. Métodos de arrays, objetos, listas e dicionários
14. O que é uma API
15. Cliente, servidor e métodos HTTP
16. MongoDB e banco relacional
17. MongoDB Atlas e operações CRUD
18. Bibliotecas, pacotes e imports
19. Servidor, portas, recursos e ambientes
20. Git e GitHub passo a passo
21. Erros comuns e soluções
22. Projeto final
23. Gabaritos orientadores
24. Referências oficiais

---

# 1. Preparação do ambiente

## 1.1 Ferramentas

Instale:

- [Visual Studio Code](https://code.visualstudio.com/);
- [Node.js](https://nodejs.org/);
- [Python](https://www.python.org/downloads/);
- [Git](https://git-scm.com/downloads);
- uma conta no [GitHub](https://github.com/).

No terminal, confira as instalações:

```bash
node --version
npm --version
python --version
python3 --version
git --version
```

No Windows, `py --version` também pode funcionar para verificar o Python.

### O que significa `--version`?

O programa recebe uma opção de linha de comando e responde com sua versão. Se o terminal disser que o comando não foi encontrado, a ferramenta pode não estar instalada ou não está no `PATH`.

## 1.2 Pasta de estudos

Crie uma pasta para as aulas:

```bash
mkdir estudos-programacao
cd estudos-programacao
code .
```

O comando `cd` muda a pasta atual. O comando `code .` abre a pasta atual no VS Code, quando o comando `code` está disponível.

Uma organização possível:

```text
estudos-programacao/
├── javascript/
│   ├── 01-variaveis.js
│   ├── 02-condicionais.js
│   └── 03-funcoes.js
├── python/
│   ├── 01_variaveis.py
│   ├── 02_condicionais.py
│   └── 03_funcoes.py
└── projetos/
```

---

# 2. Como executar JavaScript e Python no VS Code

## 2.1 Abrir o terminal integrado

No VS Code:

- menu **Terminal > Novo Terminal**;
- ou **Exibir > Terminal**;
- ou atalho `Ctrl + `` (crase);
- para criar outro terminal, `Ctrl + Shift + ``.

O terminal começa normalmente na raiz da pasta aberta no VS Code.

Fonte: [VS Code — Terminal Basics](https://code.visualstudio.com/docs/terminal/basics).

## 2.2 Executar JavaScript com Node.js

Crie `javascript/01-ola.js`:

```js
console.log('Olá, JavaScript!')
```

No terminal:

```bash
node javascript/01-ola.js
```

Saída:

```text
Olá, JavaScript!
```

Também é possível abrir o REPL do Node:

```bash
node
```

Depois:

```js
> 2 + 3
5
> console.log('testando')
testando
```

Para sair:

```text
.exit
```

## 2.3 Executar Python

Crie `python/01_ola.py`:

```python
print("Olá, Python!")
```

No terminal:

```bash
python python/01_ola.py
```

ou:

```bash
python3 python/01_ola.py
```

No Windows, também pode ser:

```bash
py python/01_ola.py
```

Para abrir o modo interativo:

```bash
python
```

Saia com `exit()` ou `Ctrl + D` no Linux/macOS.

## Exercício 1 — primeiros arquivos

Crie um programa em cada linguagem que mostre:

- seu nome;
- seu curso;
- uma frase explicando por que você quer aprender programação.

Depois, execute os dois pelo terminal. Não clique apenas no botão de executar: aprenda a reconhecer o comando que o VS Code está executando.

---

# 3. Variáveis, constantes e tipos

Uma variável é um nome que aponta para um valor. O valor pode ser texto, número, verdadeiro/falso, uma lista ou uma estrutura mais complexa.

## 3.1 JavaScript: `var`, `let` e `const`

```js
var idade = 16
let cidade = 'Recife'
const escola = 'ETE'

idade = 17       // permitido
cidade = 'Olinda' // permitido
// escola = 'Outra' // erro: const não pode ser reatribuído
```

### Quando usar?

- prefira `const` quando a variável não será reatribuída;
- use `let` quando o valor precisará mudar;
- evite `var` em código novo: ele tem regras antigas de escopo e pode gerar confusão.

`const` impede a reatribuição da variável, mas não torna automaticamente um objeto imutável:

```js
const aluno = { nome: 'Ana' }
aluno.nome = 'Beatriz' // permitido: o objeto foi alterado
// aluno = {}          // não permitido: a referência foi reatribuída
```

## 3.2 Python: não existe `const` obrigatório

Python não possui uma palavra-chave que impeça a alteração como `const` do JavaScript. Por convenção, nomes em maiúsculas indicam que o valor deve ser tratado como constante:

```python
IDADE_MINIMA = 16
NOME_ESCOLA = "ETE"

idade = 16
idade = 17
```

A convenção comunica a intenção, mas o interpretador não impede:

```python
NOME_ESCOLA = "Outra escola"  # possível, mas desrespeita a convenção
```

## 3.3 Tipos principais

### Texto

```js
const nome = 'Maria'
const mensagem = "Olá"
const frase = `A aluna é ${nome}`
```

```python
nome = "Maria"
mensagem = 'Olá'
frase = f"A aluna é {nome}"
```

### Números

```js
const quantidade = 10
const preco = 12.5
```

```python
quantidade = 10       # int
preco = 12.5          # float
```

No JavaScript, o tipo numérico comum é `number`. Python separa `int` e `float`.

### Booleanos

```js
const matriculado = true
const cancelado = false
```

```python
matriculado = True
cancelado = False
```

Atenção: JavaScript usa `true`/`false` minúsculos; Python usa `True`/`False` com inicial maiúscula.

### Ausência de valor

```js
let resposta
console.log(resposta) // undefined
const vazio = null
```

```python
resposta = None
```

## 3.4 Descobrir o tipo

```js
console.log(typeof 'texto')  // string
console.log(typeof 10)       // number
console.log(typeof true)     // boolean
console.log(typeof undefined) // undefined
```

```python
print(type("texto"))
print(type(10))
print(type(True))
```

## 3.5 Conversão de tipos

```js
const texto = '42'
const numero = Number(texto)
const comoTexto = String(numero)
const comoBooleano = Boolean(numero)
```

```python
texto = "42"
numero = int(texto)
como_texto = str(numero)
como_booleano = bool(numero)
```

Cuidado com entradas do usuário: normalmente elas chegam como texto.

```js
const idade = Number(prompt('Idade:'))
```

```python
idade = int(input('Idade: '))
```

## Exercício 2 — cadastro simples

Crie um programa que armazene:

- nome;
- idade;
- curso;
- se está matriculado.

Mostre os valores e seus tipos. Depois, transforme a idade recebida como texto em número.

---

# 4. Escopos, variáveis globais, locais, nested scopes e shadowing

**Escopo** é a região do programa onde um nome pode ser acessado.

## 4.1 Escopo global e local em JavaScript

```js
const escola = 'ETE' // escopo global deste arquivo

function apresentar() {
  const mensagem = `Estudo na ${escola}`
  console.log(mensagem)
}

apresentar()
// console.log(mensagem) // erro: mensagem é local da função
```

Uma variável criada dentro da função é local. Uma variável fora pode ser lida pela função, mas devemos evitar muitas variáveis globais porque qualquer parte do programa pode alterá-las.

## 4.2 Blocos e `let`/`const`

```js
if (true) {
  let dentro = 'só existe aqui'
  const outro = 10
  console.log(dentro)
}

// console.log(dentro) // erro
```

`let` e `const` respeitam escopo de bloco. `var` não se comporta da mesma maneira:

```js
if (true) {
  var legado = 'var escapa do bloco'
}

console.log(legado) // funciona, mas essa característica pode causar bugs
```

## 4.3 Escopo global e local em Python

```python
escola = "ETE"

def apresentar():
    mensagem = f"Estudo na {escola}"
    print(mensagem)

apresentar()
# print(mensagem)  # NameError
```

Em Python, a indentação define os blocos.

## 4.4 Nested scopes: escopos aninhados

Um escopo pode estar dentro de outro:

```js
function externa() {
  const mensagem = 'vem da função externa'

  function interna() {
    console.log(mensagem)
  }

  interna()
}

externa()
```

```python
def externa():
    mensagem = "vem da função externa"

    def interna():
        print(mensagem)

    interna()

externa()
```

A função interna consegue ler a variável do escopo externo. Isso se relaciona ao conceito de **closure**.

## 4.5 Shadowing ou sombreamento

Shadowing ocorre quando um escopo interno usa o mesmo nome de um escopo externo:

```js
const nome = 'global'

function teste() {
  const nome = 'local'
  console.log(nome) // local
}

teste()
console.log(nome) // global
```

```python
nome = "global"

def teste():
    nome = "local"
    print(nome)

teste()
print(nome)
```

O nome interno esconde o externo apenas naquele escopo. Para iniciantes, prefira nomes diferentes quando isso deixar o código mais claro.

## 4.6 Alterar uma variável externa em Python

```python
contador = 0

def incrementar():
    global contador
    contador += 1

incrementar()
print(contador)
```

Funciona, mas o uso exagerado de `global` dificulta a manutenção. Uma alternativa melhor costuma ser retornar o novo valor:

```python
def incrementar(contador):
    return contador + 1

contador = incrementar(contador)
```

## Exercício 3 — investigar escopo

Para cada trecho, antes de executar, responda:

1. qual valor será impresso?
2. qual linha causará erro?
3. a variável é global, local ou de bloco?

Crie pelo menos três exemplos com shadowing em JavaScript e três em Python. Explique o resultado em comentários.

---

# 5. Arrays, listas, vetores, matrizes, objetos e dicionários

## 5.1 Array em JavaScript

```js
const notas = [8, 7.5, 9]
console.log(notas[0])
console.log(notas.length)
```

Índices começam em zero. O primeiro item está na posição `0`.

## 5.2 Lista em Python

```python
notas = [8, 7.5, 9]
print(notas[0])
print(len(notas))
```

Em exercícios de matemática, uma lista de números pode ser chamada de vetor. Em programação, normalmente usamos array ou lista.

## 5.3 Matriz

Uma matriz é uma estrutura com linhas e colunas. Em JavaScript:

```js
const matriz = [
  [1, 2, 3],
  [4, 5, 6]
]

console.log(matriz[0][1]) // 2
```

Em Python:

```python
matriz = [
    [1, 2, 3],
    [4, 5, 6]
]

print(matriz[0][1])
```

## 5.4 Objeto em JavaScript

```js
const aluno = {
  nome: 'Ana',
  idade: 16,
  matriculado: true
}

console.log(aluno.nome)
console.log(aluno['idade'])
```

`{}` em JavaScript cria um objeto vazio:

```js
const objetoVazio = {}
```

## 5.5 Dicionário em Python

```python
aluno = {
    "nome": "Ana",
    "idade": 16,
    "matriculado": True
}

print(aluno["nome"])
```

`{}` em Python cria um dicionário vazio:

```python
dicionario_vazio = {}
```

Um conjunto (`set`) em Python usa chaves com itens, ou `set()` para vazio:

```python
cores = {"azul", "verde", "amarelo"}
conjunto_vazio = set()
```

## 5.6 Array de objetos / lista de dicionários

```js
const alunos = [
  { nome: 'Ana', nota: 8 },
  { nome: 'Bruno', nota: 6 }
]
```

```python
alunos = [
    {"nome": "Ana", "nota": 8},
    {"nome": "Bruno", "nota": 6}
]
```

Essa estrutura aparece muito em APIs JSON.

## Exercício 4 — boletim

Crie uma lista com cinco alunos. Cada aluno deve ter nome e três notas. Depois:

- mostre o nome de cada aluno;
- calcule a média;
- informe aprovado se média >= 7;
- informe recuperação se média entre 5 e 6.99;
- informe reprovado se média < 5.

Faça primeiro com dados fixos e depois tente receber um aluno pelo terminal.

---

# 6. Convenções de nomenclatura

Convenção não é decoração. Nomes bons reduzem a necessidade de comentários.

## 6.1 JavaScript

A convenção mais comum é `camelCase`:

```js
const nomeCompleto = 'Ana Lima'
let quantidadeAlunos = 30
function calcularMediaFinal() {}
```

Constantes de configuração podem usar `UPPER_SNAKE_CASE`:

```js
const PORTA_PADRAO = 3000
```

Classes costumam usar `PascalCase`:

```js
class AlunoModel {}
```

## 6.2 Python

A convenção recomendada pelo PEP 8 usa `snake_case`:

```python
nome_completo = "Ana Lima"
quantidade_alunos = 30

def calcular_media_final():
    pass
```

Constantes usam `UPPER_SNAKE_CASE`:

```python
PORTA_PADRAO = 3000
```

Classes usam `PascalCase`:

```python
class AlunoModel:
    pass
```

## 6.3 Regras práticas

Prefira:

```text
nome_aluno
quantidade_itens
calcular_media
```

Evite:

```text
x
abc
coisa
valor2finalfinal
```

Exceção: nomes curtos como `i` em um laço pequeno podem ser aceitáveis:

```js
for (let i = 0; i < 3; i++) {}
```

## Exercício 5 — renomear

Melhore estes nomes:

```text
n, x1, dado, alunoFinalFinal, NomeDoAluno, calcula
```

Crie duas versões: uma seguindo JavaScript e outra seguindo Python.

---

# 7. Operadores aritméticos, relacionais e lógicos

## 7.1 Aritméticos

| Operação | JavaScript/Python |
|---|---|
| soma | `a + b` |
| subtração | `a - b` |
| multiplicação | `a * b` |
| divisão | `a / b` |
| resto | JS/Python: `a % b` |
| potência | JS: `a ** b`; Python: `a ** b` |
| divisão inteira | Python: `a // b`; JS: `Math.floor(a / b)` |

```js
console.log(10 + 3)
console.log(10 % 3)
console.log(2 ** 3)
```

```python
print(10 + 3)
print(10 % 3)
print(2 ** 3)
print(10 // 3)
```

## 7.2 Comparação

```js
console.log(5 === 5)  // igualdade de valor e tipo
console.log(5 !== 4)
console.log(5 > 3)
console.log(5 <= 5)
```

```python
print(5 == 5)
print(5 != 4)
print(5 > 3)
print(5 <= 5)
```

No JavaScript, prefira `===` e `!==` em vez de `==` e `!=` para evitar conversões automáticas inesperadas.

## 7.3 Lógicos

JavaScript:

```js
const idade = 17
const possuiAutorizacao = true

console.log(idade >= 16 && possuiAutorizacao)
console.log(idade < 16 || possuiAutorizacao)
console.log(!possuiAutorizacao)
```

Python:

```python
idade = 17
possui_autorizacao = True

print(idade >= 16 and possui_autorizacao)
print(idade < 16 or possui_autorizacao)
print(not possui_autorizacao)
```

| Ideia | JavaScript | Python |
|---|---|---|
| E | `&&` | `and` |
| OU | `||` | `or` |
| NÃO | `!` | `not` |

## Exercício 6 — regra de entrada

Uma atividade só pode ser liberada se:

- o aluno tiver idade mínima de 16 anos; e
- tiver autorização; ou
- estiver acompanhado de um responsável.

Escreva a expressão lógica em JavaScript e Python e teste todas as combinações.

---

# 8. Entrada e saída

## 8.1 `console.log` e `print`

```js
console.log('Mensagem')
console.log('Nome:', nome)
```

```python
print("Mensagem")
print("Nome:", nome)
```

`console.log` e `print` servem principalmente para observar valores durante a execução. Não são a mesma coisa que retornar um valor de uma função.

## 8.2 `prompt` no navegador

O `prompt` é uma função do navegador:

```js
const nome = prompt('Digite seu nome:')
console.log(`Olá, ${nome}`)
```

Esse código não funciona diretamente no Node.js sem uma biblioteca ou implementação de entrada, porque `prompt` é uma API do ambiente do navegador.

## 8.3 Entrada no Node com `readline`

```js
const readline = require('node:readline')

const terminal = readline.createInterface({
  input: process.stdin,
  output: process.stdout
})

terminal.question('Digite seu nome: ', nome => {
  console.log(`Olá, ${nome}`)
  terminal.close()
})
```

Uma biblioteca como `readline-sync` simplifica a experiência, mas precisa ser instalada e importada.

```bash
npm install readline-sync
```

```js
const readlineSync = require('readline-sync')
const nome = readlineSync.question('Nome: ')
console.log(nome)
```

## 8.4 Entrada no Python

```python
nome = input("Digite seu nome: ")
print(f"Olá, {nome}")
```

Conversão:

```python
idade = int(input("Idade: "))
altura = float(input("Altura: "))
```

## Exercício 7 — calculadora

Crie uma calculadora que peça dois números e uma operação. Faça versões que:

- recebam dados no terminal;
- impeçam divisão por zero;
- mostrem uma mensagem para operação desconhecida.

---

# 9. Condicionais

## 9.1 `if`

```js
if (idade >= 18) {
  console.log('Maior de idade')
}
```

```python
if idade >= 18:
    print("Maior de idade")
```

Python usa `:` e indentação. JavaScript usa chaves, embora existam estilos sem chaves para uma única instrução.

## 9.2 `if/else`

```js
if (nota >= 7) {
  console.log('Aprovado')
} else {
  console.log('Não aprovado')
}
```

```python
if nota >= 7:
    print("Aprovado")
else:
    print("Não aprovado")
```

## 9.3 `if / else if / else`

```js
if (nota >= 7) {
  console.log('Aprovado')
} else if (nota >= 5) {
  console.log('Recuperação')
} else {
  console.log('Reprovado')
}
```

```python
if nota >= 7:
    print("Aprovado")
elif nota >= 5:
    print("Recuperação")
else:
    print("Reprovado")
```

## 9.4 `switch` em JavaScript

```js
const opcao = 'listar'

switch (opcao) {
  case 'listar':
    console.log('Listando')
    break
  case 'cadastrar':
    console.log('Cadastrando')
    break
  default:
    console.log('Opção inválida')
}
```

O `break` evita continuar executando o próximo `case`.

## 9.5 `match` em Python

Python não possui `switch` tradicional. Versões atuais têm `match`:

```python
opcao = "listar"

match opcao:
    case "listar":
        print("Listando")
    case "cadastrar":
        print("Cadastrando")
    case _:
        print("Opção inválida")
```

Para projetos simples, `if/elif/else` continua sendo uma excelente escolha.

## Exercício 8 — menu

Crie um menu no terminal:

```text
1 - Cadastrar aluno
2 - Listar alunos
3 - Sair
```

Implemente primeiro com `if/elif/else`. Depois, em JavaScript, experimente `switch` e, em Python, experimente `match`.

---

# 10. Laços de repetição

## 10.1 `for` numérico

```js
for (let i = 0; i < 5; i++) {
  console.log(i)
}
```

```python
for i in range(5):
    print(i)
```

## 10.2 Percorrer uma coleção

```js
const nomes = ['Ana', 'Bruno', 'Carla']

for (const nome of nomes) {
  console.log(nome)
}
```

```python
nomes = ["Ana", "Bruno", "Carla"]

for nome in nomes:
    print(nome)
```

## 10.3 `while`

```js
let contador = 0
while (contador < 3) {
  console.log(contador)
  contador++
}
```

```python
contador = 0
while contador < 3:
    print(contador)
    contador += 1
```

Sempre verifique se algo dentro do laço modifica a condição. Caso contrário, você pode criar um loop infinito.

## 10.4 `do...while` em JavaScript

O corpo executa pelo menos uma vez:

```js
let senha

do {
  senha = '1234' // exemplo fixo
  console.log('Tentativa realizada')
} while (senha !== '1234')
```

Python não possui `do...while` nativo. Simulamos:

```python
while True:
    senha = input("Senha: ")
    if senha == "1234":
        break
```

## 10.5 `break` e `continue`

```js
for (let i = 0; i < 10; i++) {
  if (i === 3) continue
  if (i === 7) break
  console.log(i)
}
```

```python
for i in range(10):
    if i == 3:
        continue
    if i == 7:
        break
    print(i)
```

## Exercício 9 — menu que continua

Faça o menu do exercício anterior continuar aparecendo até o usuário escolher sair. Use `while` e valide opções inválidas.

---

# 11. Funções e `def`

Uma função agrupa uma tarefa com nome. Isso evita repetição e facilita os testes.

## 11.1 Declaração de função em JavaScript

```js
function saudacao() {
  console.log('Olá!')
}

saudacao()
```

## 11.2 `def` em Python

```python
def saudacao():
    print("Olá!")

saudacao()
```

## 11.3 Parâmetros

Um parâmetro é uma entrada definida na função.

```js
function saudarPessoa(nome) {
  console.log(`Olá, ${nome}`)
}

saudarPessoa('Ana')
```

```python
def saudar_pessoa(nome):
    print(f"Olá, {nome}")

saudar_pessoa("Ana")
```

## 11.4 Um parâmetro e três parâmetros

```js
function calcularDobro(numero) {
  return numero * 2
}

function montarAluno(nome, idade, curso) {
  return { nome, idade, curso }
}
```

```python
def calcular_dobro(numero):
    return numero * 2


def montar_aluno(nome, idade, curso):
    return {"nome": nome, "idade": idade, "curso": curso}
```

## 11.5 `return` versus `console.log` / `print`

Uma função que imprime:

```js
function mostrarDobro(numero) {
  console.log(numero * 2)
}

const resultado = mostrarDobro(5)
console.log(resultado) // undefined
```

Uma função que retorna:

```js
function calcularDobro(numero) {
  return numero * 2
}

const resultado = calcularDobro(5)
console.log(resultado) // 10
```

Em Python:

```python
def mostrar_dobro(numero):
    print(numero * 2)

resultado = mostrar_dobro(5)
print(resultado)  # None


def calcular_dobro(numero):
    return numero * 2

resultado = calcular_dobro(5)
print(resultado)  # 10
```

**Regra mental:** `print`/`console.log` mostra para uma pessoa; `return` entrega um valor para outro trecho do programa continuar usando.

## 11.6 Função chamando outra função

```js
function somar(a, b) {
  return a + b
}

function calcularMedia(a, b) {
  const total = somar(a, b)
  return total / 2
}

console.log(calcularMedia(8, 10))
```

```python
def somar(a, b):
    return a + b


def calcular_media(a, b):
    total = somar(a, b)
    return total / 2

print(calcular_media(8, 10))
```

## 11.7 Chamando função em outro arquivo

JavaScript, arquivo `matematica.js`:

```js
function somar(a, b) {
  return a + b
}

module.exports = { somar }
```

Arquivo `app.js`:

```js
const { somar } = require('./matematica')
console.log(somar(2, 3))
```

Python, arquivo `matematica.py`:

```python
def somar(a, b):
    return a + b
```

Arquivo `app.py`:

```python
from matematica import somar

print(somar(2, 3))
```

A vantagem é dividir o sistema em módulos menores.

## Exercício 10 — funções matemáticas

Crie um módulo com funções para:

- somar;
- subtrair;
- multiplicar;
- dividir;
- calcular média.

Use o módulo em outro arquivo. Para divisão, trate divisão por zero.

---

# 12. Funções anônimas, arrow functions, expressão de função e IIFE

## 12.1 Função anônima

Uma função anônima não tem nome próprio:

```js
const mostrarMensagem = function () {
  console.log('Mensagem')
}

mostrarMensagem()
```

Apesar de a função não ter nome, ela foi guardada na variável `mostrarMensagem`.

## 12.2 Expressão de função

Quando uma função é criada dentro de uma expressão e atribuída a uma variável, temos uma expressão de função:

```js
const somar = function (a, b) {
  return a + b
}
```

Diferença prática em relação à declaração: declarações de função podem ser chamadas antes da linha em que aparecem por causa do hoisting; expressões guardadas em `const` não devem ser chamadas antes da inicialização.

## 12.3 Arrow function

```js
const dobrar = numero => numero * 2
const somar = (a, b) => a + b

const apresentar = nome => {
  console.log(`Olá, ${nome}`)
}
```

Quando há uma única expressão sem chaves, o retorno é implícito:

```js
const quadrado = numero => numero ** 2
```

Com chaves, use `return` se quiser devolver um valor:

```js
const quadrado = numero => {
  return numero ** 2
}
```

## 12.4 Função imediata: IIFE

IIFE significa **Immediately Invoked Function Expression**. A função é criada e executada imediatamente:

```js
(function () {
  const segredo = 'local'
  console.log('Executou agora')
})()
```

Com arrow function:

```js
(() => {
  console.log('Executou agora')
})()
```

A IIFE pode criar um escopo isolado. Hoje, módulos ES e blocos costumam ser alternativas mais claras, mas entender IIFE ajuda a ler código legado.

## 12.5 Python: funções anônimas com `lambda`

```python
dobrar = lambda numero: numero * 2
print(dobrar(5))
```

Para lógica maior, prefira `def`, pois fica mais legível:

```python
def dobrar(numero):
    return numero * 2
```

Python não possui uma IIFE com a mesma sintaxe comum do JavaScript. Podemos definir e chamar uma função, mas geralmente não há motivo didático para fazer isso.

## 12.6 Vantagens e desvantagens

### Declaração de função / `def`

Vantagens:

- legível;
- fácil de reutilizar;
- boa para tarefas nomeadas;
- simples de testar.

Desvantagens:

- pode ficar extensa se usada para operações muito pequenas;
- no JavaScript, entender hoisting é necessário em código antigo.

### Expressão de função / arrow / lambda

Vantagens:

- útil para passar uma função como argumento;
- compacta em transformações de listas;
- muito usada com `map`, `filter` e `reduce`.

Desvantagens:

- sintaxe compacta pode esconder lógica;
- arrow function tem regras específicas para `this`;
- `lambda` em Python deve ser curta.

### IIFE

Vantagem:

- cria isolamento imediatamente.

Desvantagem:

- pode confundir iniciantes;
- módulos modernos são normalmente mais claros.

## Exercício 11 — três formas

Implemente uma função `calcularDesconto(preco, percentual)` usando:

1. declaração de função;
2. expressão de função;
3. arrow function.

Faça cada uma retornar o valor. Depois crie uma versão que apenas imprime e explique a diferença.

---

# 13. Objetos, arrays, listas, dicionários e métodos

Um método é uma função associada a um objeto ou estrutura.

## 13.1 Métodos de array em JavaScript

```js
const numeros = [1, 2, 3, 4, 5]

numeros.push(6)       // adiciona no fim
const ultimo = numeros.pop()
const primeiro = numeros.shift()
numeros.unshift(0)
```

Transformar:

```js
const dobrados = numeros.map(numero => numero * 2)
```

Filtrar:

```js
const pares = numeros.filter(numero => numero % 2 === 0)
```

Encontrar:

```js
const encontrado = numeros.find(numero => numero > 3)
```

Verificar:

```js
const existe = numeros.includes(3)
const todosPositivos = numeros.every(numero => numero > 0)
const algumMaior = numeros.some(numero => numero > 10)
```

Reduzir:

```js
const soma = numeros.reduce((acumulador, numero) => acumulador + numero, 0)
```

Ordenar e unir:

```js
const ordenados = [...numeros].sort((a, b) => a - b)
const texto = numeros.join(', ')
```

## 13.2 Métodos de lista em Python

```python
numeros = [1, 2, 3, 4, 5]

numeros.append(6)
ultimo = numeros.pop()
numeros.insert(0, 0)
```

Transformar e filtrar:

```python
dobrados = [numero * 2 for numero in numeros]
pares = [numero for numero in numeros if numero % 2 == 0]
```

Verificar:

```python
existe = 3 in numeros
soma = sum(numeros)
maior = max(numeros)
menor = min(numeros)
```

Ordenar:

```python
ordenados = sorted(numeros)
numeros.sort()
```

## 13.3 Métodos de strings

```js
const texto = '  JavaScript  '
console.log(texto.trim())
console.log(texto.toUpperCase())
console.log(texto.includes('Script'))
console.log(texto.split(''))
```

```python
texto = "  Python  "
print(texto.strip())
print(texto.upper())
print("Py" in texto)
print(list(texto))
```

## 13.4 Métodos de objeto em JavaScript

```js
const aluno = { nome: 'Ana', idade: 16 }

console.log(Object.keys(aluno))
console.log(Object.values(aluno))
console.log(Object.entries(aluno))
```

Percorrer:

```js
for (const [chave, valor] of Object.entries(aluno)) {
  console.log(chave, valor)
}
```

## 13.5 Métodos de dicionário em Python

```python
aluno = {"nome": "Ana", "idade": 16}

print(aluno.keys())
print(aluno.values())
print(aluno.items())
print(aluno.get("curso", "não informado"))
```

Percorrer:

```python
for chave, valor in aluno.items():
    print(chave, valor)
```

## 13.6 Mutação e cópia

Em JavaScript:

```js
const original = [1, 2]
const copia = [...original]
copia.push(3)
```

Em Python:

```python
original = [1, 2]
copia = original.copy()
copia.append(3)
```

Se apenas atribuir `copia = original`, os dois nomes apontam para a mesma lista.

## Exercício 12 — relatório de notas

Use os métodos de arrays/listas para:

- filtrar alunos aprovados;
- criar uma lista apenas com nomes;
- calcular a média da turma;
- localizar o primeiro aluno com nota acima de 9;
- ordenar notas.

Faça a versão JavaScript com `map`, `filter`, `find`, `reduce` e a versão Python com compreensão de listas, `sum`, `next` e `sorted`.

---

# 14. O que é uma API?

API significa **Application Programming Interface**. É um conjunto de regras para que um programa converse com outro.

Exemplo: uma tela de alunos não precisa saber como o MongoDB armazena os documentos. Ela chama:

```text
GET /api/alunos
```

O servidor consulta o banco e devolve:

```json
[
  { "_id": "...", "nome": "Ana", "matricula": "1001" }
]
```

A API funciona como um contrato:

- endereço da rota;
- método HTTP;
- formato da entrada;
- formato da resposta;
- status de sucesso;
- status de erro.

## 14.1 Cliente e servidor

```text
Cliente (browser/Postman)
        │ requisição
        ▼
Servidor (Express/Python)
        │ consulta
        ▼
Banco de dados (MongoDB)
        │ resposta
        ▲
Servidor
        │ JSON/HTML/status
        ▲
Cliente
```

O cliente pede. O servidor decide como atender. O banco persiste os dados.

## 14.2 Métodos HTTP

| Método | Intenção comum | Exemplo |
|---|---|---|
| `GET` | consultar | `/api/alunos` |
| `POST` | criar | `/api/alunos` |
| `PUT` | substituir/atualizar recurso | `/api/alunos/id` |
| `PATCH` | atualizar parte do recurso | `/api/alunos/id` |
| `DELETE` | excluir | `/api/alunos/id` |

### PUT versus PATCH

`PUT` geralmente envia a representação completa que será atualizada:

```json
{
  "nome": "Ana",
  "matricula": "1001"
}
```

`PATCH` envia apenas a parte alterada:

```json
{
  "nome": "Ana Maria"
}
```

A escolha depende do contrato da API. O importante é documentar e manter consistência.

## 14.3 Exemplo Express

```js
const express = require('express')
const app = express()

app.use(express.json())

app.get('/api/saudacao', (req, res) => {
  res.status(200).json({ mensagem: 'Olá' })
})

app.post('/api/saudacao', (req, res) => {
  res.status(201).json({ recebido: req.body })
})

app.listen(3000, () => {
  console.log('Servidor rodando')
})
```

Fonte: [Express — Roteamento](https://expressjs.com/pt-br/guide/routing.html).

## 14.4 Exemplo Python com Flask

Instalação:

```bash
python -m pip install flask
```

Código:

```python
from flask import Flask, jsonify, request

app = Flask(__name__)

@app.get('/api/saudacao')
def saudacao():
    return jsonify({"mensagem": "Olá"}), 200

@app.post('/api/saudacao')
def receber():
    return jsonify({"recebido": request.json}), 201

if __name__ == '__main__':
    app.run(port=5000, debug=True)
```

---

# 15. Status HTTP e recursos da API

Um recurso é uma entidade acessível por uma URL, como `alunos`, `disciplinas` ou `matriculas`.

Exemplos:

```text
GET    /api/alunos
POST   /api/alunos
GET    /api/alunos/abc123
PUT    /api/alunos/abc123
PATCH  /api/alunos/abc123
DELETE /api/alunos/abc123
```

## Status importantes

- `200 OK`: consulta ou atualização concluída;
- `201 Created`: recurso criado;
- `204 No Content`: operação concluída sem corpo de resposta;
- `400 Bad Request`: entrada inválida;
- `401 Unauthorized`: autenticação necessária ou ausente;
- `403 Forbidden`: identidade conhecida, mas sem permissão;
- `404 Not Found`: recurso ou rota inexistente;
- `409 Conflict`: conflito, como duplicidade;
- `500 Internal Server Error`: falha inesperada no servidor.

Exemplo:

```js
if (!nome) {
  return res.status(400).json({ erro: 'Nome obrigatório' })
}
```

O status não é enfeite. Ele comunica ao cliente o que aconteceu.

## Exercício 13 — contrato da API

Escreva uma tabela para uma API de livros com:

- listar livros;
- criar livro;
- atualizar parcialmente o preço;
- excluir livro;
- livro não encontrado;
- título ausente;
- livro duplicado.

Escolha método, rota e status para cada situação e justifique.

---

# 16. O que é MongoDB e como ele difere de banco relacional?

MongoDB é um banco de dados orientado a documentos. Os documentos têm formato semelhante a JSON e ficam dentro de coleções.

Exemplo MongoDB:

```json
{
  "_id": "...",
  "nome": "Ana",
  "matricula": "1001",
  "disciplinas": ["JavaScript", "Python"]
}
```

Em um banco relacional, os dados costumam ser organizados em tabelas com linhas e colunas:

```text
ALUNOS
id | nome | matricula
```

## Comparação

| MongoDB | Relacional |
|---|---|
| banco | banco |
| coleção | tabela |
| documento | linha/registro |
| campo | coluna |
| `ObjectId` | chave numérica ou UUID comum |
| documentos podem variar | esquema normalmente definido |
| consultas MongoDB | SQL |
| agregação e `$lookup` | `JOIN` |

Não existe “melhor para tudo”. A escolha depende do problema, da equipe, da consistência necessária e do formato dos dados.

MongoDB também oferece transações e garantias ACID; não é correto dizer que banco documental não pode ter consistência.

Fonte: [MongoDB — Introduction](https://www.mongodb.com/docs/manual/introduction/).

---

# 17. MongoDB online com MongoDB Atlas

## 17.1 Criar uma conta

Acesse [MongoDB Atlas](https://www.mongodb.com/atlas) e crie uma conta.

Passos gerais:

1. criar conta;
2. criar um projeto;
3. criar um cluster gratuito, quando disponível;
4. criar um usuário de banco;
5. liberar o acesso de rede apenas para os endereços necessários;
6. copiar a connection string;
7. colocar a string em `.env`, nunca diretamente no código;
8. conectar pelo driver Node.js ou Python.

> Não publique usuário, senha ou connection string no GitHub.

## 17.2 Node.js com MongoDB

Instalar:

```bash
npm install mongodb dotenv
```

`.env`:

```env
DATABASE_URL="mongodb+srv://USUARIO:SENHA@cluster.mongodb.net/?retryWrites=true&w=majority"
```

`banco.js`:

```js
require('dotenv').config()
const { MongoClient } = require('mongodb')

const client = new MongoClient(process.env.DATABASE_URL)

async function executar() {
  await client.connect()
  const banco = client.db('escola')
  const alunos = banco.collection('alunos')

  await alunos.insertOne({ nome: 'Ana', matricula: '1001' })
  const lista = await alunos.find().toArray()
  console.log(lista)

  await client.close()
}

executar().catch(console.error)
```

## 17.3 CRUD no driver Node.js

Criar:

```js
await alunos.insertOne({ nome: 'Bruno' })
await alunos.insertMany([{ nome: 'Carla' }, { nome: 'Davi' }])
```

Ler:

```js
const todos = await alunos.find().toArray()
const um = await alunos.findOne({ nome: 'Bruno' })
```

Atualizar:

```js
await alunos.updateOne(
  { nome: 'Bruno' },
  { $set: { nome: 'Bruno Silva' } }
)
```

Excluir:

```js
await alunos.deleteOne({ nome: 'Davi' })
```

## 17.4 Python com PyMongo

Ambiente virtual:

```bash
python -m venv .venv
```

Ativar no Linux/macOS:

```bash
source .venv/bin/activate
```

Ativar no Windows:

```powershell
.venv\Scripts\activate
```

Instalar:

```bash
python -m pip install pymongo python-dotenv
```

Código:

```python
import os
from dotenv import load_dotenv
from pymongo import MongoClient

load_dotenv()
client = MongoClient(os.environ["DATABASE_URL"])
banco = client["escola"]
alunos = banco["alunos"]

alunos.insert_one({"nome": "Ana", "matricula": "1001"})
for aluno in alunos.find():
    print(aluno)

client.close()
```

CRUD Python:

```python
alunos.insert_one({"nome": "Bruno"})
aluno = alunos.find_one({"nome": "Bruno"})
alunos.update_one({"nome": "Bruno"}, {"$set": {"nome": "Bruno Silva"}})
alunos.delete_one({"nome": "Bruno Silva"})
```

## Exercício 14 — MongoDB

Crie uma coleção `livros` e implemente:

- inserir três livros;
- listar todos;
- buscar por autor;
- atualizar o preço;
- excluir um livro;
- impedir cadastro sem título;
- criar uma API que exponha essas operações.

---

# 18. Bibliotecas, pacotes e imports

Uma biblioteca é código reutilizável escrito por alguém para resolver problemas comuns.

Exemplos JavaScript:

- `readline` e `fs`: módulos nativos do Node;
- `express`: servidor web;
- `mongodb`: driver do MongoDB;
- `ejs`: templates;
- `nodemon`: reinicia o servidor durante o desenvolvimento;
- `dotenv`: carrega variáveis do arquivo `.env`;
- `axios`: cliente HTTP;
- `cors`: configuração de acesso entre origens;
- `joi` ou `zod`: validação;
- `jest`: testes;
- `supertest`: testes de APIs HTTP.

Exemplos Python:

- `os`, `json`, `pathlib`, `datetime`: biblioteca padrão;
- `flask` ou `fastapi`: APIs;
- `pymongo`: MongoDB;
- `python-dotenv`: `.env`;
- `requests`: cliente HTTP;
- `pytest`: testes;
- `pydantic`: validação de dados;
- `black`: formatação;
- `ruff`: análise de código.

## 18.1 Instalar não é importar

Instalar coloca o pacote no ambiente do projeto:

```bash
npm install express
```

ou:

```bash
python -m pip install flask
```

Importar informa ao arquivo que queremos usar aquele código:

```js
const express = require('express')
```

```python
from flask import Flask
```

São etapas diferentes porque:

1. o gerenciador baixa o pacote;
2. o pacote é salvo no projeto ou ambiente;
3. o código precisa declarar de qual módulo usará recursos;
4. o import cria os nomes disponíveis naquele arquivo.

O fato de estar instalado não faz todas as funções aparecerem automaticamente em todos os arquivos.

## 18.2 CommonJS e ES Modules

CommonJS:

```js
const express = require('express')
module.exports = minhaFuncao
```

ES Modules:

```js
import express from 'express'
export default minhaFuncao
```

No Node, a escolha depende do `package.json`, especialmente da propriedade `type`.

## 18.3 `package.json`

Criar:

```bash
npm init -y
```

Instalar uma dependência:

```bash
npm install express
```

Instalar uma dependência de desenvolvimento:

```bash
npm install --save-dev nodemon
```

O `package.json` registra nome, scripts e dependências. O `package-lock.json` registra versões detalhadas para instalações mais reproduzíveis.

Fonte: [npm — npm install](https://docs.npmjs.com/cli/v10/commands/npm-install).

## 18.4 `dotenv`

`.env`:

```env
PORT=3000
DATABASE_URL="mongodb+srv://..."
```

JavaScript:

```js
require('dotenv').config()

const port = Number(process.env.PORT) || 3000
const url = process.env.DATABASE_URL
```

Python:

```python
import os
from dotenv import load_dotenv

load_dotenv()
port = int(os.getenv("PORT", "5000"))
url = os.environ["DATABASE_URL"]
```

Inclua `.env` no `.gitignore`:

```gitignore
.env
.venv/
node_modules/
__pycache__/
```

Envie apenas `.env.example`:

```env
DATABASE_URL="coloque-sua-string-aqui"
PORT=3000
```

## 18.5 `nodemon`

Instalação:

```bash
npm install --save-dev nodemon
```

`package.json`:

```json
{
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
  }
}
```

Rodar:

```bash
npm run dev
```

O Nodemon observa alterações e reinicia o processo durante o desenvolvimento. Ele não substitui o Node e normalmente não deve ser necessário em produção.

## Exercício 15 — biblioteca

Escolha uma biblioteca:

- JavaScript: `axios`, `readline-sync` ou `express`;
- Python: `requests`, `flask` ou `python-dotenv`.

Pesquise na documentação:

1. como instalar;
2. como importar;
3. qual função principal usar;
4. qual erro acontece se importar o nome errado;
5. como fixar a dependência no projeto.

Registre tudo em um `README.md`.

---

# 19. Servidor, portas, localhost e ambientes

## 19.1 O que é servidor?

Um servidor é um processo que fica aguardando requisições e responde a elas. O Express cria um servidor HTTP:

```js
const express = require('express')
const app = express()

app.get('/', (req, res) => {
  res.send('Servidor funcionando')
})

app.listen(3000, () => {
  console.log('http://localhost:3000')
})
```

`express()` cria a aplicação. `app.listen()` abre a escuta de rede.

## 19.2 O que é uma porta?

Uma porta identifica um serviço dentro de um computador. O endereço combina host e porta:

```text
http://localhost:3000
```

- `localhost`: este próprio computador;
- `3000`: porta usada pelo processo.

A porta `3000` não é obrigatória. É uma convenção comum para aplicações web em desenvolvimento. Poderia ser `3001`, `4000`, `5000` ou outra porta disponível.

```js
const port = Number(process.env.PORT) || 3000
app.listen(port)
```

Não use uma porta já ocupada. Portas abaixo de `1024` podem exigir permissões especiais em alguns sistemas. Evite portas reservadas por outros serviços e consulte a política da rede da escola.

## 19.3 `localhost`, `127.0.0.1` e acesso externo

`localhost` normalmente aponta para o próprio computador e não significa “qualquer computador da rede”.

- `127.0.0.1`: loopback IPv4;
- `localhost`: nome local;
- `0.0.0.0`: bind para interfaces disponíveis, útil em alguns ambientes de desenvolvimento, mas exige cuidado.

Se outro computador precisar acessar o servidor, será necessário configurar a interface, firewall e rede. Não abra serviços publicamente sem entender autenticação e segurança.

## 19.4 Ambientes

### Desenvolvimento

Onde escrevemos e testamos:

```env
NODE_ENV=development
PORT=3000
DATABASE_URL="banco-de-desenvolvimento"
```

### Teste

Onde os testes automatizados rodam com dados isolados:

```env
NODE_ENV=test
DATABASE_URL="banco-de-teste"
```

### Produção

Onde usuários reais acessam o sistema:

```env
NODE_ENV=production
PORT=8080
DATABASE_URL="banco-de-producao"
```

Os ambientes existem para impedir que um teste apague dados reais e para permitir configurações diferentes. Nunca copie a senha de produção para um exercício.

## Exercício 16 — servidor e portas

1. Crie um servidor na porta `3000`.
2. Crie outra aplicação na porta `3001`.
3. Tente executar as duas na mesma porta e registre o erro.
4. Mude uma delas para `3002`.
5. Crie uma rota `/saudacao` e outra `/alunos`.
6. Teste pelo navegador e com `curl`.

---

# 20. Git e GitHub passo a passo

## 20.1 Git e GitHub não são a mesma coisa

- **Git** é o sistema de controle de versão instalado no computador;
- **GitHub** é um serviço online que hospeda repositórios Git e oferece colaboração.

Você pode usar Git sem GitHub. Para enviar código ao GitHub, o projeto precisa ter um repositório local e um repositório remoto.

## 20.2 Criar uma conta GitHub

1. Acesse [github.com](https://github.com/).
2. Clique em criar conta.
3. Escolha um nome de usuário profissional.
4. Confirme seu e-mail.
5. Ative autenticação em dois fatores quando possível.
6. Nunca compartilhe senha ou token.

Fonte: [GitHub — criar uma conta](https://docs.github.com/pt/get-started/start-your-journey/creating-an-account-on-github).

## 20.3 Configurar nome e e-mail do Git

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@example.com"
```

Conferir:

```bash
git config --global --list
```

O e-mail deve ser um e-mail associado à conta GitHub, ou você pode usar o e-mail `noreply` fornecido pelo GitHub para preservar privacidade.

Essa configuração identifica o autor dos commits. Ela não faz login automaticamente no GitHub.

## 20.4 Criar repositório local

Dentro da pasta do projeto:

```bash
git init -b main
git status
git add .
git commit -m "feat: criar primeiro programa"
```

O que cada comando faz:

- `git init`: cria a pasta interna `.git`;
- `git status`: mostra arquivos modificados e preparados;
- `git add`: coloca mudanças na área de preparação;
- `git commit`: salva um ponto no histórico.

## 20.5 `.gitignore`

Crie:

```gitignore
node_modules/
.env
.venv/
__pycache__/
*.pyc
.vscode/
```

Não envie:

- senhas;
- URI do MongoDB;
- `node_modules`;
- ambientes virtuais;
- arquivos temporários.

## 20.6 Criar repositório no GitHub

No GitHub:

1. clique em **New repository**;
2. escolha o nome;
3. selecione público ou privado;
4. para enviar um projeto já existente, evite criar outro README inicialmente;
5. crie o repositório.

A URL remota pode ser HTTPS:

```bash
git remote add origin https://github.com/USUARIO/REPOSITORIO.git
```

ou SSH:

```bash
git remote add origin git@github.com:USUARIO/REPOSITORIO.git
```

Confira:

```bash
git remote -v
```

## 20.7 Primeiro push

```bash
git branch -M main
git push -u origin main
```

Depois da primeira vez:

```bash
git add .
git commit -m "docs: atualizar instruções"
git push
```

O `-u` associa a branch local à remota. Depois, `git push` sozinho sabe para onde enviar.

Fonte: [GitHub — Hello World](https://docs.github.com/pt/get-started/start-your-journey/hello-world) e [Pro Git em português](https://git-scm.com/book/pt-br/v2).

## 20.8 Fluxo com branch

```bash
git switch -c feature/cadastro-alunos
# altere os arquivos
git add .
git commit -m "feat: adicionar cadastro de alunos"
git push -u origin feature/cadastro-alunos
```

No GitHub, abra um Pull Request para comparar sua branch com `main`.

## 20.9 Atualizar projeto local

Antes de começar um novo trabalho:

```bash
git switch main
git pull origin main
```

Se você tiver alterações locais, verifique o status antes de fazer pull.

## Exercício 17 — publicar um projeto

1. Crie um programa simples.
2. Crie `.gitignore`.
3. Configure nome e e-mail.
4. Execute `git init`.
5. Faça pelo menos três commits pequenos.
6. Crie um repositório privado no GitHub.
7. Adicione `origin`.
8. Faça push da branch `main`.
9. Crie uma branch `feature/melhorias`.
10. Faça uma alteração, push e Pull Request.

---

# 21. Erros comuns e soluções

## `node: command not found`

Causa: Node.js não instalado ou fora do `PATH`.

Solução:

```bash
node --version
```

Reinstale o Node e reabra o VS Code.

## `python: command not found`

Tente:

```bash
python3 --version
py --version
```

Se não existir, instale Python e marque a opção de adicionar ao `PATH` quando disponível.

## `SyntaxError`

Causa: sintaxe inválida, parêntese/chave ausente ou indentação incorreta.

Estratégia:

1. leia a linha indicada;
2. procure erro na linha anterior também;
3. confira `()`, `{}`, `[]`, aspas e `:`;
4. execute um trecho pequeno.

## `ReferenceError` / `NameError`

Causa: nome não existe naquele escopo ou foi digitado diferente.

Confira:

```js
console.log(nomeDaVariavel)
```

```python
print(nome_da_variavel)
```

## `TypeError`

Causa: operação incompatível com o tipo, como somar texto com objeto ou chamar algo que não é função.

Use `typeof` no JavaScript e `type()` no Python.

## `Cannot find module`

Causas comuns:

- pacote não instalado;
- `require`/`import` errado;
- caminho relativo errado;
- comando executado fora da pasta do projeto.

Soluções:

```bash
npm install
npm install nome-do-pacote
```

Verifique se o arquivo existe e se o nome respeita maiúsculas/minúsculas.

## `ModuleNotFoundError`

No Python:

```bash
python -m pip install nome-do-pacote
```

Confira se o ambiente virtual está ativado:

```bash
which python
```

No Windows:

```powershell
where python
```

## `EADDRINUSE`

A porta já está ocupada.

Soluções:

- parar o outro servidor;
- escolher outra porta;
- descobrir o processo que usa a porta.

Exemplo de mudança:

```bash
PORT=3001 npm start
```

## `ECONNREFUSED`

O cliente tentou acessar uma porta onde não existe servidor escutando. Confira se o servidor iniciou e se a URL está correta.

## `DATABASE_URL` não definida

Crie `.env` a partir de `.env.example`, instale `dotenv` e carregue a configuração antes de ler `process.env` ou `os.environ`.

## MongoDB `Authentication failed`

Confira:

- usuário;
- senha;
- caracteres especiais codificados na URI;
- nome do cluster;
- usuário criado no Atlas;
- permissão de rede.

## `git push` rejeitado

Possíveis causas:

- remoto não configurado;
- autenticação ausente;
- branch diferente;
- repositório remoto já possui commits que você não tem;
- você não tem permissão.

Comandos de investigação:

```bash
git remote -v
git branch
git status
git log --oneline -5
git pull --rebase origin main
```

## `Author identity unknown`

Configure:

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@example.com"
```

## Segredo enviado ao GitHub

1. revogue ou troque a senha/token imediatamente;
2. remova o segredo do arquivo atual;
3. adicione `.env` ao `.gitignore`;
4. entenda que apagar o arquivo no último commit não remove o segredo do histórico;
5. para casos reais, siga o procedimento de remoção de segredo do GitHub.

---

# 22. Projeto final integrador

Crie uma API de biblioteca escolar em JavaScript ou Python.

## Requisitos

### Dados

Um livro deve ter:

```json
{
  "titulo": "Aprendendo Programação",
  "autor": "Nome do autor",
  "ano": 2026,
  "disponivel": true
}
```

### Rotas

- `GET /api/livros` — listar;
- `GET /api/livros/:id` — buscar;
- `POST /api/livros` — criar;
- `PUT /api/livros/:id` — substituir;
- `PATCH /api/livros/:id` — atualizar parte;
- `DELETE /api/livros/:id` — excluir.

### Regras

- título obrigatório;
- ano deve ser número;
- livro inexistente deve retornar `404`;
- ID malformado deve retornar `400`;
- criação deve retornar `201`;
- exclusão deve retornar `204`;
- erro inesperado deve retornar `500`;
- conexão deve vir de `.env`;
- `.env` não pode ser enviado ao GitHub;
- projeto deve ter README;
- projeto deve ter pelo menos cinco commits explicativos;
- projeto deve ter testes Postman ou Jest.

### Entregáveis

1. código;
2. `.env.example`;
3. `.gitignore`;
4. README com instalação;
5. documentação das rotas;
6. coleção Postman ou testes Jest;
7. repositório GitHub;
8. apresentação de cinco minutos explicando uma decisão técnica.

## Critérios de avaliação

- funcionamento: 30%;
- clareza dos nomes e organização: 20%;
- tratamento de erros e status: 20%;
- documentação e referências: 15%;
- histórico Git: 10%;
- capacidade de explicar e investigar: 5%.

---

# 23. Gabaritos orientadores

Os gabaritos não são para copiar. Use-os depois de tentar.

## Função de média em JavaScript

```js
function calcularMedia(notas) {
  if (notas.length === 0) return 0
  const total = notas.reduce((soma, nota) => soma + nota, 0)
  return total / notas.length
}
```

## Função de média em Python

```python
def calcular_media(notas):
    if len(notas) == 0:
        return 0
    return sum(notas) / len(notas)
```

## Classificação

JavaScript:

```js
function classificar(nota) {
  if (nota >= 7) return 'Aprovado'
  if (nota >= 5) return 'Recuperação'
  return 'Reprovado'
}
```

Python:

```python
def classificar(nota):
    if nota >= 7:
        return "Aprovado"
    if nota >= 5:
        return "Recuperação"
    return "Reprovado"
```

## API mínima Express

```js
const express = require('express')
const app = express()
app.use(express.json())

const livros = []

app.get('/api/livros', (req, res) => {
  res.status(200).json(livros)
})

app.post('/api/livros', (req, res) => {
  if (!req.body.titulo) {
    return res.status(400).json({ erro: 'Título obrigatório' })
  }

  const livro = { id: livros.length + 1, ...req.body }
  livros.push(livro)
  return res.status(201).json(livro)
})

app.listen(3000, () => console.log('API em http://localhost:3000'))
```

Atenção: este exemplo usa memória, não MongoDB. Ele serve para entender o fluxo antes de conectar ao banco.

---

# 24. Referências oficiais e para continuar estudando

## JavaScript e navegador

- [MDN — Guia JavaScript](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide)
- [MDN — Referência JavaScript](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference)
- [MDN — Declarações e variáveis](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Grammar_and_types)
- [MDN — Escopo](https://developer.mozilla.org/pt-BR/docs/Glossary/Scope)
- [MDN — Funções](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Functions)
- [MDN — Arrays](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array)
- [MDN — Objetos](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Working_with_objects)
- [MDN — Fetch API](https://developer.mozilla.org/pt-BR/docs/Web/API/Fetch_API)

## Node.js e npm

- [Node.js — documentação](https://nodejs.org/docs/latest/api/)
- [Node.js — readline](https://nodejs.org/api/readline.html)
- [npm — npm install](https://docs.npmjs.com/cli/v10/commands/npm-install)
- [Express — documentação](https://expressjs.com/pt-br/)
- [Express — roteamento](https://expressjs.com/pt-br/guide/routing.html)
- [EJS](https://ejs.co/)
- [Nodemon](https://www.npmjs.com/package/nodemon)

## Python

- [Tutorial oficial Python em português](https://docs.python.org/pt-br/3/tutorial/)
- [Referência da linguagem Python](https://docs.python.org/pt-br/3/reference/)
- [Biblioteca padrão Python](https://docs.python.org/pt-br/3/library/index.html)
- [Ambientes virtuais e pacotes](https://docs.python.org/pt-br/3/tutorial/venv.html)
- [PEP 8 — estilo de código](https://peps.python.org/pep-0008/)
- [PyMongo](https://www.mongodb.com/docs/languages/python/pymongo-driver/current/)
- [Flask](https://flask.palletsprojects.com/)
- [FastAPI](https://fastapi.tiangolo.com/)

## APIs e HTTP

- [MDN — HTTP](https://developer.mozilla.org/pt-BR/docs/Web/HTTP)
- [MDN — métodos HTTP](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Reference/Methods)
- [MDN — status HTTP](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Reference/Status)
- [Postman Learning Center](https://learning.postman.com/docs/)

## MongoDB

- [MongoDB — Introduction](https://www.mongodb.com/docs/manual/introduction/)
- [MongoDB — Node.js Driver](https://www.mongodb.com/docs/drivers/node/current/)
- [MongoDB — PyMongo](https://www.mongodb.com/docs/languages/python/pymongo-driver/current/)
- [MongoDB Atlas](https://www.mongodb.com/atlas)

## Git e GitHub

- [Pro Git em português](https://git-scm.com/book/pt-br/v2)
- [Git — documentação](https://git-scm.com/docs)
- [GitHub — Hello World](https://docs.github.com/pt/get-started/start-your-journey/hello-world)
- [GitHub Skills](https://skills.github.com/)
- [GitHub Docs](https://docs.github.com/pt)

---

## Checklist final do aluno

Antes de dizer “terminei”, confirme:

- [ ] consigo executar um arquivo JavaScript com `node`;
- [ ] consigo executar um arquivo Python com `python`;
- [ ] sei diferenciar variável, constante e escopo;
- [ ] sei escolher entre `if`, `switch`/`match` e laços;
- [ ] sei criar função com parâmetro e retorno;
- [ ] sei chamar uma função de outro arquivo;
- [ ] sei trabalhar com arrays/listas e objetos/dicionários;
- [ ] sei explicar cliente, servidor e API;
- [ ] sei escolher `GET`, `POST`, `PUT`, `PATCH` e `DELETE`;
- [ ] sei conectar ao MongoDB com uma variável de ambiente;
- [ ] sei instalar e importar uma biblioteca;
- [ ] sei explicar o que é porta e `localhost`;
- [ ] sei executar uma API local;
- [ ] sei criar commit e fazer push;
- [ ] sei investigar um erro lendo a mensagem e a documentação.

> A próxima etapa não é decorar mais comandos. É escolher um exercício, tentar sem copiar, consultar uma referência e explicar por que sua solução funciona.
