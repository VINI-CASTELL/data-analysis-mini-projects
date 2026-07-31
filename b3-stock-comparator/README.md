# B3 Stock Comparator

Projeto em Python para comparar o desempenho histórico de ações, ETFs e índices relacionados ao mercado brasileiro.

## Objetivo

O projeto baixa preços históricos ajustados e compara os ativos selecionados por meio de indicadores de retorno, risco e perda acumulada.

A análise inclui:

- retorno total;
- retorno anualizado;
- volatilidade anualizada;
- índice de Sharpe;
- índice de Sortino;
- máximo drawdown;
- índice de Calmar;
- melhor e pior retorno diário;
- percentual de dias positivos;
- correlação entre os ativos;
- evolução de um investimento inicial;
- retornos anuais;
- rankings por retorno e retorno ajustado ao risco.

## Melhorias aplicadas

A versão original foi reorganizada e modernizada com:

- funções reutilizáveis;
- configuração centralizada;
- data final automática para usar os dados mais recentes disponíveis;
- download conjunto dos ativos com `yfinance.download`;
- compatibilidade com as colunas multinível retornadas pelo `yfinance`;
- uso de preços ajustados por proventos e desdobramentos;
- tentativa de reparo de anomalias de preço com `repair=True`;
- tratamento explícito de valores ausentes;
- uso de `pct_change(fill_method=None)`;
- taxa livre de risco configurável;
- novos indicadores de risco;
- mensagens de erro mais claras;
- salvamento opcional de tabelas e gráficos;
- células Markdown com metodologia, interpretação e limitações.

## Estrutura

```text
b3-stock-comparator/
├── reports/
│   ├── figures/
│   └── tables/
├── b3_stock_comparator.ipynb
├── README.md
└── requirements.txt
```

## Ativos

Os ativos negociados na B3 normalmente utilizam o sufixo `.SA` no Yahoo Finance.

Exemplos:

- `PETR4.SA`
- `VALE3.SA`
- `WEGE3.SA`
- `BOVA11.SA`

No notebook, o sufixo é acrescentado automaticamente quando o usuário informa apenas `PETR4`, `VALE3` ou outro código simples da B3.

Símbolos especiais, como `^BVSP`, devem ser informados completos.

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

5. Abra `b3_stock_comparator.ipynb`.
6. Selecione o ambiente `.venv` como kernel.
7. Ajuste a célula de configurações.
8. Execute as células em ordem ou use **Run All**.

## Configurações principais

```python
ATIVOS = ["PETR4", "VALE3", "WEGE3", "BOVA11"]
DATA_INICIO = "2015-01-01"
DATA_FIM = None
VALOR_INICIAL = 10_000
TAXA_LIVRE_RISCO_ANUAL = 0.0
SALVAR_RESULTADOS = False
```

Quando `DATA_FIM = None`, o notebook busca os dados mais recentes disponíveis no momento da execução.

## Resultados gerados

Quando `SALVAR_RESULTADOS = True`, o notebook cria:

- tabelas CSV em `reports/tables`;
- gráficos PNG em `reports/figures`.

## Fonte dos dados

Os dados são consultados por meio da biblioteca `yfinance`, que utiliza dados públicos disponibilizados pelo Yahoo Finance.

O `yfinance` é uma ferramenta de código aberto, não oficial e destinada principalmente a pesquisa e uso educacional. A disponibilidade e a estrutura dos dados podem mudar.

## Limitações

- resultados passados não garantem resultados futuros;
- a análise não considera impostos, corretagem, spread ou liquidez;
- o valor final usa preços ajustados, mas não representa uma execução real;
- a taxa livre de risco precisa ser configurada pelo usuário;
- ativos com históricos diferentes são comparados apenas no período comum;
- falhas ou mudanças no Yahoo Finance podem afetar o download.

## Aviso

Este projeto possui finalidade educacional e não constitui recomendação de investimento.

## Tecnologias

`Python` · `pandas` · `NumPy` · `Matplotlib` · `yfinance` · `Jupyter Notebook`
