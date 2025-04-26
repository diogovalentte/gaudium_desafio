# Desafio Gaudium

# Objetivo

Criar um data mart para venda de produtos aplicando o modelo dimensional.

# Fonde de Dados

A fonte de dados utilizada para o desafio foi o arquivo CSV `tabelas/dados_brutos.csv`, que contém informações sobre vendas de produtos:

# Esquema do Data Mart

As seguintes tabelas de dimensão e fato foram criadas. O modelo dimensional facilita a análise de dados e a geração de relatórios usando chaves primárias e estrangeiras.

As tabelas foram salvas no diretório `tabelas/` com os seguintes nomes:

- `dim_cliente.csv`: Tabela de dimensão com informações sobre os clientes.
- `dim_endereco.csv`: Tabela de dimensão com informações sobre os endereços dos clientes. Endereços foram extraídos para uma tabela própria para diminuir a redundância de dados.
- `dim_produto.csv`: Tabela de dimensão com informações sobre os produtos.
- `dim_categoria.csv`: Tabela de dimensão com informações sobre as categorias dos produtos. Categórias foram extraídas para uma tabela própria para facilitar a atualização de categórias independente dos produtos.
- `dim_fabricante.csv`: Tabela de dimensão com informações sobre os fabricantes dos produtos. Fabricantes foram extraídas para uma tabela própria para facilitar a atualização de categórias independente dos produtos.
- `dim_data.csv`: Tabela de dimensão com informações sobre as datas. Informações adicionais sobre a data foram extraidas para colunas próprias para facilitar queries.
- `fato_vendas.csv`: Tabela de fato com informações sobre as vendas.

# ETL

Para fazer a extração, transformação e carga (ETL) dos dados, foi utilizado o arquivo jupyter notebook `etl.ipynb`. Ele contém o código necessário para processar os dados e gerar as tabelas de dimensão e fato.

O código foi desenvolvido em **PySpark SQL**.

# Como Executar

## Manualmente

1. Suba o diretório do projeto para um ambiente com suporte a PySpark (Databricks, Fabric ou local com Spark configurado).
2. Execute o notebook para gerar os arquivos finais.
3. Os resultados serão salvos como arquivos `.csv` na pasta `tabelas/`.

## Docker

Esse repositório contém o arquivo `docker-compose.yml` para facilitar a execução do projeto em um ambiente Docker. Esse arquivo define um container para iniciar o ambiente do Jupyter Notebook com PySpark pré-configurado usando a image `jupyter/pyspark-notebook`.

1. Certifique-se de ter o Docker e o Docker Compose instalados em sua máquina.
2. Inicie o container com o seguinte comando:

```bash
docker-compose up -d
```

3. Pegue o token usado para login no Jupyter Notebook usando o seguinte comando:

```bash
docker exec pyspark-jupyter jupyter server list
```

Ele deve retornar algo como:

```bash
http://d05e56f01eb0:8888/?token=f8b958937d6d479538a32cd3f0752f9292e269710b32ce23 :: /home/jovyan
```

O token é a parte após `token=`.

4. Acesse o Jupyter Notebook no navegador em `http://localhost:8888/lab` e use o token exibido no terminal para fazer login.
5. Use a aba lateral esquerda para navegar até o diretório do projeto e abra o arquivo `etl.ipynb`.
