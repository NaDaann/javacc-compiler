# Analisador Léxico e Sintático com JavaCC e JJTree

### Disciplina: Compiladores

### Curso: Ciência da Computação

### Faculdade Cotemig

### Autor: *\Daniel B. Miranda*

---

## 📌 Propósito do Projeto

Este projeto acadêmico tem como objetivo a criação de um **analisador léxico e sintático**, com geração de **árvore sintática** para uma linguagem fictícia, utilizando as ferramentas **JavaCC** e **JJTree**.

A implementação foi baseada em estruturas sintáticas comuns a linguagens reais, como Java, com foco em:

* Declaração de classes e variáveis
* Estruturas de controle (`if`, `while`, `for`)
* Operações de comparação (`==`, `!=`, `<`, `>`)
* Operações de incremento/decremento (`++`, `--`)

---

## 🧠 Conceitos Teóricos Aplicados

Este projeto envolve os seguintes conceitos centrais da disciplina de compiladores:

* **Análise Léxica**: Reconhecimento dos *tokens* (palavras-chave, identificadores, operadores, etc.).
* **Análise Sintática**: Construção da árvore de derivação baseada na gramática definida.
* **Árvore Sintática Abstrata (AST)**: Representação hierárquica do código fonte de entrada.
* **Gramática Livre de Contexto (CFG)**: Definição formal da linguagem a ser reconhecida.

---

## 📂 Estrutura de Arquivos

O projeto é composto pelos seguintes arquivos principais:

| Arquivo                                  | Descrição                                                                                      |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `MyParser.jj`                            | Arquivo principal do JavaCC contendo a **definição da gramática**, tokens e regras sintáticas. |
| `MyParser.jjt`                           | Arquivo JJTree que estende o `.jj`, utilizado para gerar a árvore sintática.                   |
| `MyParser.java`                          | Código Java gerado automaticamente a partir do `.jj` ou `.jjt`.                                |
| `Token.java`, `TokenMgrError.java`, etc. | Arquivos auxiliares gerados automaticamente pelo JavaCC.                                       |
| `input.txt`                              | Arquivo de exemplo com o código-fonte da linguagem para teste.                                 |
| `output.txt` (opcional)                  | Saída gerada pelo analisador (mensagens ou árvore).                                            |
| `README.md`                              | Documento de explicação detalhada do projeto.                                                  |
| `RelatorioFinal.pdf`                     | Relatório formal explicando a gramática e a implementação.                                     |
| `codigo.txt`                             | Versão comentada do código-fonte para entrega.                                                 |
| `video_link.txt`                         | Link para o vídeo demonstrativo no YouTube.                                                    |

---

## ▶️ Como Executar o Projeto

> ⚠️ **Pré-requisito**: Java instalado e variáveis de ambiente configuradas.

1. Compile o analisador:

```bash
jjtree -OUTPUT_DIRECTORY=parser MyParser.jjt
cd parser && javacc MyParser.jj
```

> Isso gerará os arquivos `.java` do analisador.

2. Compile os arquivos `.java` gerados:

```bash
cd .. && javac parser/*.java
```

3. Execute o analisador:

```bash
java parser.MyParser parser/input.txt
```

---

## 📅 Entrada Esperada

O analisador espera um arquivo de entrada (`input.txt`) contendo código com a seguinte estrutura sintática:

```java
class Exemplo {
    int contador = 0;
    boolean ativo;

    void executar() {
        while (contador < 10) {
            contador++;
        }

        if (ativo == true) {
            contador--;
        }
    }
}
```

Este é apenas um exemplo. A gramática reconhece:

* Classes com nome
* Declarações de variáveis com ou sem valor inicial
* Métodos sem retorno
* Blocos `if`, `while`, `for`
* Operadores `==`, `!=`, `<`, `>`, `++`, `--`

---

## 📤 Saída Gerada

Dependendo da configuração da gramática e uso de JJTree, o analisador pode:

* Mostrar mensagens de sucesso/erro sintático
* Gerar uma árvore sintática impressa no console
* Exibir tokens identificados
* Indicar o ponto exato de erro em caso de falha

Exemplo de saída:

```
Parsing successful.
Tree generated:
Program
 Class
  VarDecl
   Type
   Value
  VarDecl
   Type
   Value
  VarDecl
   Type
  VarDecl
   Type
  Method
   Block
    While
     Condition
      ExprOrVal
      Comparison
      ExprOrVal
       Value
     Block
      Stmt
       Expr
        Inc
    If
     Condition
      ExprOrVal
      Comparison
      ExprOrVal
       Value
     Block
      Stmt
       Expr
        Dec
```

---

## 📝 Observações Relevantes

* A gramática foi definida com **clareza e modularidade**, visando a fácil manutenção e extensibilidade.
* Foram aplicadas **boas práticas de documentação** nos comentários do código.
* A árvore sintática gerada é útil para etapas posteriores, como geração de código ou interpretação.
* O projeto é **individual**, e qualquer semelhança excessiva com outros será penalizada conforme critérios de avaliação.

---

## ⚠️ Possíveis Limitações

* A linguagem reconhecida é simplificada e não cobre todos os aspectos de linguagens reais.
* Não há verificação semântica (ex: tipos ou escopo de variáveis).
* O analisador assume que a entrada está razoavelmente formatada (não lida com todos os tipos de erro).
* A árvore sintática pode não ser otimizada para linguagens reais.

---

## 📌 Informações Complementares

* Referências:

  * Documentação oficial do JavaCC: [https://javacc.github.io/javacc/](https://javacc.github.io/javacc/)
