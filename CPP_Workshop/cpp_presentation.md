class: center, middle

# Workshop C++
### NIAEFEUP

---

# Pré-requisitos

Este workshop dá como adquiridos alguns conceitos mais elementares de programação. Foi concebido para programadores que têm como base conhecimento de Python 3.

Os detalhes que são comuns às duas linguagens (C++/Python3) não serão explorados com tanto detalhe como os específicos de C++.

---

# Links importantes

- Apresentação: https://cpp-ws-2020.netlify.app/
- [Exercícios](https://github.com/antbz/WS_Cpp)
- [OnlineGDB](https://www.onlinegdb.com/online_c++_compiler)

---

# Overview

1. [Uma breve história de C++](#5)
2. [Hello world!](#6)
3. [Output](#10)
4. [Variáveis e tipos de dados](#16)
5. [Input](#14)
6. [Operadores](#21)
7. [Condições](#26)
8. [Ciclos](#29)
9. [Funções](#37)
10. [Strings](#42)
11. [STL/Vetores](#47)
12. [Classes](#52)

---

# Uma breve história de C++
- Linguagem criada por Bjarne Stroustrup em 1979.
- É uma extensão de C.
- Compatível com programação orientada a objetos.
- Amplamente suportada e muito poderosa.

![Bjarne Stroustrup](img/bjarne.jpg)

---

# Hello world!

Para começar, abre o [OnlineGDB](https://www.onlinegdb.com/online_c++_compiler), copia e cola o seguinte código e executa-o.

```C++
#include <iostream>

using namespace std;

int main() {
    cout << "Hello world!" << endl;
    return 0;
}
```

---
# Hello world!

## Breakdown

- `#include <iostream>` - Inclui/"importa" o ficheiro `iostream` que contém os objetos de **input/output**.
- `using namespace std;` - Necessário para utilizar diretamente as funções da **biblioteca padrão**. O conceito de namespace sai fora do alcance deste workshop.
- `int main()` - Define a **função de entrada** do programa. Esta função **retorna sempre um inteiro** (`int`).
- `cout` - Stream de **output** para a consola.
- `<<` - Operador de **inserção**: insere os dados que o seguem no stream que o antecede.
- `endl` - Insere um caráter de **fim de linha** `\n`.

---

# Hello world!

## Diferenças chave: C++ vs Python.

### A identação não importa (tanto)

Serve apenas para organizar melhor o código, mas não afeta o significado/execução do programa.

### Ponto; e; vírgula;

Cada comando/linha de código tem de ser terminado por `;`.

### Liguagem compilada vs. interpretada

É mais rápida, mas menos flexível.

---

# Calculadora

Vamos desenvolver uma aplicação de cálculo aritmético simples.

O desenvolvimento será feito por etapas, introduzindo aos poucos novos conceitos da linguagem.

Cada etapa tem um enunciado com algumas sugestões que servem como guia.

A seguir ao enunciado de cada etapa, é apresentada uma proposta de resolução, que será analisada.

Entre as várias etapas, serão explicados com maior detalhe os conceitos abordados.

---

# Ex1 - Boas vindas

Começemos por dar as boas vindas ao nosso utilizador.
- Pegando no exemplo do Hello World, altera a mensagem que é mostrada ao utilizador para uma que lhe dê as boas-vindas à calculadora. Por exemplo:

    ```bash
    Welcome to MyCalculator!
    App developed by António Bezerra.
    ```

---

# Ex1 - Boas vindas

### Solução

```C++
int main() {
    cout << "Welcome to MyCalculator!" << endl;
    cout << "App developed by António Bezerra." << endl;

    return 0;
}
```

---

# Output

- Para mostrar informação na consola é utilizado o stream `cout`.
- Para mudar de linha no final de uma inserção, utiliza-se a função `endl`. 
- Este objeto imprime aquilo que lhe fornecemos com o operador de inserção `<<`. 

    ```C++
    cout << "Linha 1 ";
    cout << "Linha 1" << endl;
    cout << "Linha 2 "<< endl;
    cout << "Linha 3";
    ```

    ```bash
    Linha 1 Linha 1
    Linha 2
    Linha 3
    ```

---

# Output

- É possível encadear várias inserções numa mesma instrução.
```C++
cout << "Este texto foi inserido em: " << endl;
cout << "2 linhas" << endl;
cout << "Este texto foi inserido em: " << endl << "1 linha";
```

    ```bash
    Este texto foi inserido em: 
    2 linhas
    Este texto foi inserido em: 
    1 linha
    ```

---

# Ex2 - Input

Vamos ler um número inteiro inserido pelo utilizador na consola e guardá-lo numa variável. A nossa aplicação deve:
- Pedir input ao utilizador:
```bash
Input an integer number: 
```
- Instanciar a varáivel onde vamos guardar o valor introduzir:
```C++
int input;
```
- Ler input utilizando o stream `cin`:
```C++
cin >> input;
```
- Mostrar a input recebida:
```C++
cout << "Your input: " << input << endl;
```

---

# Ex2 - Input

### Solução 

```C++
int main() {
    cout << "Welcome to MyCalculator!" << endl;
    cout << "App developed by António Bezerra." << endl;

    cout << "Please input an integer number: ";
    
    int input;
    cin >> input;

    cout << "Your input: " << input << endl;

    return 0;
}
```

---

# Variáveis e tipos de dados

- C++ é uma **linguagem estática** - o tipo das variáveis e valores de retorno das funções tem que ser declarado explicitamente.
- Não é necessário atribuir um valor a uma variável antes de a utilizar.
- Há dois **tipos de variáveis**:
    - **Globais**: Declaradas fora do corpo de uma função, podem ser utilizadas em qualquer função.
    - **Locais**: Declaradas dentro do corpo de uma função, apenas podem ser utilizadas na própria função.
- A declaração de uma variável tem a seguinte estrutura:

    ```C++
    int num;
    // ...
    num = 1;
    ```
    
    ```C++
    char letter = 'A'; 
    // Neste caso, para além de declarar a variável,
    // estamos também a inicializá-la com um valor
    ```

---

# Tipos de dados

As variáveis de C++ podem ser dos seguintes tipos:

- **char** - caracteres alfanuméricos ('c', '8', '$', ...)
- **int** - números inteiros (103, -2, ...)
- **float** - números em vírgula flutuante de precisão simples (1.902, -5,926563840, ...)
- **double** - números em vírgula flutuante de precisão dupla (1.902, -5,926563840, ...)  
- **bool** - valor booleano (true, false)

Existem bibliotecas que acrescentam outros tipos de dados, como ***strings*** ou ***vectors***, que veremos mais à frente.

---

# Input

- Para obter informação da consola é utilizado o stream `cin`.
- Este objeto extraí a informação obtida para a variável que é fornecida ao operador de extração `>>`.
- O programa **para a execução** enquanto espera pela input do utilizador.
- Por defeito, a extração acontece quando o stream contém um **caráter de espaço branco **(newline, espaço, tab, etc).
- Se o stream estiver **vazio**, a extração não acontece e o programa continua à espera.
- Se o stream contiver **dados incompatíveis** com o tipo de variável, os dados não são extraídos mas a execução continua.

---

# Input

- É possível encadear duas extrações:
```C++
int main() {
    int num;
    char letter;

    cin >> num >> letter;

    cout << "INPUT: " << endl;
    cout << "num: " << num << endl;
    cout << "letter: " << letter << endl;

    return 0;
}
```

    ```bash
    11 # input
    a # input
    INPUT:
    num: 11
    letter: a
    ```

---

# Input

Para além do stream `cin` é também comum utilizar a função `getline()`.
- `getline()` obtém uma linha como uma string.
- Ao contrário de `cin`, o delimitador de extração é apenas o caráter de newline, e não qualquer espaço branco.
- Assim, é possível extrair informação que contenha espaços, por exemplo.
- É importante ***não misturar*** a utilização dos dois métodos.
    - Ao obter informação diretamente de `cin`, o caráter de delimitação não é retirado do stream.
    - Assim, se o delimitador fosse um '\n', ao utilizar `getline()` obteríamos uma string vazia.

Veremos casos de utilzação desta função mais à frente.

---

# Ex3 - Soma

Vamos acrescentar a funcionalidade de somar dois números à nossa aplicação. Tendo por base o código do último exercício:
- Declara mais uma variável e pede input ao utilizador novamente para obter o seu valor.
- Ao invés de no final mostrar na consola as inputs, soma o valor das duas variáveis e mostra o resultado.

---

# Ex3 - Soma

### Solução

```C++
int main() {
    cout << "Welcome to MyCalculator!" << endl;
    cout << "App developed by António Bezerra." << endl;

    cout << "Please input an integer number: ";
    int num1;
    cin >> num1;
    
    cout << "Please input an integer number: ";
    int num2;
    cin >> num2;

    int sum = num1 + num2;

    cout << "Sum: " << sum << endl;

    return 0;
}
```

---

# Operadores

## Operadores Aritméticos
- `+` - adição
- `-` - subtração
- `*` - multiplicação
- `/` - divisão*
- `%` - módulo (resto da divisão inteira)

\* **Nota:** O tipo retornado pela divisão depende do tipo dos operandos. Se ambos forem do tipo inteiro, a divisão terá um resultado inteiro também:
```C++
int a = 3;
int b = a / 2; // = 1
double c = a / 2.0 // = 1.5
```

---

# Operadores

## Operadores de igualdade
- `==` - igual a
- `!=` - diferente de
- `>` - maior do que
- `<` - menor do que
- `>=` - maior ou igual
- `<=` - menor ou igual

## Operadores lógicos
- `&&` - E lógico
- `||` - OU lógico 
- `!` - NÃO lógico (negação)

---

# Operadores

## Operadores de atribuição
- `a = b` - a fica com o valor de b
- `a += b` - `a = a + b`
- `a -= b` - `a = a - b`
- `a *= b` - `a = a * b`
- `a /= b` - `a = a / b`
- `a++` - `a = a + 1`
- `a--` - `a = a - 1`

---

# Ex4 - Outras operações

Usando os operandos já vistos e introduzindo cláusulas *if*, vamos adicionar à nossa calculadora a capacidade de realizar qualquer uma das quatro operações aritméticas fundamentais.

- Acrescentar uma variável `char op` para armazenar um caráter lido da consola, que deverá ser um de: +, -, *, /.
- Utilizando o operador de igualdade `==` e uma cláusula *if*, realizar a operação correta.
- Em C++, uma cláusula *if* tem a seguinte estrutura:
```C++
if (cond) {
    // CÓDIGO A EXECUTAR SE cond FOR VERDADE
} else if (cond2) {
    // CÓDIGO A EXECUTAR SE cond FOR FALSO E cond2 VERDADE
} else {
    // CÓDIGO A EXECUTAR SE TANTO cond COMO cond2 FOREM FALSO
}
```
- **Sugestão:** para tornar a nossa calculadora mais versátil, muda o tipo de dados dos números da calculadora para `double`.

---

# Ex4 - Outras operações

### Solução

```C++
int main() {
    cout << "Welcome to MyCalculator!" << endl;
    cout << "App developed by António Bezerra." << endl;

    cout << "Please input an operator (+, -, *, /): ";
    char op;
    cin >> op;

    cout << "Please input a number: ";
    double num1;
    cin >> num1;
    
    cout << "Please input a number: ";
    double num2;
    cin >> num2;

    // ...
```

---

# Ex4 - Outras operações

### Solução

```C++
    // ...
    double result;

    if (op == '+') {
        result = num1 + num2;
    } else if (op == '-') {
        result = num1 - num2;
    } else if (op == '*') {
        result = num1 * num2;
    } else if (op == '/') {
        if (num2 == 0) {
            cout << "Invalid operation!" << endl;
            return -1; // Atenção à divisão por zero!
        }
        result = num1 / num2;
    }

    cout << "Result: " << result << endl;

    return 0;
}
```

---

# Ex5 - Repetir operações

Vamos adaptar a aplicação para não terminar no final de realizar uma operação.
- Envolve o código atual num ciclo `while (true)` - ciclo infinito.
- Usa `break;` para terminar o ciclo quando o utilizador inserir um caráter 'x' como operador.
```C++
while (true) {
    // ...
    break; // Termina o ciclo
}
```

---

# Ex5 - Repetir operações

### Solução

```C++
int main() {
    cout << "Welcome to MyCalculator!" << endl;
    cout << "App developed by António Bezerra." << endl;
    
    while (true) {
        cout << "Please input an operator (+, -, *, /) - x to quit: ";
        char op;
        cin >> op;

        if (op == 'x') {
            break;
        }

        cout << "Please input an integer number: ";
        double num1;
        cin >> num1;
        
        cout << "Please input an integer number: ";
        double num2;
        cin >> num2;

    // ...
```

---

# Ex5 - Repetir operações

### Solução

```C++
    // ...
        double result;

        if (op == '+') {
            result = num1 + num2;
        } else if (op == '-') {
            result = num1 - num2;
        } else if (op == '*') {
            result = num1 * num2;
        } else if (op == '/') {
            if (num2 == 0) {
                cout << "Invalid operation!" << endl;
                return -1;
            }
            result = num1 / num2;
        }

        cout << "Result: " << result << endl;
    }

    return 0;
}
```

---

# Ciclos

## While loop 
```C++
while (cond) {
    // Corre enquanto cond for verdade
}
```

## Do-while loop
```C++
do {
    // Corre sempre pelo menos uma vez
    // Corre mais vezes enquanto cond for verdade
}
while (cond); 
```

## For loop
```C++
for (int i = 0; i < 10; i++) {
    // Corre enquanto i for menor do que 10, incrementando por 1 a cada iteração
}
```

---

# Variáveis e ciclos

- Em C++, chavetas `{ }` representam um *scope* ou âmbito.
- *Scopes* delimitam os locais onde determinadas variáveis podem ser referenciadas.
- Tal como variáveis locais só são acedíveis dentro da função onde são declaradas, variáveis declaradas dentro de um ciclo ou cláusula *if* delimitados por `{ }` só podem ser utilizadas no ciclo/cláusula.
- A cada iteração, as variáveis declaradas no corpo do ciclo são re-inicializadas.
- A variável declarada no cabeçalho de um ciclo `for` pertence ao *scope* do ciclo, mas é inicializada apenas uma vez, antes do ciclo iniciar.

### Exemplo
```C++
int a = 1;
if (cond) {
    int i = 1;
    cout << a + i; // Imprime: 2
}
cout << i; // Inválido!
```

---

# Ex6 - Calculadora com memória

Vamos acrescentar a funcionalidade de utilizar o valor do último resultado da calculadora como operando. Assim, podemos encadear as operações!
- Cria uma variável que armazene o último resultado.
- Quando o utilizador inserir como operador o caráter 'm', utiliza o resultado anterior como o primeiro operando e pede novamente o operador.
- Tem em atenção o local de declaração da variável e o local de atualização do respetivo valor.

---

# Ex6 - Calculadora com memória

### Solução 

```C++
int ex6() {
    cout << "Welcome to MyCalculator!" << endl;
    cout << "App developed by António Bezerra." << endl;
    
    double last_result = 0;

    while (true) {
        cout << "Input an operator (+, -, *, /) - m to use last result - x to quit: ";
        char op;
        cin >> op;

        int num1;

        if (op == 'x') {
            break;
        } else if (op == 'm') {
            num1 = last_result;
            cout << "Please input an operator (+, -, *, /): ";
            cin >> op;
        } else {
            cout << "Please input an integer number: ";
            cin >> num1;
        }
```

---

# Ex6 - Calculadora com memória

### Solução 

```C++
        cout << "Please input an integer number: ";
        int num2;
        cin >> num2;

        int result;

        if (op == '+') {
            result = num1 + num2;
        } else if (op == '-') {
            result = num1 - num2;
        } else if (op == '*') {
            result = num1 * num2;
        } else if (op == '/') {
            if (num2 == 0) {
                cout << "Invalid operation!" << endl;
                return -1;
            }
            result = num1 / num2;
        }
        cout << "Result: " << result << endl;
        last_result = result;
    }

    return 0;
}
```
---

# Funções

À medida que vamos expandindo a nossa aplicação, a nossa função `main` começa a ficar um pouco grande. Começa a aparecer código repetido e a ser difícil compreender imediatamente o que certas secções do código fazem.

Para resolver este problema, podemos dividir o código em várias **funções**.

Assim, o nosso código torna-se mais fácil de compreender e modular, sendo possível reutilizá-lo facilmente.

Declaração de uma função em C++:
```C++
int foo(int num, char a) {
    // ...
}
```

Para além dos vários tipos de dados, as funções podem não retornar nada, tendo o tipo `void`.

As funções têm que ser declaradas por ordem. Se uma função `a()` utiliza outra função `f()`, a declaração de `f()` tem que anteceder a de `a()`.

---

# Ex7 - Organizar

Vamos manter as funcionalidades da nossa calculadora, mas melhorar a organização do código.
- Cria funções para as principais funcionalidades do programa:
    - `void printGreeting()`
    - `char getOperator()`
    - `double getNum()`
    - `double calculateResult(double num1, double num2, char op)`

---

# Ex7 - Organizar

### Solução

```C++
void printGreeting() {
    cout << "Welcome to MyCalculator!" << endl;
    cout << "App developed by António Bezerra." << endl;
}

char getOperator() {
    cout << "Input an operator (+, -, *, /) - m to use last result - x to quit: ";
    char op;
    cin >> op;
    return op;
}

double getNum() {
    double num;
    cout << "Please input a number: ";
    cin >> num;
    return num;
}
```

---

# Ex7 - Organizar

### Solução

```C++
double calculateResult(double num1, double num2, char op) {
    double result;
    if (op == '+') {
        result = num1 + num2;
    } else if (op == '-') {
        result = num1 - num2;
    } else if (op == '*') {
        result = num1 * num2;
    } else if (op == '/') {
        if (num2 == 0) {
            cout << "Invalid operation!" << endl;
            return -1;
        }
        result = num1 / num2;
    }
    return result;
}
```

---

# Ex7 - Organizar

### Solução

```C++
int ex7() {
    printGreeting();
    double last_result = 0;
    while (true) {
        char op = getOperator();
        double num1;
        if (op == 'x') {
            break;
        } else if (op == 'm') {
            num1 = last_result;
            op = getOperator();
        } else {
            num1 = getNum();
        }
        double num2 = getNum();
        double result = calculateResult(num1, num2, op);
        cout << "Result: " << result << endl;
        last_result = result;
    }
    return 0;
}
```

---

# Strings

Em C++, `string` é um tipo de variável utilizado para armazenar texto.

Para utilizar strings no nosso programa, é necessário incluir a biblioteca de strings:
```C++
#include <string>

string texto = "Isto é um texto";
```

Strings são sempre delimitadas por `"`. Carateres sempre por `'`.

Ao contrário dos tipos básicos, strings são objetos e possuem métodos *built-in*. Existem também funções para converter de e para strings;

```C++
texto.size(); // = 15 - tamanho da string
texto.find("um") // = 7 - primeiro índice em que aparece a sequência "um"
int i = stoi("123") // Converte uma string para um valor inteiro
string str = to_string(6+36) // Converte um valor numérico para uma string
```

[Referência da biblioteca](http://www.cplusplus.com/reference/string/)

---

# Ex8 - Strings

Para já a nossa aplicação utiliza apenas tipos básicos de C++. No entanto, podemos torná-la mais resistente a erros do utilizador se utilizarmos strings para tratar do input, em conjunção com `getline()`. 
- Substitui a função `getOperator()` por `getWithMessage(string message)`, que retorna uma string de input do utilizador, mostrando anteriormente a mensagem `message`.
- Substitui a função `getNum()` por `to_num(string str)` que converte o parâmetro `str` num número. Deve conseguir converter as string "m" para o último resultado. Neste caso, imprime este valor.
- Usando estas novas funções, adapta o código do loop para que o utilizador possa sair do programa em qualquer fase da inserção de dados/operador. Permite também sair do loop escrevendo "exit".

Uso de `getline`:
```C++
string dest;
getline(cin, dest);
```

---

# Ex8 - Strings

### Solução

```C++
double last_result = 0; // Agora é global

void printGreeting() {
    cout << "Welcome to MyCalculator!" << endl;
    cout << "App developed by António Bezerra." << endl;
    cout << "Operators: + - * /" << endl;
    cout << "Accessing last result: m" << endl;
    cout << "Exiting: x or exit" << endl;
    cout << "---------------------------------" << endl;
}

string getWithMessage(string message) {
    string op;
    cout << message;
    getline(cin, op);
    return op;
}

double to_num(string str) {
    if (str == "m") {
        cout << "mem: " << last_result << endl;
        return last_result;
    }
    return stod(str);
}
```

---

# Ex8 - Strings

### Solução

```C++
double calculateResult(double num1, double num2, string op) {
    double result;
    if (op == "+") {
        result = num1 + num2;
    } else if (op == "-") {
        result = num1 - num2;
    } else if (op == "*") {
        result = num1 * num2;
    } else if (op == "/") {
        if (num2 == 0) {
            cout << "Invalid operation!" << endl;
            return -1;
        }
        result = num1 / num2;
    }
    return result;
}
```

---

# Ex8 - Strings

### Solução

```C++
int main() {
    printGreeting();

    while (true) {
        string aux = getWithMessage("Input first number: ");
        if (aux == "x" || aux == "exit") {
            break;
        } 
        double num1 = to_num(aux);

        aux = getWithMessage("Input operator: ");
        if (aux == "x" || aux == "exit") {
            break;
        }
        string op = aux;
        
        aux = getWithMessage("Input second number: ");
        if (aux == "x" || aux == "exit") {
            break;
        } 
        double num2 = to_num(aux);

        // ... O resto mantém-se
```

---

# STL - Standard Template Library

A Standard Template Library (STL) é um conjunto de classes que implementam algumas estruturas de dados e algoritmos mais comuns, entre outras funcionalidades.

Estas classes são chamadas *template* pois podem ser utilizadas com variáveis de qualquer tipo. No entanto, o tipo tem sempre que ser declarado.

As estrutras de dados mais comuns implementadas na STL são:

- `vector<T>` - guarda dados sequencialmente, fácil de iterar.
- `set<T>` - não admite duplicados, acesso rápido aos elementos.
- `map<T>` - semelhante a um dicionário, guarda pares chave-valor, não admite chaves duplicadas.

`T` representa o tipo dos dados armazenados na estrutura.

À exceção dos `array`, todas as estruturas de dados da STL têm tamanho dinâmico.

---

# Vetores

- São semelhantes a listas de Python.
- A inserção de dados é feita por defeito no final do vetor.
- O acesso aos dados numa determinada posição pode ser feito com `[]`.

### Exemplo

```C++
#include <vector>

vector<int> vec1 = {1, 2, 3, 4};
vector<string> vec2;
vec2.push_back("Um");
vec2.push_back("Dois");
vec2.push_back("Três");

vec1[0]; // = 1
vec2[2]; // = Três

vec1.size(); // = 4
vec2.size(); // = 3

vec1[2] = 4;
```

[Referência da biblioteca](http://www.cplusplus.com/reference/vector/vector/)

---

# Ex9 - Histórico

Vamos adicionar um histórico de resultados à nossa calculadora. O histórico pode ser consultado utilizando "m-N", em que N é o número de posições a retroceder. Se N for omitido, assume-se que se pretende o último resultado. Se N ultrapassar o tamanho do histórico, assume-se que se pretende o primeiro resultado.
- Substitui a variável que armazena o último resultado por um vetor.
- Cria uma nova função `getFromMem(string pos)` que consiga aceder à posição do histórico conforme especificado no enunciado.
- Procede aos ajustes necessários no resto do código.

**Tip:** 
- Podes utilizar o método `.substr(i)` para obter uma substring de uma string, começando na posição i.

---

# Ex9 - Histórico

### Solução

```C++
vector<double> result_history;

void printGreeting() {
    cout << "Welcome to MyCalculator!" << endl;
    cout << "App developed by António Bezerra." << endl;
    cout << "Operators: + - * /" << endl;
    cout << "Accessing N-th previous result: m-N" << endl;
    cout << "Exiting: x or exit" << endl;
    cout << "---------------------------------" << endl;
}

double getFromMem(string pos) {
    if (pos.size() == 1 && !pos.empty()) {
        return result_history.back();
    } else if (pos[1] == '-') {
        int shift = stoi(pos.substr(2));
        if (shift < result_history.size()) {
            return result_history[result_history.size() - 1 - shift];
        }
        return result_history[0];
    } else {
        return 0;
    }
}
```

---

# Ex9 - Histórico

### Solução

```C++
double to_num(string str) {
    if (str[0] == 'm') {
        double mem = getFromMem(str);
        cout << "mem: " << getFromMem(str) << endl;
        return mem;
    }
    return stod(str);
}

int main() {
    //...
        double result = calculateResult(num1, num2, op);
        cout << "Result: " << result << endl;
        result_history.push_back(result);
    // ...
}
```
---

# Classes

C++ acrescenta a C o suporte para programação orientada a objetos (POO).

Um objeto é uma entidade que pode conter dados e métodos para os manipular, garantido que apenas as funções do objeto podem aceder diretamente aos dados.

As **classes** são um tipo de dados definido pelo utilizador que representam objetos.
- Podem conter métodos (funções) ou atributos (variáveis) públicos (acedíveis em qualquer parte do código) ou privados (acedíveis apenas na própria classe).
- O construtor de uma classe cria um novo objeto do seu tipo de acordo com os parâmetros que recebe.
- É possível implementar relações entre classes, por exemplo, de herança. No entanto, não abordaremos estes aspetos no workshop.

---

# Classes

### Exemplo

```C++
class Foo {
private:
    int dataPriv1;
    string dataPriv2;

    void metodoPriv();
public:
    Foo(int data);
    int getData1();
    void setData1(int data);
    void metodoPub();
};
```

---

# Classes

### Exemplo

```C++
void Foo::metodoPriv() {
    // Código que implementa o método
}

int Foo::getData1() {
    return dataPriv1;
}

void Foo::setData1(int data) {
    dataPriv1 = data;
}

Foo::Foo(int data) {
    dataPriv1 = data;
}
```

---

# Classes

### Exemplo

```C++
int main() {
    Foo foo1(10);

    foo1.getData1(); // = 10
    foo1.setData1(2);
    foo1.getData1(); // = 2

    foo1.metodoPub(); // OK
    foo1.metodoPriv(); // Inválido
}
```

---

# Ex10 - Classes

Vamos transformar a nossa calculadora numa classe. O benefício principal da mudança para a classe será garantir que os dados do histórico, por exemplo, só são manipuláveis no contexto da calculadora.
- Cria a classe MyCalculator que contém:
    - Um método público `void run()` que executa o ciclo principal do programa.
    - Os métodos criados nos exercícios anteriores como privados.
    - Um vetor com o histórico de resultados também privado.
- **Extra:** cria um novo atributo `stop` para evitar a repetição de código que faz a verificação da string de saída.

---

# Ex10 - Classes

### Solução

```C++
class MyCalculator {
private:
    vector<double> result_history;
    bool stop = false;

    void printGreeting();
    string getWithMessage(string message);
    double getFromMem(string pos);
    double to_num(string str);
    double calculateResult(double num1, double num2, string op);
public:
    void run();
};
```

---

# Ex10 - Classes

### Solução

```C++
void MyCalculator::printGreeting() {
    cout << "Welcome to MyCalculator!" << endl;
    cout << "App developed by António Bezerra." << endl;
    cout << "Operators: + - * /" << endl;
    cout << "Accessing N-th previous result: m-N" << endl;
    cout << "Exiting: x or exit" << endl;
    cout << "---------------------------------" << endl;
}

string MyCalculator::getWithMessage(string message) {
    string op;
    cout << message;
    getline(cin, op);
    stop = (op == "x" || op == "exit");
    return op;
}
```

---

# Ex10 - Classes

### Solução

```C++
double MyCalculator::getFromMem(string pos) {
    if (pos.size() == 1 && !pos.empty()) {
        return result_history.back();
    } else if (pos[1] == '-') {
        int shift = stoi(pos.substr(2));
        if (shift < result_history.size()) {
            return result_history[result_history.size() - 1 - shift];
        }
        return result_history[0];
    } else {
        return 0;
    }
}

double MyCalculator::to_num(string str) {
    if (str[0] == 'm') {
        double mem = getFromMem(str);
        cout << "mem: " << getFromMem(str) << endl;
        return mem;
    }
    return stod(str);
}
```

---

# Ex10 - Classes

### Solução

```C++
double MyCalculator::calculateResult(double num1, double num2, string op) {
    double result;
    if (op == "+") {
        result = num1 + num2;
    } else if (op == "-") {
        result = num1 - num2;
    } else if (op == "*") {
        result = num1 * num2;
    } else if (op == "/") {
        if (num2 == 0) {
            cout << "Invalid operation!" << endl;
            return -1;
        }
        result = num1 / num2;
    }
    return result;
}
```

---

# Ex10 - Classes

### Solução

```C++
void MyCalculator::run() {
    printGreeting();

    while (true) {
        string aux = getWithMessage("Input first number: ");
        if (stop) {
            break;
        } 
        double num1 = to_num(aux);
        aux = getWithMessage("Input operator: ");
        if (stop) {
            break;
        }
        string op = aux;
        aux = getWithMessage("Input second number: ");
        if (stop) {
            break;
        } 
        double num2 = to_num(aux);

        double result = calculateResult(num1, num2, op);
        cout << "Result: " << result << endl;
        result_history.push_back(result);
    }
}
```

---

# Ex10 - Classes

### Solução

```C++
int main() {
    MyCalculator calc;

    calc.run();

    return 0;
}
```

---
# Recursos Recomendados

## Ferramenta de Desenvolvimento

- [Visual Studio Code](https://code.visualstudio.com/) & Extensão C/C++ & g++ (Linux/Mac)
- [Visual Studio](https://visualstudio.microsoft.com/) (Windows)
- [CLion](https://www.jetbrains.com/clion/) (Windows/Linux/Mac)

## Referência

- [cppreference](https://en.cppreference.com/w/)

## Livros

- The C++ Programming Language, 4ª Edição, de Bjarne Stroustrup
- Effective C++, 3ª Edição, de Scott Meyers

---

# The End

![Congratulations](https://i.imgur.com/qeGOBbl.jpeg)
