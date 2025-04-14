# 🔍 Busca Inteligente de Empresas Brasileiras (CNPJ)

Este projeto simula um sistema de **busca textual de empresas brasileiras**, capaz de identificar as empresas mais prováveis com base em **entradas digitadas pelo usuário** (ex: nome fantasia ou razão social), utilizando técnicas de NLP e similaridade textual.

---

## 🧠 Objetivo

Desenvolver um sistema que, a partir de um `user_input`, retorne as empresas mais semelhantes com base nos dados públicos da Receita Federal.  
A entrada simulada (`user_input`) foi gerada com distorções, erros e variações propositalmente, para testar a robustez do modelo.

---

## 🗃️ Dados

- Arquivo: `train.parquet`
- Origem: Receita Federal (fev/2025)
- O dataset contém campos como `razaosocial`, `nome_fantasia`, `uf`, `cnpj` e `user_input` (texto digitado simulado).

---

## 🧪 Modelos Utilizados

### 1. TF-IDF + Cosine Similarity
- Representação vetorial clássica dos textos
- Cálculo de similaridade entre `user_input` e os textos alvo (`razaosocial` + `nome_fantasia`)
- Filtro por **UF** para aumentar precisão

---

## 📊 Avaliação

A performance foi avaliada utilizando as métricas:

- `Precision 1`: Empresa correta na **1ª posição**
- `Precision 5`: Empresa correta entre as **5 primeiras posições**

Há dois tipos de avaliação no notebook: com o dataset completo (mais demorado) e com uma subamostra de 100 registros.

---

## 💻 Como usar

1. Instale as dependências:

```bash
pip install -r requirements.txt

jupyter notebook busca_empresas.ipynb

buscar_empresas("<nome da loja>, "<UF>", df)
