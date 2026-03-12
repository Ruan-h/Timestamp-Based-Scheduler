# Timestamp-Based Scheduler (Escalonador Baseado em Timestamp)

Este projeto implementa um verificador de escalonamentos de transações para sistemas de banco de dados. O objetivo é determinar se uma execução concorrente de transações é **serializável**, garantindo que ela produza o mesmo resultado que uma execução serial. 

Para isso, o sistema utiliza o algoritmo de **Escalonador Baseado em Timestamp** (Timestamp-Based Scheduling), que atribui marcas de tempo únicas para manter a ordem de precedência das operações de leitura (Read) e escrita (Write).

Projeto desenvolvido como parte do Trabalho III da disciplina de Sistemas de Bancos de Dados (CK0117).

## ⚙️ Funcionalidades Implementadas

O sistema atende a todos os requisitos propostos:
- [x] Leitura de escalonamentos a partir de um arquivo padrão `in.txt`.
- [x] Verificação de serialização baseada na estrutura de dados `<ID-dado, TS-Read, TS-Write>`. A estrutura é reinicializada a cada novo escalonamento.
- [x] Geração de um arquivo de log geral `out.txt` com o status final de cada escalonamento (Serial/OK ou ROLLBACK com o momento da falha).
- [x] Criação automática de arquivos de log individuais para cada objeto de dado (ex: arquivo para `X`, `Y`, `Z`) detalhando o ID do escalonamento, a operação e o momento exato em que ocorreu.

## 📂 Formato de Entrada (`in.txt`)

O arquivo de entrada deve seguir rigorosamente a seguinte estrutura:
1. Lista de objetos de dados.
2. Lista de transações.
3. Timestamps das transações (na mesma ordem).
4. Linhas subsequentes contendo os escalonamentos (iniciados por `E_X`).

**Exemplo de `in.txt`:**
X, Y, Z;
t1, t2, t3;
5, 10, 3;
E_1-r1(X)
r2(Y)
W2(Y)
...

## 📄 Formato de Saída (`out.txt`)

O programa analisa os escalonamentos e gera o arquivo `out.txt`. O "momento" é definido como uma contagem sequencial (iniciando em zero) de todas as operações realizadas até a operação atual.

**Exemplo de saída esperada:**
E_1-ROLLBACK-3
E_2-ROLLBACK-2
E_3-OK

## 🚀 Como Compilar e Executar no Linux/Ubuntu

O projeto foi desenvolvido em C/C++. Para rodar o projeto localmente no seu terminal:

1. **Clone o repositório:**
git clone https://github.com/Ruan-h/Timestamp-Based-Scheduler.git
cd Timestamp-Based-Scheduler

2. **Compile o código:**
*(Se estiver usando C)*
gcc main.c -o escalonador

*(Se estiver usando C++)*
g++ main.cpp -o escalonador

3. **Execute:**
Certifique-se de que o arquivo `in.txt` está no mesmo diretório do executável antes de rodar.
./escalonador

Após a execução, os arquivos `out.txt` e os logs individuais dos objetos de dados serão gerados automaticamente na pasta.

## 👨‍💻 Autor
* **Ruan**
