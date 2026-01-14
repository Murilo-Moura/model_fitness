# Análise de Rotatividade de Clientes — Model Fitness

## Descrição do Projeto
A rede de academias Model Fitness está a modernizar a sua estratégia de CRM para combater a rotatividade de clientes (churn), um desafio comum no setor fitness. Este projeto utiliza ciência de dados para antecipar a saída silenciosa de utilizadores — definida aqui como a ausência por um mês completo. O objetivo é desenvolver modelos preditivos de rotatividade, identificar perfis comportamentais através de clustering e sugerir ações estratégicas de retenção baseadas em evidências.

## Ferramentas e Bibliotecas Utilizadas
- **Python**: Linguagem base.
- **Pandas & NumPy**: Tratamento, limpeza e manipulação de dados.
- **Matplotlib, Seaborn & Plotly**: Visualização de dados e gráficos de distribuição/correlação.
- **Scikit-learn**: 
  - Pré-processamento (StandardScaler)
  - Modelos de Machine Learning (Regressão Logística e Random Forest)
  - Métricas (Acurácia, Precisão, Recall, F1, ROC AUC)
  - Algoritmos de Clusterização (K-Means)
- **SciPy**: Agrupamento hierárquico (Dendrogramas).

## Tabela (Dicionário de Dados)
O conjunto de dados contém informações sobre os perfis dos clientes e o seu histórico de utilização:

- `gender` — género (1 ou 0)
- `Near_Location` — proximidade da residência ou trabalho à academia
- `Partner` — se o utilizador é funcionário de uma empresa parceira
- `Promo_friends` — se se inscreveu através de promoção de amigos
- `Phone` — se forneceu número de telefone
- `age` — idade do cliente
- `Lifetime` — meses desde a primeira visita
- `Contract_period` — duração do contrato (1, 6 ou 12 meses)
- `Month_to_end_contract` — meses restantes até o fim do contrato
- `Group_visits` — participação em aulas de grupo
- `Avg_class_frequency_total` — frequência média semanal histórica
- `Avg_class_frequency_current_month` — frequência média semanal no mês atual
- `Avg_additional_charges_total` — gastos totais em serviços extras (café, massagem, etc.)
- **`Churn`** — rotatividade no mês em questão (1 - saiu; 0 - ficou)

## Metodologia
**Análise Exploratória de Dados (AED)**
- Verificação de valores ausentes e consistência dos tipos de dados.
- Padronização dos nomes das colunas para snake_case.
- Análise estatística comparativa entre os grupos de clientes (quem ficou vs. quem saiu).
- Criação de histogramas e matrizes de correlação para identificar variáveis críticas.

**Preparação e Treino de Modelos**
- Divisão dos dados em conjuntos de treino e teste.
- Normalização de características com StandardScaler.
- Treino e comparação de modelos de classificação: **Regressão Logística** e **Random Forest**.

**Agrupamento e Perfilamento (Clustering)**
- Construção de matriz de distância e dendrograma para definir o número de clusters.
- Aplicação do algoritmo **K-Means** (k=5) para segmentar os clientes em perfis distintos.
- Análise da taxa de churn por cluster.

## Resultados
O projeto permitiu identificar padrões claros de comportamento:
- Variáveis como `Contract_period`, `Age` e `Lifetime` mostraram-se os preditores mais fortes de fidelidade.
- Clientes com planos mensais (1 mês) apresentam um risco de churn significativamente superior aos que possuem planos anuais.
- Os modelos de Machine Learning apresentaram métricas sólidas (F1-score e AUC-ROC), permitindo à academia agir preventivamente sobre clientes em risco.
- Através da clusterização, identificámos perfis específicos, como os "fidelizados estáveis" e os "novatos de alto risco".

## Aprendizados
- **Machine Learning**: Aplicação prática de algoritmos de classificação e avaliação de desempenho de modelos preditivos.
- **Clustering**: Utilização de K-Means para segmentar clientes e gerar insights de negócio acionáveis.
- **Interpretação Estatística**: Compreensão de como variáveis demográficas e comportamentais influenciam a retenção de clientes.
- **Recomendações Estratégicas**: Tradução de dados técnicos em planos de ação (ex: incentivo à migração de planos mensais para semestrais e programas de onboarding para novatos).
