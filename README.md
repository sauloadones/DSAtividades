# 📈 Previsão de Transações Financeiras com Prophet

Este projeto utiliza o modelo Prophet, desenvolvido pelo Facebook, para realizar previsões de séries temporais financeiras com base em dados trimestrais do Banco Central do Brasil (ETL BCB).

## 🔍 Objetivo

Prever o comportamento de variáveis financeiras ao longo do tempo, com foco nas seguintes operações:

- `valorPix`
- `valorTED`
- `valorCartaoCredito` (originalmente abordado na Aula 10)

## 🧾 Fonte de Dados

O conjunto de dados utilizado possui colunas como:

- `datatrimestre`: data de referência trimestral
- `valorPix`, `valorTED`, `valorCartaoCredito`, `valorBoleto`, `valorDOC`, etc.
- `quantidadePix`, `quantidadeTED`, `quantidadeCartaoCredito`, etc.

Formato CSV com separador `;` e separador decimal `,`.

## 🛠 Tecnologias Utilizadas

- Python 3.10
- [Prophet (Facebook)](https://facebook.github.io/prophet/)
- Pandas
- Matplotlib

## ⚙️ Etapas de Execução

1. **Pré-processamento**:
   - Conversão da coluna `datatrimestre` para datetime.
   - Conversão dos valores monetários para `float`.

2. **Treinamento do modelo Prophet**:
   - Separação da variável de interesse (`ds` = data, `y` = valor).
   - Treinamento com `Prophet()`.
   - Geração de previsão para os próximos 4 trimestres.

3. **Visualização**:
   - Gráfico contendo:
     - Histórico (azul)
     - Modelagem (verde tracejada)
     - Previsão (vermelha tracejada)
     - Intervalo de confiança (faixa vermelha clara)

## 📊 Exemplo de Gráfico

![Exemplo de Previsão com Prophet](./caminho-para-exemplo.png)

## 📦 Exportação

Os dados previstos podem ser exportados para CSV com:

```python
forecast[['ds', 'yhat', 'yhat_lower', 'yhat_upper']].to_csv('previsao_pix.csv', index=False)
