# Modelagem Preditiva para Diagnóstico de Câncer de Mama

Este repositório documenta o desenvolvimento de um modelo de Machine Learning para classificar tumores de mama como benignos ou malignos, utilizando o clássico dataset "Wisconsin Breast Cancer". O projeto foi conduzido com foco em rigor estatístico, interpretabilidade e validação robusta, aplicando os conceitos estudados no Mestrado em Estatística da UFRJ.

---

## 🎯 Objetivo

O objetivo central foi construir um modelo estatístico robusto e interpretável capaz de prever a malignidade de um tumor com alta acurácia, seguindo o ciclo de vida completo de um projeto de Data Science.

## 📊 Dataset

Foi utilizado o [Wisconsin Breast Cancer dataset](https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+(Original)), um conjunto de dados público e amplamente utilizado do repositório da UCI Machine Learning. Ele contém informações clínicas de amostras de tumores, com 10 atributos preditores e uma variável alvo (`Class`).

---

## 🛠️ Metodologia e Desenvolvimento

O projeto foi dividido em etapas claras, simulando um fluxo de trabalho profissional:

1.  **Análise Exploratória de Dados (EDA):**
    *   Investigação da distribuição de cada variável.
    *   Visualização da relação entre os preditores e a variável alvo (`Class`) usando `ggplot2`.
    *   Análise de correlação (Spearman) para identificar multicolinearidade entre os atributos. Foi detectada uma alta correlação (> 0.9) entre `Cell.size` e `Cell.shape`.

2.  **Engenharia de Atributos e Pré-processamento:**
    *   **Decisão Estratégica:** Para mitigar a instabilidade causada pela multicolinearidade, a variável `Cell.shape` foi removida, preservando a robustez do modelo.
    *   Imputação de valores faltantes (`NA`) na variável `Bare.nuclei` utilizando a moda da classe benigna, uma vez que a maioria dos casos faltantes pertencia a essa classe.
    *   Criação de novas variáveis categóricas a partir de preditores contínuos (ex: `Mitoses`), transformando relações não lineares em sinais mais claros para o modelo.

3.  **Modelagem Comparativa:**
    *   Divisão estratificada dos dados em conjuntos de treino (70%) e teste (30%).
    *   Ajuste de três Modelos Lineares Generalizados (GLM) com diferentes funções de ligação para avaliar qual delas melhor se adequava aos dados: **Logit**, **Probit** e **Cauchit**.
    *   Seleção do modelo Logit como o final, com base no menor valor de AIC (Akaike Information Criterion) no conjunto de treino, indicando o melhor equilíbrio entre ajuste e simplicidade.

4.  **Validação Rigorosa:**
    *   Avaliação da performance do modelo final no conjunto de teste (dados nunca vistos antes).
    *   Cálculo de métricas de negócio essenciais, como Acurácia, Sensibilidade (Recall) e Especificidade.
    *   Análise da Área Sob a Curva ROC (AUC) como principal indicador da capacidade de discriminação geral do modelo.

---

## 📈 Resultados Principais

O modelo Logit final alcançou uma performance excelente no ambiente de teste, validando sua capacidade de generalização:

- **AUC:** **0.9876** — O modelo tem uma capacidade excepcional de distinguir entre casos benignos e malignos.
- **Acurácia:** **92.3%** — O modelo acerta o diagnóstico em mais de 92% dos casos.
- **Sensibilidade (Recall):** **86.1%** — Consegue identificar corretamente 86% de todos os casos realmente malignos.
- **Especificidade:** **95.6%** — Consegue identificar corretamente quase 96% de todos os casos realmente benignos.

## 🚀 Como Visualizar o Relatório Completo

O relatório detalhado da análise, contendo todos os gráficos e o código R, foi gerado em formato HTML a partir do arquivo R Markdown (`analise_cancer_mama.Rmd`).

**Para visualizar o relatório interativo, [clique aqui para acessá-lo via GitHub Pages](https://aemilianus.github.io/Projeto_Cancer_Mama/analise_cancer_mama.html).**
*(Nota: Este link só funcionará após a configuração do GitHub Pages descrita na próxima seção).*

## 🛠️ Ferramentas Utilizadas

- **Linguagem:** R
- **Pacotes Principais:** `ggplot2` (visualização), `dplyr` (manipulação de dados), `caret` (modelagem), `pROC` (análise ROC).
- **Relatório:** R Markdown
