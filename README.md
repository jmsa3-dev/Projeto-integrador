# Geração renovável e exportação de energia no Nordeste (2023–2025)

## Objetivo

O Nordeste concentra boa parte da geração eólica e solar do Brasil e, quando gera mais do que consome, exporta o excedente para outras regiões. Este projeto analisa como a geração eólica e solar se relaciona com a energia exportada pela região entre 2023 e 2025, e em quais meses e horários essa exportação é maior.

A ideia é apoiar o planejamento do setor elétrico na identificação dos períodos de maior uso das linhas de transmissão.

**Pergunta:** Como a geração eólica e solar do Nordeste se relaciona com a energia exportada pelo subsistema entre 2023 e 2025, e em quais meses e horários a exportação é maior?

**Hipótese:** A exportação aumenta quando a geração eólica é maior.

## Dados

- **Fonte:** ONS (Operador Nacional do Sistema Elétrico), base *Balanço de Energia nos Subsistemas*, disponível no Portal de Dados Abertos do ONS (https://dados.ons.org.br).
- **Período:** 2023 a 2025, um arquivo CSV por ano.
- **Granularidade:** uma linha por hora e por subsistema (Norte, Nordeste, Sudeste/Centro-Oeste, Sul e SIN).
- **Principais colunas usadas:** `din_instante`, `id_subsistema`, `val_gereolica`, `val_gersolar`, `val_carga` e `val_intercambio`.

Os três arquivos anuais devem ser colocados na pasta `dados/` antes de rodar o notebook.

## Estrutura do projeto

```
NomeSobrenome_Projeto/
├── README.md          # descrição do projeto
├── requirements.txt   # bibliotecas necessárias
├── projeto.ipynb      # notebook com toda a análise
├── dados/             # CSVs brutos do ONS (2023, 2024 e 2025)
└── resultados/        # base consolidada e gráficos gerados pelo notebook
```

## Como executar

1. Instale as dependências:
   ```
   pip install -r requirements.txt
   ```
2. Baixe os arquivos do ONS e coloque na pasta `dados/`.
3. Abra o `projeto.ipynb` e rode todas as células (*Run All*).

O notebook consolida os três anos em `resultados/BALANCO_ENERGIA_SUBSISTEMA_2023_a_2025.csv` e salva todos os gráficos em `resultados/`.

## Etapas da análise

1. **Problema e pergunta analítica:** contexto, público, decisão apoiada e hipótese.
2. **Extração e consolidação:** leitura dos três arquivos e criação de uma base única.
3. **Revisão e limpeza:** checagem de nulos e duplicados e conversão das datas.
4. **Análise exploratória:** comparação entre regiões, sazonalidade mensal, padrão por hora (heatmaps), correlação e perfil médio diário.
5. **Conclusões:** resposta à pergunta, comparação entre anos e limitações.

## Principais resultados

- O Nordeste concentra cerca de 92% da geração eólica do país.
- A geração eólica tem correlação forte com o intercâmbio (0,78), enquanto a solar tem correlação fraca (0,16) e a carga praticamente nenhuma (−0,02). **A hipótese foi confirmada.**
- A relação com a eólica se manteve forte nos três anos, mas diminuiu de 0,84 (2023) para 0,70 (2025).
- A exportação é maior entre julho e outubro, com pico em setembro e outubro, e nos horários da madrugada e do início da manhã (6h–9h).
- O fim da tarde (16h–18h) é o momento mais fraco: a solar acaba antes de a eólica ganhar força, e no primeiro semestre a região chega a importar energia.
- O volume exportado no pico cresce a cada ano, o que indica pressão crescente sobre a transmissão.

## Limitações

- A base não informa a capacidade instalada, então parte do crescimento pode vir de novas usinas, e não de mais vento ou sol.
- Correlação não prova causa.

## Autor

Jamila-Maria de Souza Abid