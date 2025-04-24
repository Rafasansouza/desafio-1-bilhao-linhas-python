# Desafio de Processamento de 1 Bilhão de Linhas com Python

Este projeto foi desenvolvido durante a **Aula 5 do Bootcamp de Python para dados da Jornada de Dados**, com o objetivo de aplicar técnicas eficientes de processamento de dados em larga escala utilizando Python e bibliotecas de alto desempenho.

## 📌 Descrição do Projeto

O desafio consistiu em processar um arquivo massivo com **1 bilhão de linhas (~14GB) (na execução adaptamos para 1 milhão de linhas)** contendo registros de temperatura de estações meteorológicas no seguinte formato:

```
<nome da estação>;<medição>
```

Exemplo:
```
Hamburg;12.0  
Bulawayo;8.9  
Palembang;38.8  
St. Johns;15.2  
```

O objetivo foi calcular, para cada estação:

- Temperatura **mínima**
- Temperatura **média** (com 1 casa decimal)
- Temperatura **máxima**

Além disso, o projeto compara o desempenho de diferentes bibliotecas Python utilizadas para a mesma tarefa, focando na eficiência e no tempo de execução.

## 📚 Aprendizados

Durante o desenvolvimento, pude explorar diversos conceitos fundamentais para quem trabalha com grandes volumes de dados:

- Leitura eficiente de arquivos massivos com Python
- Cálculo de estatísticas agregadas
- Avaliação de performance entre diferentes bibliotecas
- Otimização com bibliotecas de consulta orientadas a colunas
- Análise e visualização de benchmarks

## ⚙️ Tecnologias Utilizadas

- [Python 3.12.1](https://docs.python.org/release/3.12.1/)
- [Polars 0.20.3](https://pola.rs/)
- [DuckDB 0.10.0](https://duckdb.org/)
- [Dask 2024.2.0](https://www.dask.org/)
- [Pandas](https://pandas.pydata.org/)
- [Poetry](https://python-poetry.org/) (gerenciador de dependências)
- Bash + awk (como benchmark adicional)

## 🚀 Resultados

Houve uma adaptação ao longo do projeto, para andar mais rapido alteramos o arquivo "create..." na pasta "src" para criar apenas um arquivo de 1M de linhas.
O **DuckDB** apresentou o melhor desempenho, graças à sua arquitetura otimizada para leitura de dados em colunas e execução vetorizada.

## 🛠️ Como Executar

### 1. Clone este repositório
```bash
git clone https://github.com/Rafasansouza/desafio-1-bilhao-linhas-python.git
cd desafio-1-bilhao-linhas-python
```

### 2. Configure o ambiente
```bash
pyenv local 3.12.1
poetry env use 3.12.1
poetry install --no-root
poetry lock --no-update
```

### 3. Gere o arquivo de dados
```bash
python src/create_measurements.py
```

*Observação: A geração do arquivo leva cerca de 10 minutos e o arquivo final tem aproximadamente 14GB.*

### 4. Execute os scripts
```bash
python src/using_python.py
python src/using_pandas.py
python src/using_dask.py
python src/using_polars.py
python src/using_duckdb.py
```

## 🧪 Benchmark Extra com Bash + awk

Você também pode testar a versão em Bash com:

```bash
chmod +x src/using_bash_and_awk.sh
./src/using_bash_and_awk.sh 1000
```

Certifique-se de ter as ferramentas `awk`, `sort`, e `pv` (Pipe Viewer) instaladas.

### Para instalar `pv`:
- No Ubuntu/Debian:
```bash
sudo apt-get update
sudo apt-get install pv
```

- No macOS (com Homebrew):
```bash
brew install pv
```

## 🎯 Conclusão

Este projeto foi uma ótima oportunidade para colocar em prática tudo que venho aprendendo sobre **processamento de dados em larga escala com Python**. Descobri que com as bibliotecas certas — como **Polars** e **DuckDB** — é possível lidar com datasets gigantescos de forma muito mais rápida e eficiente, mesmo em máquinas com poucos recursos.

Além de aprofundar o uso de bibliotecas como Pandas, Dask e DuckDB, o projeto me ensinou a importância de benchmarking e de escolher a tecnologia certa para o desafio proposto.

## 🔗 Repositório de Referência

Este projeto foi inspirado e adaptado a partir do bootcamp de python para dados da **Jornada de dados** [lvgalvao/One-Billion-Row-Challenge-Python](https://github.com/lvgalvao/One-Billion-Row-Challenge-Python).
