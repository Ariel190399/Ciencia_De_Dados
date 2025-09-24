# 🚗 Projeto: Predição de Autonomia de Veículos Elétricos

Este projeto realizou uma análise exploratória aprofundada e um rigoroso pré-processamento do dataset **Electric Vehicles Specification 2025**, com o objetivo de investigar as relações entre as especificações técnicas dos veículos elétricos e sua autonomia, além de preparar os dados para modelagem preditiva.

---

## 🔧 1. Entendimento do Problema e Hipóteses

O problema foi definido como uma **tarefa de regressão supervisionada**, com foco em compreender e prever a autonomia dos veículos elétricos com base em variáveis técnicas como:

- Velocidade Máxima  
- Capacidade da Bateria  
- Torque  
- Eficiência Energética  

**Hipóteses iniciais:**
- Correlação **positiva** entre capacidade da bateria e autonomia.  
- Correlação **negativa** entre eficiência energética e autonomia.  

Essas hipóteses foram verificadas nas etapas seguintes.

---

## 📊 2. Análise Exploratória de Dados (EDA)

### 2.1 Estrutura e Qualidade dos Dados
- Dataset com **478 instâncias e 22 atributos**, incluindo variáveis numéricas e categóricas.  
- Valores faltantes em `numero_celulas`, `torque_nm` e `capacidade_reboque_kg` tratados com:  
  - **Mediana** (numéricas).  
  - **Moda** (categóricas).  

### 2.2 Distribuições Individuais
- A autonomia apresentou **assimetria à direita**, com média ≈ **393 km**.  
- Ampla diversidade de modelos: desde compactos urbanos até veículos de alta performance.  

### 2.3 Análises Combinadas
- **Correlação positiva** entre capacidade da bateria e autonomia.  
- **Correlação negativa** entre eficiência energética e autonomia.  
- Predominância do segmento **JC – Medium**, refletindo veículos de porte médio.  

---

## ⚙️ 3. Pré-Processamento de Dados

Etapas realizadas para garantir consistência e adequação:  

- ✅ Imputação de valores faltantes.  
- ✅ Normalização e padronização de variáveis numéricas.  
- ✅ One-Hot Encoding para variáveis categóricas.  
- ✅ Agrupamento de categorias pouco representadas.  

➡️ O dataset final resultou em um **formato robusto e adequado para algoritmos de Machine Learning**.

---

## 🤖 4. Modelagem e Treinamento

### 4.1 Preparação
- Divisão em treino (80%) e teste (20%), com `random_state=42`.  
- Distribuição equilibrada da variável alvo entre os dois conjuntos.  

### 4.2 Algoritmos Selecionados
- **Ridge Regression** → estabilidade e regularização L2.  
- **Lasso Regression** → seleção automática de variáveis.  
- **Random Forest** → robustez em dados tabulares.  
- **Gradient Boosting** → alto desempenho em relações complexas.  

### 4.3 Ajustes e Otimização
- Avaliação inicial indicou **R² elevado** em todos os modelos.  
- **GridSearchCV** aplicado em Ridge, Lasso e Gradient Boosting.  
- Destaque para o **Ridge** como modelo linear estável (R² Teste = 0.9794).  

### 4.4 Métodos Avançados
- **XGBoost** → melhor modelo individual (R² Teste = 0.9825).  
- **HistGradientBoosting** e **LightGBM** → competitivos e robustos.  
- **MLPRegressor** → desempenho inferior (R² Teste = 0.9485).  

### 4.5 Comitê de Modelos (Ensembles)
- **Voting Regressor** → R² Teste = 0.9840.  
- **Stacking Regressor** (com Ridge como meta-modelo) → **melhor resultado, R² Teste = 0.9845**.  

---

## 📈 5. Avaliação de Resultados

- **Métrica principal:** R², adequada para regressão (opcionalmente poderia ser complementada por MAE/RMSE).  
- Os resultados mostraram **consistência**, com pequenas diferenças entre treino e teste, descartando overfitting significativo.  
- Comparações entre modelos revelaram evolução clara:  
  - Modelos lineares estáveis (**Ridge/Lasso**).  
  - Árvores e ensembles robustos (**Random Forest, GB**).  
  - Boosting avançado (**XGBoost**).  
  - Ensembles (**Stacking**) com melhor desempenho geral.  

👉 **Melhor solução encontrada:** *Stacking Regressor* (**R² Teste = 0.9845**), combinando estabilidade, poder preditivo e robustez.  

---

## ✅ 6. Considerações Finais

O projeto seguiu boas práticas de ciência de dados:

- ✔️ Definição clara do problema.  
- ✔️ Análise exploratória robusta.  
- ✔️ Tratamento completo de inconsistências e valores ausentes.  
- ✔️ Pré-processamento adequado (normalização, codificação, limpeza).  
- ✔️ Avaliação de múltiplos algoritmos.  
- ✔️ Uso de ensembles para alcançar o melhor desempenho.  

---

## 🚗 Conclusão Técnica

- A autonomia está fortemente relacionada à **capacidade da bateria**, ao **torque** e à **eficiência energética**.  
- O mercado é diverso, mas com predominância de veículos médios.  
- O **Stacking Regressor (R² = 0.9845)** foi o modelo campeão, mostrando que a combinação de algoritmos supera soluções isoladas.  

---

## 🔍 Limitações e Desafios

- Dataset relativamente pequeno (**478 instâncias**).  
- Viés de representatividade (predominância de veículos médios).  
- Ausência de variáveis externas (peso, aerodinâmica, clima).  

---

## 🚀 Perspectivas Futuras

- Inclusão de variáveis adicionais (peso, consumo em diferentes cenários).  
- Aplicação de técnicas de **Explainable AI (SHAP, LIME)**.  
- Integração em sistemas de apoio à decisão, como **estimadores de autonomia em catálogos digitais**.  

---
