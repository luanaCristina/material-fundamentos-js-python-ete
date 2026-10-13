# Orientação de uso em aula — Python

## 1. Objetivo do material

Este guia orienta o professor a conduzir aulas de Python para alunos do primeiro módulo, priorizando compreensão, prática e capacidade de investigar.

O aluno não precisa decorar todos os comandos. Ele precisa aprender a:

- ler um problema;
- dividir o problema em passos;
- escolher variáveis e estruturas de dados;
- testar uma hipótese;
- interpretar mensagens de erro;
- consultar a documentação;
- explicar por que escolheu determinada solução;
- melhorar o código depois que ele funciona.

A sequência recomendada é:

```text
terminal → saída → variáveis → decisões → repetições → funções → coleções → módulos → API
```

## 2. Preparação do ambiente

### 2.1 Instalações

Verifique se os alunos possuem:

- Python 3;
- VS Code;
- extensão Python do VS Code;
- Git;
- acesso ao terminal.

No terminal:

```bash
python --version
```

Em alguns sistemas:

```bash
python3 --version
```

Se o comando `python` não funcionar no Linux ou macOS, use `python3` nos exemplos.

### 2.2 Criar a pasta da aula

```bash
mkdir aula-python
cd aula-python
code .
```

Crie o arquivo:

```text
hello.py
```

Execute:

```bash
python hello.py
```

ou:

```bash
python3 hello.py
```

### 2.3 Ambiente virtual

Quando a turma começar a instalar bibliotecas, explique o ambiente virtual:

```bash
python -m venv .venv
```

Ativação no Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

Ativação no Linux/macOS:

```bash
source .venv/bin/activate
```

Depois da ativação, instalar uma biblioteca afeta somente este projeto:

```bash
python -m pip install requests
```

Explique que o ambiente virtual evita misturar as dependências de projetos diferentes.

## 3. Roteiro de uma aula de 3 horas

### Bloco 1 — 9h às 9h20: terminal e primeiro programa

Objetivos:

- abrir o terminal;
- localizar a pasta atual;
- criar um arquivo Python;
- executar o arquivo;
- observar a saída.

Código:

```python
print("Olá, turma!")
print("Estou executando meu primeiro programa em Python.")
```

Pergunte:

- qual comando executou o arquivo?
- o que acontece se removermos as aspas?
- o que acontece se escrevermos `Print` com letra maiúscula?

A ideia é mostrar que Python diferencia maiúsculas e minúsculas.

### Bloco 2 — 9h20 às 9h50: variáveis e tipos

```python
nome = "Ana"
idade = 16
altura = 1.65
matriculado = True

print(nome)
print(type(nome))
print(type(idade))
print(type(altura))
print(type(matriculado))
```

Explique:

- `str`: texto;
- `int`: número inteiro;
- `float`: número decimal;
- `bool`: `True` ou `False`;
- Python não exige declarar o tipo antes da variável;
- o tipo pode ser consultado com `type()`.

Exercício rápido:

```python
produto = "Caderno"
preco = 18.90
quantidade = 2

print(produto)
print(preco * quantidade)
```

Peça aos alunos para alterarem os valores e preverem o resultado antes de executar.

### Bloco 3 — 9h50 às 10h20: entrada e conversão

```python
nome = input("Digite seu nome: ")
idade = int(input("Digite sua idade: "))

print(f"Olá, {nome}!")
print(f"No próximo ano você terá {idade + 1} anos.")
```

Explique que `input()` sempre retorna texto. Por isso usamos `int()` para transformar o texto em número.

Exercício:

- pedir nome;
- pedir duas notas;
- converter as notas para `float`;
- calcular a média;
- exibir o resultado.

```python
nome = input("Nome: ")
nota1 = float(input("Nota 1: "))
nota2 = float(input("Nota 2: "))
media = (nota1 + nota2) / 2

print(f"{nome} ficou com média {media}.")
```

### Bloco 4 — 10h20 às 10h50: condicionais

```python
media = 7

if media >= 7:
    print("Aprovado")
elif media >= 5:
    print("Em recuperação")
else:
    print("Reprovado")
```

