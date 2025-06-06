# Guia de Instalação do JavaCC, JJTree e JFlex (Windows, Mac e Linux)

## 1. Pré-requisitos
- Java 22 (ou superior) instalado
- Git e VS Code (opcional)

## 2. Instalar JavaCC (com JJTree)

### Via Gerenciador de Pacotes
- **Linux/Mac**: `brew install javacc`
- **Windows**: `choco install javacc`

### Manual
1. Baixe o JavaCC do site oficial
2. Extraia o arquivo (zip ou tar.gz)
3. Configure o PATH e torne os scripts executáveis (consulte detalhes no guia)

## 3. Verificação JavaCC/JJTree
- `javacc`
- `jjtree`

## 4. Instalar JFlex

### Via Gerenciador de Pacotes
- **Linux/Mac**: `brew install jflex`
- **Windows**: `choco install jflex`

### Manual
1. Baixe o JFlex do site oficial
2. Extraia o arquivo (tar.gz)
3. Configure o PATH (ou symlink no Linux/Mac)

## 5. Verificação JFlex
- `jflex --version`

## 6. Integração com VS Code
- Instale a extensão Java Extension Pack
- Configure tarefas no `tasks.json`

## 7. Dicas Windows
- Use `javacc`, `jjtree` e `jflex` no Prompt de Comando ou PowerShell
- Ou use: `java -jar javacc.jar` e `java -jar jflex.jar`

## 8. Atualizações
- **Linux/Mac**: `brew update && brew upgrade javacc jflex`
- **Windows**: `choco upgrade javacc jflex`

## 9. Links Úteis
- [JavaCC Downloads](https://javacc.github.io/javacc/)
- [JFlex Downloads](https://jflex.de/download.html)

---

Pronto para uso em qualquer plataforma!