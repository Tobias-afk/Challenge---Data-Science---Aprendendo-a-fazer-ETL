# 📊 Customer Churn Challenge  

Este desafio tem como objetivo **analisar os clientes que tiveram evasão (churn)** em uma empresa, passando por todas as etapas do processo de análise de dados: desde a **extração** até a apresentação de um **relatório final**.  

---

## 🚀 Etapas do Projeto  

### 1️⃣ Extração de Dados  
Coletamos os dados de clientes a partir da base disponibilizada.  

```python
import pandas as pd  

# Leitura da base
df = pd.read_csv("dados_clientes.csv")

# Visualizando as 5 primeiras linhas
df.head()
```

---

### 2️⃣ Transformação dos Dados  
Antes da análise, realizamos uma **limpeza e preparação**:  

- 🔎 Verificação de valores nulos (NaN)  
- 📑 Remoção de duplicatas  
- 🔧 Ajustes de tipos de dados  

```python
# Valores nulos
print(df.isna().sum())

# Remoção de duplicatas
df = df.drop_duplicates()

# Ajuste de tipos
df['Churn'] = df['Churn'].astype('category')
```

---

### 3️⃣ Carga e Análise dos Dados  

#### 📌 Análise Descritiva  
Resumo estatístico das variáveis:  

```python
df.describe()
```

#### 📌 Distribuição de Evasão (Churn)  
```python
import matplotlib.pyplot as plt  

df['Churn'].value_counts().plot(kind='bar', figsize=(6,4))
plt.title("Distribuição de Evasão (Churn)")
plt.xlabel("Churn (Sim/Não)")
plt.ylabel("Quantidade de Clientes")
plt.show()
```

#### 📌 Contagem de Evasão por Variáveis Numéricas  
Exemplo: **Total Gasto** e **Tempo de Contrato**  

```python
import seaborn as sns  

# Total Gasto
sns.boxplot(x='Churn', y='TotalGasto', data=df)

# Tempo de Contrato
sns.boxplot(x='Churn', y='TempoContrato', data=df)
```

---

### LINK 🤖 :https://colab.research.google.com/drive/1OGo415dOtWj4Y2vo6f5j0mfdDJABzKhH?usp=sharing

### 4️⃣ 📑 Relatório Final  

Após a análise, observamos:  
- Clientes que **não cancelaram** tendem a gastar mais e manter contratos longos.  
- Clientes que **cancelaram** geralmente possuem **baixo gasto** e **contratos curtos**.  
- O período inicial do contrato é **crítico para retenção**.  

📌 **Recomendações:**  
- Fortalecer o **onboarding inicial** dos clientes.  
- Criar **estratégias de engajamento** para clientes de baixo gasto.  
- Monitorar **clientes de alto valor que cancelam**, evitando perdas significativas.  

---

## ✅ Conclusão  

Este challenge mostrou a importância de entender o perfil dos clientes que saem da empresa.  
Com uma análise exploratória e um relatório final, conseguimos identificar padrões de evasão e sugerir ações para melhorar a **retenção de clientes**.  

💡 *Próximos passos: aplicar modelos de Machine Learning para prever o churn antes que ele aconteça!* 🔮  