O ponto principal em Python é a indentação. O bloco pertence ao `if` porque está recuado.

Mostre operadores:

```python
idade >= 16
idade == 18
nome != ""
nota >= 7 and frequencia >= 75
curso == "Python" or curso == "JavaScript"
not matriculado
```

Exercício: criar um programa que leia a idade e informe se a pessoa pode participar de uma atividade.

### Bloco 5 — 10h50 às 11h20: repetição

`for` com `range`:

```python
for numero in range(1, 6):
    print(numero)
```

`while`:

```python
contador = 1

while contador <= 5:
    print(contador)
    contador += 1
```

Explique que o `while` precisa de uma condição que eventualmente se torne falsa. Caso contrário, teremos um loop infinito.

Exercício:

- imprimir números de 1 a 10;
- imprimir somente pares;
- somar os números de 1 a 100.

### Bloco 6 — 11h20 às 11h50: funções

Declaração:

```python
def calcular_media(nota1, nota2):
    return (nota1 + nota2) / 2

resultado = calcular_media(8, 6)
print(resultado)
```

Explique:

- `def` declara a função;
- os nomes entre parênteses são parâmetros;
- `return` devolve um resultado;
- chamar a função é escrever seu nome com valores;
- uma função evita repetir lógica.

Função sem retorno:

```python
def mostrar_mensagem(nome):
    print(f"Olá, {nome}!")
```

Compare:

```python
mostrar_mensagem("Ana")
media = calcular_media(8, 6)
```

A primeira função imprime. A segunda devolve um valor que pode ser guardado.

### Bloco 7 — 11h50 às 12h: exercício de fechamento

Proponha um pequeno cadastro de alunos em memória:

- pedir nome;
- pedir duas notas;
- calcular média;
- informar a situação;
- permitir cadastrar três alunos usando um laço;
- exibir o resultado.

O objetivo é combinar variáveis, `input`, conversão, função, `if` e `for`.

## 4. Sequência de aulas recomendada

### Aula 1 — ambiente e sintaxe básica

- terminal;
- `print`;
- comentários;
- variáveis;
- tipos;
- `input`;
- conversões.

### Aula 2 — decisões e operadores

- operadores aritméticos;
- operadores de comparação;
- `if`, `elif`, `else`;
- operadores `and`, `or`, `not`;
- validação de entradas.

### Aula 3 — laços

- `for`;
- `range`;
- `while`;
- contador;
- acumulador;
- `break` e `continue` somente depois que o básico estiver claro.

### Aula 4 — funções

- `def`;
- parâmetros;
- retorno;
- função que chama outra função;
- separação em arquivos.

### Aula 5 — listas e dicionários

Lista:

```python
alunos = ["Ana", "Bruno", "Carla"]
alunos.append("Diego")
print(alunos[0])
```

Dicionário:

```python
aluno = {
    "nome": "Ana",
    "idade": 16,
    "curso": "Informática"
}

print(aluno["nome"])
```

Lista de dicionários:

```python
alunos = [
    {"nome": "Ana", "nota": 8},
    {"nome": "Bruno", "nota": 6}
]
```

Esse formato prepara a turma para entender documentos no MongoDB e registros em APIs.

### Aula 6 — arquivos e módulos

`calculadora.py`:

```python
def somar(a, b):
    return a + b
```

`main.py`:

```python
from calculadora import somar

print(somar(2, 3))
```

Explique que dividir o código em arquivos ajuda a organizar responsabilidades.

### Aula 7 — erros e leitura de dados

Introduza `try/except` somente depois de a turma compreender `if`:

```python
try:
    idade = int(input("Idade: "))
    print(idade)
except ValueError:
    print("Digite um número inteiro.")
```

A lógica é:

- `try`: tente executar;
- `except`: faça algo caso aconteça um erro específico;
- `ValueError`: o valor não pôde ser convertido.

### Aula 8 — API com Python

Depois dos fundamentos, apresente Flask ou FastAPI como uma nova biblioteca, sem misturar tudo na primeira aula.

Exemplo mínimo com Flask:

```bash
python -m pip install flask
```

`app.py`:

