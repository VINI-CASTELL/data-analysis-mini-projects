# IBGE API Analysis

Projeto em Python para consultar, organizar e visualizar dados públicos disponibilizados pelas APIs do IBGE.

## Objetivo

O projeto demonstra como consumir APIs REST, validar respostas HTTP, transformar estruturas JSON em DataFrames e produzir análises simples com dados públicos.

As análises incluídas são:

- comparação do PIB per capita de Brasil e Estados Unidos;
- evolução do percentual de indivíduos com acesso à internet no Brasil;
- ranking dos nomes mais frequentes no país.

## Melhorias aplicadas

- funções reutilizáveis para chamadas HTTP e tratamento dos dados;
- validação de status da resposta com `raise_for_status()`;
- limite de tempo para evitar requisições travadas;
- mensagens de erro mais claras quando a API não devolve JSON;
- conversão segura dos valores para tipos numéricos;
- gráficos com títulos e eixos identificados;
- separação entre coleta, tratamento, análise e visualização;
- nomes de variáveis padronizados.

## Estrutura

```text
ibge-api-analysis/
├── ibge_api_analysis.ipynb
├── README.md
└── requirements.txt
```

## APIs utilizadas

- API Países, versão 1
- API Nomes, versão 2

Os indicadores utilizados são:

- `77823`: PIB per capita;
- `77857`: indivíduos com acesso à internet.

## Como executar

1. Abra a pasta no VS Code.
2. Crie um ambiente virtual:

```bash
python -m venv .venv
```

3. Ative o ambiente no Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

4. Instale as dependências:

```bash
pip install -r requirements.txt
```

5. Abra `ibge_api_analysis.ipynb`.
6. Selecione o ambiente `.venv` como kernel.
7. Execute as células em ordem ou use **Run All**.

## Observação sobre disponibilidade

Os resultados dependem da disponibilidade e da estrutura atual das APIs do IBGE. O notebook valida as respostas e apresenta mensagens claras quando um endpoint está indisponível ou devolve um formato inesperado.

## Nota sobre projeções populacionais

O material original utilizava um endpoint de projeções populacionais que retornou uma resposta incompatível com JSON. Como esse serviço não aparece atualmente no catálogo principal de APIs do IBGE, ele não foi mantido no fluxo executável deste projeto.

## Tecnologias

`Python` · `requests` · `pandas` · `Matplotlib` · `Jupyter Notebook`
