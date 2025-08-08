# 🚗 Projeto: Análise e Preparação de Dados de Veículos Elétricos

## 📌 Descrição
Este projeto realizou uma **análise exploratória aprofundada** e um **pré-processamento rigoroso** do dataset **Electric Vehicles Specification 2025**, com o objetivo de investigar as relações entre as especificações técnicas dos veículos elétricos e sua autonomia, além de preparar os dados para modelagem preditiva.

---

## 🔧 1. Entendimento do Problema e Hipóteses
O problema foi definido como uma **tarefa de regressão supervisionada**, visando compreender e prever a **autonomia** dos veículos elétricos a partir de variáveis técnicas como:

- **Velocidade Máxima**
- **Capacidade da Bateria**
- **Torque**
- **Eficiência Energética**

**Hipóteses iniciais:**
- Correlação **positiva** entre **capacidade da bateria** e **autonomia**.
- Correlação **negativa** entre **eficiência energética** e **autonomia**.

Essas hipóteses foram **tecnicamente embasadas** e **validadas** nas análises.

---

## 📊 2. Análise Exploratória de Dados (EDA)

### 2.1 Estrutura e Qualidade dos Dados
- **478 instâncias** e **22 atributos** (numéricos e categóricos).
- Valores faltantes identificados principalmente em:
  - `numero_celulas`
  - `torque_nm`
  - `capacidade_reboque_kg`
- **Tratamento aplicado**:
  - Imputação de **mediana** para variáveis numéricas.
  - Imputação de **moda** para variáveis categóricas.

### 2.2 Distribuições Individuais
- Autonomia com **assimetria à direita**, concentrada abaixo de **400 km**.
- **Média** ≈ **393 km**, condizente com padrões de mercado.
- Estatísticas descritivas revelaram grande diversidade — de modelos urbanos a veículos de alto desempenho.

### 2.3 Análises Combinadas
- **Matriz de correlação** e **pairplot** indicaram:
  - Correlação **positiva**: Capacidade da bateria ↔ Autonomia.
  - Correlação **negativa**: Eficiência energética ↔ Autonomia.
- Análise categórica:
  - Predomínio do segmento **JC - Medium** (porte médio).
  - Diversidade de modelos: compactos, esportivos e de luxo.

---

## ⚙️ 3. Pré-Processamento de Dados
Etapas realizadas para garantir dados prontos para modelagem:

- ✅ Imputação de valores faltantes.
- ✅ Normalização e padronização de variáveis numéricas.
- ✅ One-Hot Encoding para variáveis categóricas.
- ✅ Agrupamento de categorias pouco representadas.

**Resultado:** Dataset final com estrutura limpa, escalas compatíveis e formato numérico pronto para algoritmos de Machine Learning.

---

## 🤖 4. Preparação para Modelagem Preditiva
- Separação em **treino (80%)** e **teste (20%)** usando `train_test_split`.
- `random_state=42` para garantir reprodutibilidade.
- Distribuição da variável alvo (autonomia) **balanceada** entre treino e teste.

---

## ✅ 5. Considerações Finais
O projeto seguiu **boas práticas de ciência de dados**:

- ✔️ Definição clara do problema.
- ✔️ Análise exploratória robusta (gráficos + estatísticas).
- ✔️ Tratamento completo de inconsistências e valores ausentes.
- ✔️ Pré-processamento adequado.
- ✔️ Preparação cuidadosa para modelagem supervisionada.

---

## 🚀 Conclusão Técnica
- A **autonomia** dos veículos elétricos está **fortemente relacionada** à **capacidade da bateria**, ao **torque** e à **eficiência energética**.
- O dataset reflete a **diversidade do mercado**: de modelos compactos urbanos a veículos premium de alta performance.
- A base tratada é **ideal para desenvolvimento de modelos de regressão**, apoiando fabricantes e consumidores na escolha e otimização de veículos elétricos.

---
