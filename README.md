
# 📊 Análise de Dados – Projeto Olist E-commerce

## 👥 Integrantes da Equipe

* **Caio Palácio**
* *(Adicione outros integrantes aqui, se houver)*

---

## 🔗 Base de Dados Utilizada

**Fonte oficial:**
Olist E-commerce Public Dataset
Link: [https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

---

## 🎯 Objetivo do Projeto

O objetivo deste projeto é **analisar padrões de comportamento no e-commerce brasileiro**, identificando fatores que influenciam:

* satisfação do cliente,
* valor do frete,
* dimensões do produto,
* possíveis causas de inconsistências nos dados.

A partir das análises, buscou-se melhorar o entendimento do funcionamento geral do marketplace e levantar percepções úteis para futuras aplicações (modelagem estatística ou machine learning).

---

## 🧹 Descrição do Processo de Tratamento dos Dados

### 1. **Carregamento e inspeção inicial**

Foram analisadas as colunas numéricas, categóricas e textuais, além de verificada a existência de valores nulos e duplicados.

### 2. **Remoção de duplicatas**

Entradas duplicadas foram identificadas com `df.duplicated().sum()` e posteriormente removidas.

### 3. **Tratamento de valores ausentes (missing values)**

Linhas contendo valores nulos foram removidas para garantir consistência durante a análise estatística e nos cálculos de correlação.

### 4. **Tratamento de outliers**

Foi utilizada uma função modificada baseada na mediana (método robusto), limitando valores extremos sem descartá-los completamente.
Exemplo aplicado às colunas numéricas como `price`, `freight_value`, dimensões e peso do produto.

### 5. **Normalização e padronização**

Após a limpeza, aplicou-se:

* **MinMaxScaler** → normalização 0–1
* **StandardScaler (Z-score)** → padronização baseada na média e desvio padrão

Os scalers foram aplicados tanto às colunas originais quanto às geradas por feature engineering.

### 6. **Feature Engineering**

Foram criadas novas variáveis para enriquecer a análise, como:

* volume do produto (`product_length_cm * product_height_cm * product_width_cm`)
* densidade estimada
* relações entre preço, peso e frete
  Essas variáveis foram normalizadas e analisadas junto às demais.

### 7. **Correlação**

Gerou-se um mapa de calor (heatmap) com **todas as colunas numéricas**, incluindo as derivadas, para avaliar possíveis relações entre atributos.

---

## 🧗 Principais Desafios Encontrados

1. **Grande quantidade de outliers**
   Valores extremamente altos nas colunas de preço, frete e dimensões exigiram técnicas robustas de suavização.

2. **Variabilidade alta entre atributos**
   A diferença de escalas (centímetros vs. reais vs. pesos) demandou normalização adequada para permitir análises comparáveis.

3. **Dados inconsistentes e incompletos**
   Registros faltantes e duplicados impactavam estatísticas e precisaram ser removidos com cuidado.

4. **Feature engineering sem causar viés**
   Criar novas variáveis que fossem realmente informativas, sem redundância ou distorções, exigiu diversas iterações.

---

## 💡 Principais Conclusões

* Os dados apresentavam **outliers significativos**, especialmente relacionados a preço, frete e dimensões. Após o tratamento, a distribuição tornou-se mais estável e adequada para análise estatística.
* As colunas relacionadas ao **tamanho e peso do produto** mostraram correlação moderada com o **valor do frete**, indicando impacto direto da logística sobre o custo.
* O processo de padronização permitiu identificar padrões que não eram visíveis antes da normalização.
* A engenharia de atributos (principalmente volume e densidade) trouxe informações complementares que ajudaram a explicar variações no preço e no frete.
* A limpeza dos dados alterou significativamente o comportamento das distribuições, reduzindo assimetria e aumentando a confiabilidade das conclusões.

---
