## Detalhes Técnicos e Estruturas de Dados
O código foi modularizado para separar as lógicas de manipulação de bits, estruturas de dados e entrada/saída. As principais estruturas utilizadas foram:

* **Fila de Prioridade (Min-Heap):** Implementada através de uma lista encadeada ordenada pela frequência de aparição de cada byte no arquivo original.
* **Árvore Binária de Huffman:** Construída a partir da extração dos nós de menor frequência da fila. Os nós folhas (que contêm os caracteres originais) são identificados essencialmente por possuírem seus ponteiros de filhos (`left` e `right`) apontando para `NULL`. 
* **Travessia em Pré-ordem:** A árvore é serializada no cabeçalho do arquivo compactado usando travessia em pré-ordem, utilizando o caractere `*` para nós internos e `\` como caractere de escape estrutural.
* **Manipulação de Bits (Bitwise):** Uso de operadores lógicos (shifts e máscaras) para empacotar os caminhos da árvore de Huffman em bytes reais, otimizando o tamanho final do arquivo.

## Estrutura do Projeto
- `main.c`: Ponto de entrada, menu interativo e chamadas principais.
- `codificacao.c`: Lógica central de leitura de arquivos, cálculo de frequência, e orquestração da compactação/descompactação.
- `arvoreHuffman.c`: Funções de criação, travessia e reconstrução da árvore binária.
- `fila.c`: Gerenciamento da fila de prioridade usada na montagem da árvore.
- `bytes.c`: Funções de baixo nível para manipulação de bits, criação do cabeçalho e escrita do dicionário/mapa.

## Como Compilar e Executar

Certifique-se de ter o compilador GCC instalado na sua máquina.

1. Clone o repositório ou baixe os arquivos.
2. Abra o terminal na pasta do projeto e compile com os seguintes comandos:

**No Windows:**
```cmd
gcc -o huffman.exe main.c arvoreHuffman.c codificacao.c bytes.c fila.c
```
**No Linux:**
```bash
gcc -o huffman main.c arvoreHuffman.c codificacao.c bytes.c fila.c
```