```python
from flask import Flask, jsonify

app = Flask(__name__)

@app.get("/")
def inicio():
    return jsonify({"mensagem": "API funcionando"})

if __name__ == "__main__":
    app.run(port=5000, debug=True)
```

Execute:

```bash
python app.py
```

Teste:

```http
GET http://localhost:5000/
```

Explique a correspondência com Express:

| Express | Flask |
|---|---|
| `const app = express()` | `app = Flask(__name__)` |
| `app.get('/', handler)` | `@app.get('/')` + função |
| `res.json(dados)` | `jsonify(dados)` |
| `app.listen(3000)` | `app.run(port=5000)` |

## 5. Estratégia de explicação

Use sempre o ciclo:

1. apresentar um problema pequeno;
2. pedir que os alunos prevejam a saída;
3. escrever o menor código possível;
4. executar;
5. provocar um erro controlado;
6. ler a mensagem do erro;
7. pesquisar a documentação;
8. corrigir;
9. pedir que expliquem a solução.

Evite começar com um projeto grande. Um cadastro simples com lista é mais eficiente para ensinar do que entregar uma API completa sem contexto.

## 6. Perguntas para estimular a mentalidade de programador

Para cada exercício, pergunte:

- qual é a entrada?
- qual é a saída?
- qual informação precisa ser guardada?
- qual tipo de dado representa essa informação?
- existe repetição?
- existe uma decisão?
- esse trecho deveria virar uma função?
- como sabemos que o resultado está correto?
- qual teste prova que a solução funciona?

## 7. Exercícios progressivos

### Exercício 1 — apresentação

Peça nome, idade e curso e mostre uma frase formatada.

### Exercício 2 — média

Leia três notas, calcule a média e informe a situação.

### Exercício 3 — tabuada

Leia um número e exiba sua tabuada de 1 a 10.

### Exercício 4 — lista de compras

Permita inserir cinco itens em uma lista e depois exiba todos.

### Exercício 5 — cadastro em memória

Crie uma lista de dicionários com nome, email e telefone.

### Exercício 6 — funções

Separe cadastrar, listar e buscar em funções diferentes.

### Exercício 7 — API

Transforme a lista de alunos em uma rota GET e depois crie uma rota POST.

## 8. Erros comuns

### `python` não foi encontrado

Tente:

```bash
python3 arquivo.py
```

ou instale o Python e reinicie o VS Code.

### `IndentationError`

Verifique os espaços no início das linhas. Python usa indentação para definir blocos.

### `NameError`

O nome da variável pode estar escrito errado ou ainda não foi criado.

### `ValueError`

O programa tentou converter um valor inválido:

```python
int("abc")
```

### `ModuleNotFoundError`

A biblioteca não está instalada no ambiente atual ou o ambiente virtual não está ativado.

### Servidor Flask não responde

Verifique:

- se `python app.py` continua em execução;
- a porta correta;
- se a URL começa com `http://localhost:`;
- se outra aplicação não está usando a porta.

## 9. Avaliação

Avalie o processo, não apenas o programa final:

- o aluno consegue executar o arquivo?
- sabe explicar as variáveis?
- escolhe tipos coerentes?
- usa condicionais e laços corretamente?
- cria funções com nomes claros?
- consegue ler uma mensagem de erro?
- testa entradas diferentes?
- consegue explicar sua solução sem decorar?
- consulta a documentação?
- organiza o projeto?

## 10. Referências para os alunos

- [Tutorial oficial do Python](https://docs.python.org/pt-br/3/tutorial/)
- [Funções no Python](https://docs.python.org/pt-br/3/tutorial/controlflow.html#definindo-funcoes)
- [Estruturas de dados](https://docs.python.org/pt-br/3/tutorial/datastructures.html)
- [Ambientes virtuais](https://docs.python.org/pt-br/3/tutorial/venv.html)
- [Documentação do Flask](https://flask.palletsprojects.com/)
- [Documentação do VS Code para Python](https://code.visualstudio.com/docs/python/python-tutorial)

> Regra pedagógica principal: o aluno não precisa decorar tudo. Ele precisa saber identificar o problema, procurar a sintaxe, testar e explicar o que fez.
