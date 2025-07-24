# 🚀 Projeto MotoGP - Engenharia de Dados

## 👩‍💻 Nome do Projeto  
**MVP do Sprint: Engenharia de Dados**  
**Responsável:** Ariel Chaves Escafura

---

## 📊 Estrutura do Projeto  
1️⃣ Carga e qualidade dos dados  
2️⃣ Modelagem em esquema estrela  
3️⃣ Análise exploratória  
4️⃣ Resposta às perguntas de negócio  

---

## 🏁 Relatório do Projeto MotoGP  

- 📥 Fiz upload do arquivo CSV do campeonato MotoGP (2008-2025) via Kaggle para o Databricks (DBFS).  
- 🗄️ Criei a tabela permanente "MotoGp" a partir da temporária, usando Python e SQL.  
- 🧹 Excluí a tabela temporária.  
- 🏷️ Configurei a primeira linha como cabeçalho e padronizei nomes das colunas.  
- 🔄 Reorganizei a ordem das colunas para facilitar o acesso.  
- 🔍 Realizei consulta para detectar duplicatas (confirmei que não há).  
- 🛠️ Padronizei os tipos de dados das colunas com CAST (ex: Pontos, Colocação e Corridas_participadas como INT), melhorando desempenho e evitando erros.  
- ⭐ Modelei o dado com esquema estrela, ideal para consultas rápidas e análises simples.

---

## ⭐ Esquema Estrela - Dimensões e Fato

| Dimensão       | Objetivo                                | Colunas Principais                                      |
|----------------|----------------------------------------|--------------------------------------------------------|
| **dim_piloto** | Dados únicos dos pilotos                | id_piloto, Nome_piloto, Numero_moto, Pais_origem, Titulos_mundiais |
| **dim_equipe** | Registra as equipes participantes       | id_equipe, nome_equipe                                 |
| **dim_moto**   | Modelos de motos usados nas corridas    | id_moto, modelo_moto                                   |
| **dim_tempo**  | Informação temporal e classe de corrida | id_tempo, ano, classe                                  |

| Tabela Fato              | Objetivo                                           | Colunas Principais                                                                    |
|-------------------------|---------------------------------------------------|--------------------------------------------------------------------------------------|
| **fato_temporada_piloto** | Resultados de pilotos por temporada, equipe, moto e classe | id_piloto, id_equipe, id_moto, id_tempo, Vitorias, Podios, Poles, Volta_mais_rapida, Pontos, Colocacao, Corridas_participadas, eficiencia_pontos, taxa_vitorias, taxa_podios |

---

## 📋 Catálogo de Dados

| Tabela                | Coluna               | Tipo    | Descrição                           | Domínio/Valores Esperados         |
|-----------------------|----------------------|---------|-----------------------------------|----------------------------------|
| fato_temporada_piloto | id_piloto            | INT     | Chave estrangeira para dim_piloto | 1 a 22                           |
| fato_temporada_piloto | id_equipe            | INT     | Chave estrangeira para dim_equipe | 1 a 85                           |
| fato_temporada_piloto | id_moto              | INT     | Chave estrangeira para dim_moto   | 1 a 33                           |
| fato_temporada_piloto | id_tempo             | INT     | Chave estrangeira para dim_tempo  | 1 a 42                           |
| fato_temporada_piloto | Vitorias             | INT     | Vitórias na temporada             | 0 a 13                           |
| fato_temporada_piloto | Podios               | INT     | Pódios conquistados               | 0 a 18                           |
| fato_temporada_piloto | Poles                | INT     | Pole positions                   | 0 a 13                           |
| fato_temporada_piloto | Volta_mais_rapida    | INT     | Voltas mais rápidas               | 0 a 12                           |
| fato_temporada_piloto | Pontos               | INT     | Pontos na temporada               | 0 a 508                          |
| fato_temporada_piloto | Colocacao            | INT     | Colocação no campeonato           | 1 a 47                           |
| fato_temporada_piloto | Corridas_participadas| INT     | Corridas disputadas               | 0 a 20                           |
| fato_temporada_piloto | eficiencia_pontos    | FLOAT   | Média de pontos por corrida       | 0.0 a 9.06                      |
| fato_temporada_piloto | taxa_vitorias        | FLOAT   | % de vitórias sobre corridas      | 0.0 a 100.0                    |
| fato_temporada_piloto | taxa_podios          | FLOAT   | % de pódios sobre corridas        | 0.0 a 100.0                    |
| dim_piloto            | id_piloto            | INT     | Identificador do piloto            | 1 a 22                           |
| dim_piloto            | Nome_piloto          | STRING  | Nome do piloto (ex: Marc Marquez) | Texto livre                    |
| dim_piloto            | Numero_moto          | INT     | Número da moto                    | 1 a 93                          |
| dim_piloto            | Pais_origem          | STRING  | País de origem (ex: Spain, Italy) | Texto livre                    |
| dim_piloto            | Titulos_mundiais     | INT     | Títulos ganhos                   | 0 a 8                           |
| dim_equipe            | id_equipe            | INT     | Identificador da equipe           | 1 a 85                          |
| dim_equipe            | nome_equipe          | STRING  | Nome completo da equipe           | Texto livre                    |
| dim_moto              | id_moto              | INT     | Identificador do modelo           | 1 a 33                          |
| dim_moto              | modelo_moto          | STRING  | Nome do modelo (ex: Honda RC213V) | Texto livre                    |
| dim_tempo             | id_tempo             | INT     | Identificador temporal            | 1 a 42                          |
| dim_tempo             | ano                  | INT     | Ano da temporada                 | 2008 a 2025                    |
| dim_tempo             | classe               | STRING  | Categoria da corrida              | MotoGP, Moto2, Moto3, 125cc, MotoE |

---

## 🔄 Linhagem dos Dados

- 📍 Origem: Site Kaggle (dados históricos do MotoGP).  
- 🔧 Transformações: Padronização de colunas, cálculo de métricas, modelagem em esquema estrela.  
- ⚙️ Plataforma de ETL: Databricks (Spark SQL).

---

Quer ajuda para colocar as consultas SQL também? 😄
