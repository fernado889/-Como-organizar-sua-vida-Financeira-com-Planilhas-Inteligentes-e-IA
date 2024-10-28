# -Como-organizar-sua-vida-Financeira-com-Planilhas-Inteligentes-e-IA
| A            | B          | C          | D          | E          | F          |
|--------------|------------|------------|------------|------------|------------|
| Data         | Descrição  | Categoria  | Valor      | Previsão   | Recomendações|
| 01/10/2024   | Aluguel    | Moradia    | 1200       | 1250       | Reduzir gastos em lazer |
| 02/10/2024   | Supermercado| Alimentação| 300        | 320        | Comprar em atacado |
| 03/10/2024   | Transporte  | Transporte  | 150        | 160        | Usar transporte público |
| 04/10/2024   | Lazer       | Lazer      | 200        | 180        | Limitar saídas |
|--------------|------------|------------|------------|------------|------------|
| Total        |            |            | =SOMA(D2:D5)|            |            |
import pandas as pd

# Carregar dados da planilha
df = pd.read_csv('financas.csv')

# Análise de gastos
gastos_totais = df['Valor'].sum()
media_gastos = df['Valor'].mean()

# Previsão simples (exemplo)
df['Previsão'] = df['Valor'].shift(1) * 1.05  # Aumenta 5% em relação ao mês anterior

# Recomendações
def recomendacao(row):
    if row['Valor'] > 300:
        return 'Considere reduzir gastos nesta categoria.'
    return 'Gastos dentro do esperado.'

df['Recomendações'] = df.apply(recomendacao, axis=1)

# Salvar resultados
df.to_csv('financas_analise.csv', index=False)
