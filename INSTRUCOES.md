# Instruções de Compilação e Execução

## Pré-requisitos

1. Java JDK instalado (versão 22 ou superior)
2. JavaCC instalado
3. Variáveis de ambiente configuradas corretamente

## Estrutura do Projeto

O projeto contém os seguintes arquivos principais:

- `MyParser.jjt`: Arquivo principal com a gramática da linguagem
- `input.txt`: Arquivo de exemplo com código na linguagem definida
- `INSTRUCOES.md`: Este arquivo com instruções de uso

## Passos para Compilação

1. Primeiro, gere os arquivos Java a partir do arquivo .jjt:
```bash
jjtree MyParser.jjt
```

2. Em seguida, gere o parser a partir do arquivo .jj gerado:
```bash
javacc MyParser.jj
```

3. Compile todos os arquivos Java gerados:
```bash
javac *.java
```

## Execução

Para executar o parser com o arquivo de exemplo:
```bash
java MyParser input.txt
```

## Saída Esperada

O programa irá gerar uma árvore sintática que representa a estrutura do código de entrada. A saída deve ser similar a:

```
Parsing completed successfully.
Program
  ClassDeclaration: ExemploCompleto
    VarDeclaration: contador = 0
    VarDeclaration: ativo = true
    VarDeclaration: soma
    VarDeclaration: finalizado
    MethodDeclaration: executar
      WhileStatement
        Condition: contador < 10
        Expression: contador++
      IfStatement
        Condition: ativo == true
        Expression: contador--
      ForStatement
        Expression: soma = 0
        Condition: soma < 5
        Expression: soma++
        IfStatement
          Condition: soma != 3
          Expression: ativo = false
      IfStatement
        Condition: contador >= 10
        Expression: finalizado = true
      IfStatement
        Condition: soma <= 5
        Expression: finalizado = false
```

## Funcionalidades Suportadas

A gramática reconhece:

1. Declarações de classe
2. Declarações de variáveis (com ou sem atribuição inicial)
   - Tipos suportados: int, boolean
3. Métodos void
4. Estruturas de controle:
   - if
   - while
   - for
5. Operadores de comparação:
   - == (igual)
   - != (diferente)
   - < (menor que)
   - > (maior que)
   - <= (menor ou igual)
   - >= (maior ou igual)
6. Operadores de incremento/decremento:
   - ++ (incremento)
   - -- (decremento)

## Tratamento de Erros

O parser irá reportar erros sintáticos com mensagens indicando a linha e coluna onde o erro foi encontrado.

## Observações

- A gramática foi projetada para ser simples e didática
- Comentários são suportados (tanto // quanto /* */)
- A indentação não é significativa para a análise
- A árvore sintática gerada mostra a estrutura hierárquica do código 

## Comandos para execução:

- jjtree -OUTPUT_DIRECTORY=parser MyParser.jjt
cd parser && javacc MyParser.jj
cd .. && javac parser/*.java
java parser.MyParser parser/input.txt