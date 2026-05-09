# 🗺️ Otimização de Rotas Comerciais — Do Caos à Estratégia

**Distribuidora Farmacêutica · Grande São Paulo · Python + Algoritmos de Otimização**

[![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python)](https://python.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)](https://jupyter.org)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

---

## 🎯 Contexto de Negócio

Uma distribuidora farmacêutica com atuação na Grande São Paulo possui **10 representantes comerciais** responsáveis por visitar **50 farmácias** distribuídas pela região.

O problema: rotas planejadas no *feeling*, sem critério geográfico — gerando deslocamentos desnecessários, cobertura irregular e alto custo operacional.

**Este projeto implementa e compara múltiplos algoritmos de otimização**, desde heurísticas clássicas até melhorias iterativas com clusterização geográfica, com análise completa de saving, ROI e planejamento semanal operacional.

---

## 📊 Resultados

| Algoritmo | Distância Total | Saving vs Baseline | Economia Anual |
|-----------|:--------------:|:-----------------:|:--------------:|
| Aleatório *(situação atual)* | 664 km | — | — |
| Nearest Neighbor | 539 km | 18,9% | R$ 9.386 |
| **2-Opt** | **518 km** | **22,0%** | **R$ 10.979** |
| Prioridade (NN) | 607 km | 8,6% | R$ 4.301 |
| **K-Means + 2-Opt** | **281 km** | **57,6%** | **R$ 28.689** |

> 🏆 **Melhor resultado:** K-Means + 2-Opt — redução de **57,6%** na distância com territórios geográficos coesos  
> ⚡ **Melhor heurística pura:** 2-Opt — 22% de saving com **break-even no Mês 6** e ROI de R$ 5.373 em 12 meses

![Dashboard Executivo](https://github.com/RoneyGalan/otimizacao-rotas/raw/main/images/06_dashboard_executivo.png)

---

## 🧠 Algoritmos Implementados

### 1. Rota Aleatória *(benchmark)*
Simula o planejamento manual sem critério geográfico. Serve como baseline para calcular o saving dos algoritmos otimizados.

### 2. Nearest Neighbor (NN)
Heurística gulosa clássica de TSP: a cada passo, visita o ponto não visitado mais próximo. Simples, rápido e já gera 18,9% de redução sobre o aleatório.

### 3. 2-Opt *(melhoria iterativa)*
Parte da rota do NN e melhora iterativamente trocando pares de arestas que se cruzam. Repete até não haver mais melhorias. Encontra soluções ~3% melhores que o NN com baixo custo computacional.

### 4. Prioridade de Visita
Garante que farmácias de **alta prioridade** sejam visitadas primeiro, independente da distância. Balanceia eficiência de rota com proteção de clientes estratégicos.

### 5. K-Means + 2-Opt *(territorialização)*
Agrupa farmácias geograficamente com K-Means antes de atribuir representantes, criando **territórios coesos** sem cruzamento de rotas entre profissionais. Aplica 2-Opt dentro de cada cluster. Resultado: 57,6% de saving — o maior ganho do projeto.

---

## 🗺️ Clusterização Geográfica

![Clusters](https://github.com/RoneyGalan/otimizacao-rotas/raw/main/images/01_clusters.png)

---

## 📈 Comparativo de Algoritmos

![Comparativo](https://github.com/RoneyGalan/otimizacao-rotas/raw/main/images/02_comparativo_algoritmos.png)

---

## 📅 Planejamento Semanal

![Planejamento Semanal](https://github.com/RoneyGalan/otimizacao-rotas/raw/main/images/03_planejamento_semanal.png)

---

## 🌍 Análise de Cobertura Geográfica

![Heatmap Cobertura](https://github.com/RoneyGalan/otimizacao-rotas/raw/main/images/04_heatmap_cobertura.png)

---

## 💰 Projeção de ROI — 12 Meses

![ROI Projeção](https://github.com/RoneyGalan/otimizacao-rotas/raw/main/images/05_roi_projecao.png)

---

## 📁 Estrutura do Notebook

```
otimizacao_rotas_completo.ipynb
│
├── Seção 0  — Imports e configurações
├── Seção 1  — Geração dos dados sintéticos
├── Seção 2  — Funções base (Haversine, dist_rota)
├── Seção 3  — Benchmark: Rota Aleatória
├── Seção 4  — Algoritmo 1: Nearest Neighbor
├── Seção 5  — Algoritmo 2: 2-Opt
├── Seção 6  — Algoritmo 3: Prioridade de visita
├── Seção 7  — Algoritmo 4: K-Means + 2-Opt
├── Seção 8  — Comparativo de algoritmos (gráficos)
├── Seção 9  — Planejamento semanal (1 visita/rep/dia)
├── Seção 10 — Heatmap de cobertura geográfica
├── Seção 11 — Projeção de ROI — 12 meses
├── Seção 12 — Mapa interativo Folium (Antes vs Depois)
└── Seção 13 — Dashboard executivo final
```

---

## 🗂️ Dados Sintéticos

| Parâmetro | Valor |
|-----------|-------|
| Farmácias | 50 pontos de venda na Grande SP |
| Representantes | 10 profissionais de campo |
| Regiões cobertas | Centro, Paulista, Faria Lima, Berrini, Tatuapé, Santo André, Guarulhos, Osasco, Santana, Mooca |
| Prioridade Alta / Média / Baixa | 25% / 45% / 30% |
| Custo por km | R$ 1,50 |
| Faturamento mensal total | ~R$ 17,7 Mi |
| Custo de implementação (ROI) | R$ 5.000 |

---

## 🛠️ Stack

```
Python 3.11
├── pandas          — manipulação de dados
├── numpy           — cálculos vetoriais
├── matplotlib      — visualizações estáticas
├── seaborn         — heatmaps e estilo
├── scikit-learn    — KMeans (clusterização)
├── folium          — mapas interativos
└── scipy / random  — suporte geral
```

---

## ▶️ Como Executar

```bash
git clone https://github.com/RoneyGalan/otimizacao-rotas.git
cd otimizacao-rotas
pip install pandas numpy matplotlib seaborn scikit-learn folium
jupyter notebook otimizacao_rotas_completo.ipynb
```

Execute as células em ordem. Os gráficos serão salvos em `images/` e os mapas Folium em `mapas/`.

---

## 🚀 Próximos Passos

- **OR-Tools (Google):** solver exato para resultados ainda melhores que o 2-Opt
- **Google Maps API:** distâncias reais considerando trânsito e janelas de horário
- **Streamlit:** dashboard web para atualização dinâmica das rotas pelo gestor
- **Dados reais:** integração com CRM e sistema de pedidos para scoring de prioridade dinâmico

---

## 👤 Autor

**Roney Galan**  
Data Analyst · MBA Big Data & Analytics — FGV  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-roney--wesley--galan-blue?logo=linkedin)](https://linkedin.com/in/roney-wesley-galan-ba7aa194) [![GitHub](https://img.shields.io/badge/GitHub-RoneyGalan-black?logo=github)](https://github.com/RoneyGalan)

---

> *"Sem critério geográfico, toda rota é uma aposta. Com algoritmos, é uma estratégia."*
